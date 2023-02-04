## 关于go mod安装第三方包提示： module declares its path as: github.com/apache/thrift but was required as: git.apache.org/thrift.git 解决办法

问题描述：

![](https://img2022.cnblogs.com/blog/1043600/202203/1043600-20220316112617346-92177789.png)

原因分析：

apache/thrift软件包已经转移到git.apache.com中，不在使用原来的git.apache.org路径

解决方案：

在go mod 文件中添加以下替换语句：

```
replace git.apache.org/thrift.git v0.16.0 => github.com/apache/thrift v0.16.0
```

然后更新依赖：

```
go mod tidy
```

参考资料：

[关于go mod安装第三方包提示： module declares its path as: github.com/apache/thrift but was required as: git.apache.org/thrift.git 解决办法 - 码农骆驼 - 博客园 (cnblogs.com)](https://www.cnblogs.com/rxbook/p/16012074.html)

## Windows环境golang程序开发 报错exec: gcc: executable file not found in %PATH%

问题描述：

```
cgo: C compiler "gcc" not found: exec: "gcc": executable file not found in %PATH%
```

原因分析：

缺少gcc编译器

引入新的包，**需要c语言编译环境，而系统缺少相关安装环境**，所以执行失败。

解决方案：

下载MinGW-w64安装包并配置系统环境变量

参考资料：

[Windows环境golang程序开发 报错exec: gcc: executable file not found in %PATH%_灬倪先森_的博客-CSDN博客_golang 缺少gcc](https://blog.csdn.net/Lyon_Nee/article/details/106840502)

-----

<p style="text-align:right">Lastest Updated: {docsify-updated}</p>