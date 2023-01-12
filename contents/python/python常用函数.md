## 

# Python 标准库

官方文档：[Python 标准库 — Python 3.11.1 文档](https://docs.python.org/zh-cn/3/library/index.html)

## 创建目录——os.mkdir和os.makedirs

`os.mkdir` 方法用于以数字权限模式创建目录。不能递归创建

```
语法
mkdir()方法语法格式如下：  os.mkdir(path, mode)
参数
path -- 要创建的目录，可以是相对或者绝对路径。
mode -- 要为目录设置的权限数字模式，可以不填，默认的模式为 0777 (八进制)。
返回值
该方法没有返回值。
注意点：
1. os.mkdir不能递归的创建。即：如果目录有多级，则创建最后一级，如果最后一级目录的上级目录有不存在的，则会抛出一个 OSError
2. 如果目录创建失败或者已经存在，也会抛出一个 OSError 的异常，所以在使用之前需要判断目录是否存在
使用：
import os, sys
# 创建的目录
path = "/tmp/home/monthly/daily/hourly"  
# 前提/tmp/home/monthly/daily/该路径已存在
if not os.path.exists(path):  # 判断folder目录是否存在，如果不存在则创建目录。
    os.mkdir(path);

```

`os.makedirs`方法用于递归创建目录，即支持创建多层目录。  如果参数 path 只有一级，则 与`os.mkdir `函数相同

```
语法
makedirs()方法语法格式如下： os.makedirs(path, mode, exist_ok)
参数
path -- 要创建的目录，可以是相对或者绝对路径。
mode -- 要为目录设置的权限数字模式，可以不填，默认的模式为 0777 (八进制)。
exist_ok -- 是否已存在标志
返回值
该方法没有返回值。
注意点：
1. os.makedirs可以递归的创建。逐层创建直到最后一级
2. 如果目录已经存在兵器exist_ok为false，则会抛出一个 OSError的异常，否则不会抛异常。所以在使用之前需要判断目录是否存在
使用：
import os, sys
# 创建的目录
path = "/tmp/home/monthly/daily/hourly"  
if not os.path.exists(path):  # 判断folder目录是否存在，如果不存在则创建目录。
    os.makedirs(path);
```

## 判断当前环境操作系统——platform.system

[`platform`](https://docs.python.org/zh-cn/3/library/platform.html#module-platform "platform: Retrieves as much platform identifying data as possible.") --- 获取底层平台的标识数据的包

`platform.system()`在Windows系统下运行返回 `Windows`，Linux返回`Linux`

某 MacOS 返回 `Darwin`

```py
方法一
import platform

if ('Windows' == platform.system()):
    print('Windows')
elif ('Linux' == platform.system()):
    print('Linux')
else:
    print('Others')

方法二
from sys import platform
if ("linux" == platform) or ("linux2" == platform):
    print("Linux")
elif ("win32" == platform):
    print("Linux")
else:
	print("Others")
```

其他相关检测函数：

```py
import platform

print(platform.architecture())  # Python解释器信息，如('64bit', 'WindowsPE')
print(platform.dist())  # Linux发行版名称，如('Ubuntu', '18.04', 'bionic')
print(platform.linux_distribution())  # 同上
print(platform.java_ver())  # Jython接口版本
print(platform.libc_ver())  # libc版本，如('glibc', '2.25')
print(platform.mac_ver())  # MacOS版本
print(platform.machine())  # 处理器架构，如AMD64
print(platform.node())  # 网络名称
print(platform.platform())  # 详细操作系统信息，如Windows-7-6.1.7601-SP1
print(platform.popen('echo Hello').read())  # 执行系统命令
print(platform.processor())  # 处理器名称，如Intel64 Family 6 Model 94 Stepping 3, GenuineIntel
print(platform.python_branch())  # Python分支，如v3.6.4
print(platform.python_build())  # Python版本和编译时间，如('v3.6.4:d48eceb', 'Dec 19 2017 06:54:40')
print(platform.python_compiler())  # 编译器版本，如MSC v.1900 64 bit (AMD64)
print(platform.python_implementation())  # Python实现，有CPython、Jython、PyPy、IronPython
print(platform.python_revision())  # Python版次，如d48eceb
print(platform.python_version())  # Python版本，如3.6.4
print(platform.python_version_tuple())  # Python版本元组，如('3', '6', '4')
print(platform.release())  # 系统发行版，如Win7对应7
print(platform.system())  # 操作系统，如Windows、Linux
print(platform.system_alias(platform.system(), platform.release(), platform.version()))  # 系统别名，如('Windows', '7', '6.1.7601')
print(platform.uname())  # uname接口，返回(system, node, release, version, machine, processor)
print(platform.version())  # 系统的发布版本，如6.1.7601

```



## 系统分隔符——os.sep

作用：用于系统路径中的分隔符

Windows系统上，文件的路径[分隔符](https://so.csdn.net/so/search?q=%E5%88%86%E9%9A%94%E7%AC%A6&spm=1001.2101.3001.7020)是 **'\'**

Linux系统上，文件的路径分隔符是 **'/'**

苹果Mac OS系统中是 **':'**

**Python 为满足跨平台的要求，使用os.sep能够在不同系统上采用不同的分隔符**

```py
# 获取当前路径
current = os.getpwd()  # 假如为/local/yang
data_dir = os.sep.join(['hello', 'world'])  # hello/world或者hello\world
retpath = current + os.sep + data_dir  # /local/yang/hello/world

```
