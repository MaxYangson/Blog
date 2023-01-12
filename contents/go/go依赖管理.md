最近公司的一个项目需要从go vendor依赖管理升级到go mod 管理模式，期间也出现过不少问题，借此机会重温学习了go的依赖管理模式，记录升级过程中遇到的部分问题。

本文主要分为以下几个方面阐述：go的依赖管理、vendor升级mod模式、常见问题解决

## go依赖管理模式

对于一个大的项目来说，可能会引用很多的外部依赖包，依赖包可能会有不同的版本，如何对这些依赖管理显得至关重要，类似于java的maven、vue的npm、python的pip等，go也有自己的依赖管理模式。go的依赖管理经历了：GOPATH、go vendor&&dep、gomod等阶段。

目前的主流依赖管理自然是gomod管理，但是部分公司或者小的项目可能仍然采用GOPATH或者vendor模式，下面对这些模式做具体说明。

### GOPATH模式

#### 介绍

GOPATH是go依赖管理的早期模式，

> GOPATH
> 
> 1. 在 1.8 版本前必须设置这个环境变量
> 2. 1.8 版本后（含 1.8）如果没有设置使⽤用默认值
> 
> 在 Unix 上默认为 $HOME/go , 在 Windows 上默认为 %USERPROFILE%/go
> 在 Mac 上 GOPATH 可以通过修改 ～/.bash_profile 来设置

在 go mod 出现之前，所有的 Go 项目都需要放在同一个工作空间：`$GOPATH/src` 内，比如：

```
src/
    github.com/golang/example/
        .git/                      # Git repository metadata
    outyet/
        main.go                # command source
        main_test.go           # test source
    stringutil/
        reverse.go             # package source
        reverse_test.go        # test source
```

相比其他语言，这个限制有些无法理解。其实，这和 Go 的一设计理念紧密相关：

> 包管理应该是去中心化的

所以 Go 里面没有 maven/npm 之类的包管理工具，只有一个 go get，支持从公共的代码托管平台（Bitbucket/GitHub..）下载依赖，当然也支持自己托管，具体可参考官方文档：Remote import paths。

由于没有中央仓库，所以 Go 项目位置决定了其 import path，同时为了与 go get 保持一致，所以一般来说我们的项目名称都是 github.com/user/repo 的形式。
当然也可以不是这种形式，只是不方便别人引用而已，后面会讲到如何在 go mod 中实现这种效果

#### GOPATH使用步骤

### vendor和dep模式

使用 go get 下载依赖的方式简单暴力，伴随了 Go 七年之久，直到 1.6（2016/02/17）才正式支持了 vendor，可以把所有依赖下载到当前项目中，解决可重复构建（reproducible builds）的问题，但是无法管理依赖版本。社区出现了各式各样的包管理工具，来方便开发者固化依赖版本，由于不同管理工具采用不同的元信息格式（比如：godep 的 Godeps.json、Glide 的 glide.yaml），不利于社区发展，所以 Go 官方推出了 dep。

dep 的定位是实验、探索如何管理版本，并不会直接集成到 Go 工具链，Go 核心团队会吸取 dep 使用经验与社区反馈，开发下一代包管理工具 modules，并于 2019/09/03 发布的 1.13 正式支持，并随之发布 Module Mirror, Index, Checksum，用于解决软件分发、中间人攻击等问题。

### gomod模式

Go modules机制在go 1.11中是experiment feature，按照Go的惯例，在新的experiment feature首次加入时，都会有一个特性开关，go modules也不例外，GO111MODULE这个临时的环境变量就是go module特性的experiment开关。

GO111MODULE有三个值：auto、on和off，默认值为auto。

GO111MODULE的值会直接影响Go compiler的“依赖管理”模式的选择（是GOPATH mode还是module-aware mode），我们详细来看一下：

> + 当GO111MODULE的值为off时，go modules experiment feature关闭，go compiler显然会始终使用GOPATH mode，即无论要构建的源码目录是否在GOPATH路径下，go compiler都会在传统的GOPATH和vendor目录(仅支持在gopath目录下的package)下搜索目标程序依赖的go package；
> 
> + 当GO111MODULE的值为on时（export GO111MODULE=on），go modules experiment feature始终开启，与off相反，go compiler会始终使用module-aware mode，即无论要构建的源码目录是否在GOPATH路径下，go compiler都不会在传统的GOPATH和vendor目录下搜索目标程序依赖的go package，而是在go mod命令的缓存目录($GOPATH/pkg/mod）下搜索对应版本的依赖package；
> 
> + 当GO111MODULE的值为auto时(不显式设置即为auto)，也就是我们在上面的例子中所展现的那样：使用GOPATH mode还是module-aware mode，取决于要构建的源码目录所在位置以及是否包含go.mod文件。
>   
>   + 如果要构建的源码目录不在以GOPATH/src为根的目录体系下，且包含go.mod文件(两个条件缺一不可)，那么使用module-aware mode；
>   
>   + 否则使用传统的GOPATH mode。

#### Module 文件

执行命令 go build && go mod tidy ，下载依赖并整理。

项目根目录下会生成两个文件（需要加入到 git 中）：

> + 文件 go.mod：指示模块名称、go 的版本、该模块的依赖信息（依赖名称），类似 npm 生成的文件 package.json 。
> 
> + 文件 go.sum：该模块的所有依赖的校验和，类似 npm 生成的文件 package-lock.json 

Module 是多个 package 的集合，版本管理的基本单元，使用 go.mod 文件记录依赖的 module。

go.mod 位于项目的根目录，支持 4 条命令：module、require、replace、exclude。示例：

```
module github.com/my/repo

require (
    github.com/some/dependency v1.2.3
    github.com/another/dependency/v4 v4.0.0
)
```

> module 声明 module path，一个 module 内所有 package 的 import path 都以它为前缀
> require 声明所依赖的 module，版本信息使用形如 v(major).(minor).(patch) 的语义化版本 
> replace/exclude 用于替换、排查指定 module path

#### go mod命令

> golang 提供了 `go mod`命令来管理包。

go mod 有以下命令：

| 命令       | 说明                                                      |
| -------- | ------------------------------------------------------- |
| download | download modules to local cache(下载依赖包)                  |
| edit     | edit go.mod from tools or scripts（编辑go.mod）             |
| graph    | print module requirement graph (打印模块依赖图)                |
| init     | initialize new module in current directory（在当前目录初始化mod） |
| tidy     | add missing and remove unused modules(拉取缺少的模块，移除不用的模块)  |
| vendor   | make vendored copy of dependencies(将依赖复制到vendor下)       |
| verify   | verify dependencies have expected content (验证依赖是否正确）    |
| why      | explain why packages or modules are needed(解释为什么需要依赖)   |

#### Go modules使用步骤

> 1. 首先将你的版本更新到最新的Go版本(>=1.11)。
> 
> 2. 通过go命令行，进入到你当前的工程目录下，在命令行设置环境变量
> 
> ```
> #方式1：临时设置
> 注意
> # Windows环境用set
> # linux环境用export
> #########Windows#########
> # 开启
> set GO111MODULE=on
> # 1.13 之后才支持多个地址，之前版本只支持一个
> set GOPROXY=https://goproxy.cn,https://mirrors.aliyun.com/goproxy,direct
> # 1.13 开始支持，配置私有 module，不去校验 checksum
> set GOPRIVATE=*.corp.example.com,rsc.io/private
> #########Linux#########
> # 开启
> export GO111MODULE=on
> # 1.13 之后才支持多个地址，之前版本只支持一个
> export GOPROXY=https://goproxy.cn,https://mirrors.aliyun.com/goproxy,direct
> # 1.13 开始支持，配置私有 module，不去校验 checksum
> export GOPRIVATE=*.corp.example.com,rsc.io/private
> 
> #方式2：全局设置
> # 设置全局开启 go mod Go1.16版本默认为on，可跳过这一步
> go env -w GO111MODULE=on
> # 设置全局代理地址
> go env -w GOPROXY=https://goproxy.cn,https://mirrors.aliyun.com/goproxy,direct
> ```
> 
> 3. 执行命令go mod init在当前目录下生成一个go.mod文件，执行这条命令时，当前目录不能存在go.mod文件。如果之前生成过，要先删除；
> 
> 4. 如果你工程中存在一些不能确定版本的包，那么生成的go.mod文件可能就不完整，因此继续执行下面的命令；
> 
> 5. 执行go mod tidy命令，它会添加缺失的模块以及移除不需要的模块。执行后会生成go.sum文件(模块下载条目)。添加参数-v，例如go mod tidy -v可以将执行的信息，即删除和添加的包打印到命令行；
> 
> 6. 执行命令go mod verify来检查当前模块的依赖是否全部下载下来，是否下载下来被修改过。如果所有的模块都没有被修改过，那么执行这条命令之后，会打印all modules verified。
> 
> 7. 执行命令go mod vendor生成vendor文件夹，该文件夹下将会放置你go.mod文件描述的依赖包，文件夹下同时还有一个文件modules.txt，它是你整个工程的所有模块。在执行这条命令之前，如果你工程之前有vendor目录，应该先进行删除。同理go mod vendor -v会将添加到vendor中的模块打印出来；

#### go module文件下载位置

> 存储下载的依赖包,具体位置在$GOPATH/pkg/mod

在 Go 1.8 版本之前，GOPATH 环境变量默认是空的。从 Go 1.8 版本开始，Go 开发包在安装完成后，将 GOPATH 赋予了一个默认的目录，参见下表。

GOPATH 在不同平台上的安装路径

| 平 台        | GOPATH 默认值       | 举 例             |
| ---------- | ---------------- | --------------- |
| Windows 平台 | %USERPROFILE%/go | C:\Users\用户名\go |
| Unix 平台    | $HOME/go         | /home/用户名/go    |



代理地址

> https://goproxy.cn  //七牛云赞助支持的开源代理
> 
> [https://goproxy.io](https://goproxy.io) //也是一个开源的go代理
> 
> https://mirrors.aliyun.com/goproxy  //阿里云官方维护的go代理



## vendor升级mod模式



## 常见问题解决