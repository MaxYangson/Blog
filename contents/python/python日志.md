

### 文章目录

- [1 日志相关概念](#1__1)
- - [1.1 日志的作用](#11__2)
  - [1.2 日志的等级](#12__8)
  - [1.3 logging 模块两种使用方式](#13_logging__18)
- [2 使用 logging 提供的模块级别的函数](#2__logging__22)
- - [2.1 logging 模块定义常用函数](#21_logging__23)
  - [2.2 使用方式1：简单配置](#22_1_36)
  - [2.3 使用方式2：使用 logging.basicConfig() 函数](#23_2_loggingbasicConfig__58)
- [3 使用 Logging 日志系统的四大组件](#3__Logging__131)
- - [3.1 Logger 类](#31_Logger__159)
  - [3.2 Handler 类](#32_Handler__193)
  - [3.3 Formater 类](#33_Formater__212)
  - [3.4 Filter类（了解即可）](#34_Filter_227)
  - [3.5 日志流处理简要流程](#35__238)

# 1 日志相关概念

## 1.1 日志的作用

- 程序调试
- 了解程序运行是否正常
- 故障分析与问题定位
- 用户行为分析

## 1.2 日志的等级

| 等级       | 含义                                                |
| -------- | ------------------------------------------------- |
| DEBUG    | 最详细的日志信息，典型应用场景是问题诊断                              |
| INFO     | 信息详细程度仅次于 DEBUG，通常只记录关键节点信息，用于确认一切都是按照我们预期的那样进行工作 |
| WARNING  | 当某些不期望的事情发生时记录的信息（如，磁盘可用空间较低），但是此时应用程序还是正常运行的     |
| ERROR    | 由于一个更严重的问题导致某些功能不能正常运行时记录的信                       |
| CRITICAL | 当发生严重错误，导致应用程序不能继续运行时记录的信息                        |

默认情况下，logging 模块将等级为 WARNING 及其以上的日志信息打印到控制台

## 1.3 logging 模块两种使用方式

logging 模块有两种使用方式

- 第一种方式是使用 logging 提供的模块级别的函数
- 第二种方式是使用 Logging 日志系统的四大组件

# 2 使用 logging 提供的模块级别的函数

## 2.1 logging 模块定义常用函数

| 函数                                   | 说明                       |
| ------------------------------------ | ------------------------ |
| logging.debug(msg,*args,**kwargs)    | 创建一条严重级别为 DEBUG 的日志记录    |
| logging.info(msg,*args,*kwargs)      | 创建一条严重级别为 INFO 的日志记录     |
| logging.warning(msg,*args,*kwargs)   | 创建一条严重级别为 WARNING 的日志记录  |
| logging.error(msg,*args,*kwargs)     | 创建一条严重级别为 ERROR 的日志记录    |
| logging.critical(msg,*args,**kwargs) | 创建一条严重级别为 CRITICAL 的日志记录 |
| logging.log(level,*args,*kwargs)     | 创建一条严重级别为 level 的日志记录    |
| logging.basicConfig(**kwargs)        | 对 root logger 进行一次性配置    |

下面进行使用演示：

## 2.2 使用方式1：简单配置，直接使用

```python
import logging

logging.debug("debug message")
logging.info("info message")
logging.warning("warning message")
logging.error("error message")
logging.critical("critical message")
logging.log(level=logging.ERROR, msg = "error in logging.log function")
```

输出结果：

```python
WARNING:root:warning message
ERROR:root:error message
CRITICAL:root:critical message
ERROR:root:error in logging.log function
```

默认情况下 logging 模块将日志打印到了标准输出中，且只显示大于等于 WARNING 级别的日志，这说明默认的日志级别设置为 WARNING（日志级别等级 CRITICAL > ERROR > WARNING > INFO > DEBUG）

## 2.3 使用方式2：使用 logging.basicConfig() 函数

使用 logging.basicConfig() 函数可以调整日志级别、输出格式等

logging.basicConfig() 函数说明

| 参数名      | 描述                                                                                                                                                                        |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| filename | 指定日志输出目标文件的文件名，指定该设置项后日志信息就不会被输出到控制台了                                                                                                                                     |
| format   | 指定日志格式字符串，即指定日志输出时所包含的字段信息以及它们的顺序。logging 模块定义的格式字段下面会列出。                                                                                                                 |
| datefmt  | 指定日期/时间格式。需要注意的是，该选项要在 format 中包含时间字段 %(asctime)s 时才有效                                                                                                                    |
| level    | 指定日志器的日志级别                                                                                                                                                                |
| stream   | 指定日志输出目标 stream，如 sys.stdout、sys.stderr 以及网络 stream。需要说明的是，stream 和 filename 不能同时提供，否则会引发 ValueError 异常                                                                   |
| style    | Python3.2 中新添加的配置项。指定 format 格式字符串的风格，可取值为 ‘%’、’{’ 和 ‘$’，默认为 ‘%’                                                                                                          |
| handlers | Python 3.3 中新添加的配置项。该选项如果被指定，它应该是一个创建了多个 Handler 的可迭代对象，这些 handler 将会被添加到 rootlogger。需要说明的是：filename、stream 和 handlers 这三个配置项只能有一个存在，不能同时出现 2 个或 3 个，否则会引发 ValueError 异常。 |

logging 模块的格式字符串

| 字段/属性名称         | 使用格式                | 描述                                                               |
| --------------- | ------------------- | ---------------------------------------------------------------- |
| asctime         | %(asctime)s         | 日志事件发生的时间–人类可读时间，如：2003-07-08 16:49:45,896                       |
| created         | %(created)f         | 日志事件发生的时间–时间戳，就是当时调用 time.time() 函数返回的值                          |
| relativeCreated | %(relativeCreated)d | 日志事件发生的时间相对于 logging 模块加载时间的相对毫秒数（目前还不知道干嘛用的）                    |
| msecs           | %(msecs)d           | 日志事件发生事件的毫秒部分                                                    |
| levelname       | %(levelname)s       | 该日志记录的文字形式的日志级别（‘DEBUG’, ‘INFO’, ‘WARNING’, ‘ERROR’, ‘CRITICAL’） |
| levelno         | %(levelno)s         | 该日志记录的数字形式的日志级别（10, 20, 30, 40, 50）                              |
| name            | %(name)s            | 所使用的日志器名称，默认是 ‘root’，因为默认使用的是 rootLogger                         |
| message         | %(message)s         | 日志记录的文本内容，通过 msg % args 计算得到的                                    |
| pathname        | %(pathname)s        | 调用日志记录函数的源码文件的全路径                                                |
| filename        | %(filename)s        | pathname 的文件名部分，包含文件后缀                                           |
| module          | %(module)s          | filename 的名称部分，不包含后缀                                             |
| lineno          | %(lineno)d          | 调用日志记录函数的源代码所在的行号                                                |
| funcName        | %(funcName)s        | 调用日志记录函数的函数名                                                     |
| process         | %(process)d         | 进程 ID                                                            |
| processName     | %(processName)s     | 进程名称，Python 3.1 新增                                               |
| thread          | %(thread)d          | 线程 ID                                                            |
| threadName      | %(thread)s          | 线程名称                                                             |

```python
# coding=utf-8
import logging

MY_FORMAT = "%(asctime)s %(name)s %(levelname)s %(pathname)s %(lineno)d %(message)s"  # 配置输出日志格式
DATE_FORMAT = '%Y-%m-%d  %H:%M:%S %a '  #配置输出时间的格式

logging.basicConfig(
    filename="my.log",  # 指定日志写入到文件
    level=logging.INFO,
    datefmt=DATE_FORMAT,
    format=MY_FORMAT,
)

logging.debug("debug")
logging.info("info")
logging.warning("warning")
logging.error("error")
logging.critical("critical")
```

打开文件 my.log，内容如下：

```
2020-11-22  19:18:58 Sun  root INFO E:/prapy/python_project/testcase/test1.py 15 info
2020-11-22  19:18:58 Sun  root WARNING E:/prapy/python_project/testcase/test1.py 16 warning
2020-11-22  19:18:58 Sun  root ERROR E:/prapy/python_project/testcase/test1.py 17 error
2020-11-22  19:18:58 Sun  root CRITICAL E:/prapy/python_project/testcase/test1.py 18 critical
```

说明：

- logging.basicConfig() 函数是一个一次性的简单配置工具，也就是说只有在第一次调用该函数时会起作用，后续再次调用该函数时完全不会产生任何操作的，多次调用的设置并不是累加操作。
- 日志器（Logger）是有层级关系的，上面调用的 logging 模块级别的函数所使用的日志器是 RootLogger 类的实例，其名称为 ‘root’，它是处于日志器层级关系最顶层的日志器，且该实例是以单例模式存在的。
- 如果要记录的日志中包含变量数据，可使用一个格式字符串作为这个事件的描述消息（logging.debug、logging.info 等函数的第一个参数），然后将变量数据作为第二个参数 *args 的值进行传递，

```python
>>> import logging
>>> logging.warning('%s is %d years old.', 'Tom', 10)
WARNING:root:Tom is 10 years old.
```

# 3 使用 Logging 日志系统的四大组件

上面我们了解到了 logging.debug()、logging.info()、logging.warning()、logging.error()、logging.critical()（分别用以记录不同级别的日志信息），logging.basicConfig()（用默认日志格式（Formatter）为日志系统建立一个默认的流处理器（StreamHandler），设置基础配置（如日志级别等）并加到 root logger（根 Logger）中）这几个 logging 模块级别的函数。

下面介绍第二种打印日志的方法，日志流处理，使用函数 logging.getLogger([name])（返回一个 logger 对象，如果没有指定名字将返回 root logger）。

在介绍 logging 模块的日志流处理流程之前，我们先来介绍下 logging 模块的四大组件：

| 组件名称 | 对应类名      | 功能描述                             |
| ---- | --------- | -------------------------------- |
| 日志器  | Logger    | 提供了应用程序可一直使用的接口                  |
| 处理器  | Handler   | 将 logger 创建的日志记录发送到合适的目的输出       |
| 过滤器  | Filter    | 提供了更细粒度的控制工具来决定输出哪条日志记录，丢弃哪条日志记录 |
| 格式器  | Formatter | 决定日志记录的最终输出格式                    |

**这些组件之间的关系描述：**

- 日志器（logger）需要通过处理器（handler）将日志信息输出到目标位置，如：文件、sys.stdout、网络等；
- 不同的处理器（handler）可以将日志输出到不同的位置；
- 日志器（logger）可以设置多个处理器（handler）将同一条日志记录输出到不同的位置；
- 每个处理器（handler）都可以设置自己的过滤器（filter）实现日志过滤，从而只保留感兴趣的日志；
- 每个处理器（handler）都可以设置自己的格式器（formatter）实现同一条日志以不同的格式输出到不同的地方。

简单点说就是：日志器（logger）是入口，真正干活儿的是处理器（[handler](https://so.csdn.net/so/search?q=handler&spm=1001.2101.3001.7020)），处理器（handler）还可以通过过滤器（filter）和格式器（formatter）对要输出的日志内容做过滤和格式化等处理操作。

**logging 日志模块相关类及其常用方法介绍**

与 logging 四大组件相关的类：Logger, Handler, Filter, Formatter。

## 3.1 Logger 类

Logger 对象有 3 个任务要做：

1. 向应用程序代码暴露几个方法，使应用程序可以在运行时记录日志消息；
2. 基于日志严重等级（默认的过滤设施）或 filter 对象来决定要对哪些日志进行后续处理；
3. 将日志消息传送给所有感兴趣的日志 handlers。

Logger 对象最常用的方法分为两类：配置方法和消息发送方法

**Logger 类相关方法**

| 方法                                           | 描述                           |
| -------------------------------------------- | ---------------------------- |
| Logger.setLevel()                            | 设置日志器将会处理的日志消息的最低严重级别        |
| Logger.addHandler() 和 Logger.removeHandler() | 为该logger对象添加 和 移除一个handler对象 |
| Logger.addFilter() 和 Logger.removeFilter()   | 为该logger对象添加 和 移除一个filter对象  |

logger对象配置完成后，可以使用下面的方法来创建日志记录：

| 方法                                                                                    | 描述                            |
| ------------------------------------------------------------------------------------- | ----------------------------- |
| Logger.debug(), Logger.info(), Logger.warning(),<br>Logger.error(), Logger.critical() | 创建一个与它们的方法名对应等级的日志记录          |
| Logger.exception()                                                                    | 创建一个类似于 Logger.error() 的日志消息  |
| Logger.log()                                                                          | 需要获取一个明确的日志 level 参数来创建一个日志记录 |

一个 Logger 对象呢？一种方式是通过 Logger 类的实例化方法创建一个 Logger 类的实例，但是我们通常都是用第二种方式–logging.getLogger() 方法。

logging.getLogger() 方法有一个可选参数 name，该参数表示将要返回的日志器的名称标识，如果不提供该参数，则其值为 ‘root’。若以相同的 name 参数值多次调用 getLogger() 方法，将会返回指向同一个 logger 对象的引用。

多次使用注意不能创建多个logger,否则会出现重复输出日志现象。

**关于logger的层级结构与有效等级的说明：**

- logger的名称是一个以 ‘.’ 分割的层级结构，每个 ‘.’ 后面的 logger 都是 ‘.’ 前面的 logger 的 children，例如，有一个名称为 foo 的 logger，其它名称分别为 foo.bar, foo.bar.baz 和 foo.bam 都是 foo 的后代。
- logger 有一个"有效等级（effective level）"的概念。如果一个 logger 上没有被明确设置一个 level，那么该 logger 就是使用它 parent 的 level；如果它的 parent 也没有明确设置 level 则继续向上查找 parent 的 parent 的有效 level，依次类推，直到找到个一个明确设置了 level 的祖先为止。需要说明的是，root logger 总是会有一个明确的 level 设置（默认为 WARNING）。当决定是否去处理一个已发生的事件时，logger 的有效等级将会被用来决定是否将该事件传递给该 logger 的 handlers 进行处理。
- child loggers 在完成对日志消息的处理后，默认会将日志消息传递给与它们的祖先 loggers 相关的 handlers。因此，我们不必为一个应用程序中所使用的所有 loggers 定义和配置 handlers，只需要为一个顶层的 logger 配置 handlers，然后按照需要创建 child loggers 就可足够了。我们也可以通过将一个 logger 的 propagate 属性设置为 False 来关闭这种传递机制。

## 3.2 Handler 类

Handler 对象的作用是（基于日志消息的 level）将消息分发到 handler 指定的位置（文件、网络、邮件等）。Logger 对象可以通过 addHandler() 方法为自己添加 0 个或者更多个 handler 对象。比如，一个应用程序可能想要实现以下几个日志需求：

| 方法                                                 | 描述                          |
| -------------------------------------------------- | --------------------------- |
| Handler.setLevel(lel)                              | 指定被处理的信息级别，低于 lel 级别的信息将被忽略 |
| Handler.setFormatter()                             | 给这个 handler 选择一个格式          |
| Handler.addFilter(filt)、Handler.removeFilter(filt) | 新增或删除一个 filter 对象           |

需要说明的是，应用程序代码不应该直接实例化和使用 Handler 实例。因为 Handler 是一个基类，它只定义了所有 handlers 都应该有的接口，同时提供了一些子类可以直接使用或覆盖的默认行为。下面是一些常用的 Handler：

| Handler                                   | 描述                                                                                                                  |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| logging.StreamHandler                     | 将日志消息发送到输出到 Stream，如 std.out, std.err 或任何 file-like 对象。                                                             |
| logging.FileHandler                       | 将日志消息发送到磁盘文件，默认情况下文件大小会无限增长                                                                                         |
| logging.handlers.RotatingFileHandler      | 将日志消息发送到磁盘文件，并支持日志文件按大小切割                                                                                           |
| logging.hanlders.TimedRotatingFileHandler | 将日志消息发送到磁盘文件，并支持日志文件按时间切割                                                                                           |
| logging.handlers.HTTPHandler              | 将日志消息以 GET 或 POST 的方式发送给一个 HTTP 服务器                                                                                 |
| logging.handlers.SMTPHandler              | 将日志消息发送给一个指定的 email 地址                                                                                              |
| logging.NullHandler                       | 该 Handler 实例会忽略 error messages，通常被想使用 logging 的 library 开发者使用来避免 ‘No handlers could be found for logger XXX’ 信息的出现。 |

## 3.3 Formater 类

Formater 对象用于配置日志信息的最终顺序、结构和内容。与 logging.Handler基类不同的是，应用代码可以直接实例化 Formatter 类。另外，如果你的应用程序需要一些特殊的处理行为，也可以实现一个 Formatter 的子类来完成。

Formatter 类的构造方法定义如下：

```python
logging.Formatter.__init__(fmt=None, datefmt=None, style='%')
```

可见，该构造方法接收 3 个可选参数：

- fmt：指定消息格式化字符串，如果不指定该参数则默认使用 message 的原始值
- datefmt：指定日期格式字符串，如果不指定该参数则默认使用 “%Y-%m-%d %H:%M:%S”
- style：Python 3.2 新增的参数，可取值为 ‘%’，’{’ 和 ‘$’，如果不指定该参数则默认使用 ‘%’

一般直接用 logging.Formatter(fmt, datefmt)

## 3.4 Filter类（了解即可）

Filter 可以被 Handler 和 Logger 用来做比 level 更细粒度的、更复杂的过滤功能。Filter 是一个过滤器基类，它只允许某个 logger 层级下的日志事件通过过滤。该类定义如下：

```python
class logging.Filter(name='')
    filter(record)
```

比如，一个 filter 实例化时传递的 name 参数值为 ‘A.B’，那么该 filter 实例将只允许名称为类似如下规则的 loggers 产生的日志记录通过滤：‘A.B’，‘A.B,C’，‘A.B.C.D’，‘A.B.D’，而名称为 ‘A.BB’，‘B.A.B’ 的 loggers 产生的日志则会被过滤掉。如果 name 的值为空字符串，则允许所有的日志事件通过过滤。

filter 方法用于具体控制传递的 record 记录是否能通过过滤，如果该方法返回值为0表示不能通过过滤，返回值为非 0 表示可以通过过滤。

## 3.5 日志流处理简要流程

1、创建一个 logger  
2、设置下 logger 的日志的等级  
3、创建合适的 Handler(FileHandler 要有路径)  
4、设置下每个 Handler 的日志等级  
5、创建下日志的格式  
6、向 Handler 中添加上面创建的格式  
7、将上面创建的 Handler 添加到 logger 中  
8、打印输出 logger.debug\logger.info\logger.warning\logger.error\logger.critical

```python
# coding=utf-8
import logging

# 创建logger，如果参数为空则返回 root logger
logger = logging.getLogger("mylogger")
logger.setLevel(logging.DEBUG)  # 设置logger日志等级

# 创建handler
fh = logging.FileHandler("test.log", encoding="utf-8")
ch = logging.StreamHandler()

# 设置输出日志格式, 注意 logging.Formatter的大小写
formatter = logging.Formatter(
    fmt="%(asctime)s %(name)s %(filename)s %(message)s",
    datefmt="%Y/%m/%d %X"
)

# 为handler指定输出格式，注意大小写
fh.setFormatter(formatter)
ch.setFormatter(formatter)

# 为logger添加的日志处理器
logger.addHandler(fh)
logger.addHandler(ch)

# 输出不同级别的log
logger.warning("warning message")
logger.info("info message")
logger.error("error message")
```

运行结果

```
2020/11/22 21:00:24 mylogger test3.py warning message
2020/11/22 21:00:24 mylogger test3.py info message
2020/11/22 21:00:24 mylogger test3.py error message
```

**python logging 重复写日志问题**

用 Python 的 logging 模块记录日志时，可能会遇到重复记录日志的问题，第一条记录写一次，第二条记录写两次，第三条记录写三次

**原因：没有移除 handler 解决：在日志记录完之后 removeHandler**

```python
# coding=utf-8
import logging

def log(msg):
    #创建logger，如果参数为空则返回root logger
    logger = logging.getLogger("mylogger")
    logger.setLevel(logging.DEBUG)  #设置logger日志等级

    #创建handler
    fh = logging.FileHandler("test.log",encoding="utf-8")
    ch = logging.StreamHandler()

    #设置输出日志格式
    formatter = logging.Formatter(
        fmt="%(asctime)s %(name)s %(filename)s %(message)s",
        datefmt="%Y/%m/%d %X"
        )

    #为handler指定输出格式
    fh.setFormatter(formatter)
    ch.setFormatter(formatter)

    #为logger添加的日志处理器
    logger.addHandler(fh)
    logger.addHandler(ch)

    # 输出不同级别的log
    logger.info(msg)

# 输出不同级别的log
log("message1")
log("message2")
log("message3")
```

运行结果

```
2020/11/22 21:08:04 mylogger test3.py message1
2020/11/22 21:08:04 mylogger test3.py message2
2020/11/22 21:08:04 mylogger test3.py message2
2020/11/22 21:08:04 mylogger test3.py message3
2020/11/22 21:08:04 mylogger test3.py message3
2020/11/22 21:08:04 mylogger test3.py message3
```

**分析**：可以看到输出结果有重复打印

原因：第二次调用 log 的时候，根据 getLogger(name) 里的 name 获取同一个logger，而这个 logger 里已经有了第一次你添加的 handler，第二次调用又添加了一个 handler，所以，这个 logger 里有了两个同样的 handler，以此类推，调用几次就会有几个 handler。

**解决方案 1：添加 removeHandler 语句**

```python
# coding=utf-8
import logging


def log(msg):
    # 创建logger，如果参数为空则返回root logger
    logger = logging.getLogger("mylogger")
    logger.setLevel(logging.DEBUG)  # 设置logger日志等级

    # 创建handler
    fh = logging.FileHandler("test.log", encoding="utf-8")
    ch = logging.StreamHandler()

    # 设置输出日志格式
    formatter = logging.Formatter(
        fmt="%(asctime)s %(name)s %(filename)s %(message)s",
        datefmt="%Y/%m/%d %X"
    )

    # 为handler指定输出格式
    fh.setFormatter(formatter)
    ch.setFormatter(formatter)

    # 为logger添加的日志处理器
    logger.addHandler(fh)
    logger.addHandler(ch)

    # 输出不同级别的log
    logger.info(msg)

    # 解决方案1，添加removeHandler语句，每次用完之后移除Handler
    logger.removeHandler(fh)
    logger.removeHandler(ch)


# 输出不同级别的log
log("message1")
log("message2")
log("message3")
```

**解决方案 2：在 log 方法里做判断，如果这个 logger 已有 handler，则不再添加 handler。**

```python
# coding=utf-8
import logging


def log(msg):
    # 创建logger，如果参数为空则返回root logger
    logger = logging.getLogger("mylogger")
    logger.setLevel(logging.DEBUG)  # 设置logger日志等级

    if not logger.handlers:
        # 创建handler
        fh = logging.FileHandler("test.log", encoding="utf-8")
        ch = logging.StreamHandler()

        # 设置输出日志格式
        formatter = logging.Formatter(
            fmt="%(asctime)s %(name)s %(filename)s %(message)s",
            datefmt="%Y/%m/%d %X"
        )

        # 为handler指定输出格式
        fh.setFormatter(formatter)
        ch.setFormatter(formatter)

        # 为logger添加的日志处理器
        logger.addHandler(fh)
        logger.addHandler(ch)

    # 输出不同级别的log
    logger.info(msg)


# 输出不同级别的log
log("message1")
log("message2")
log("message3")
```

**logger 调用方法的例子**

```python
# coding=utf-8
import logging.handlers
import datetime


def get_logger():
    logger = logging.getLogger('mylogger')  # mylogger为日志器的名称标识，如果不提供该参数，默认为'root'
    logger.setLevel(logging.DEBUG)  # 设置logger处理等级

    # 这里进行判断，如果logger.handlers列表为空，则添加，否则，直接去写日志
    if not logger.handlers:
        # rf_handler将所有的日志信息写到 all.log 中
        # when:字符串，定义了日志切分的间隔时间单位
        # interval:间隔时间单位的个数，指等待多少个when的时间后Logger会自动重建新闻继续进行日志记录
        # backupCount 是保留日志的文件个数，日志文件最多backupCount个，多余的删除，默认为0，表示不会自动删除
        rf_handler = logging.handlers.TimedRotatingFileHandler('all.log', when='midnight', interval=1, backupCount=7,
                                                               atTime=datetime.time(0, 0, 0, 0))

        # 设置输出日志格式
        rf_formatter = logging.Formatter("%(asctime)s - %(levelname)s - %(message)s")
        # 为handler指定输出格式
        rf_handler.setFormatter(rf_formatter)

        # f_handler 将等级大于等于 error的信息写到error.log文件中
        f_handler = logging.FileHandler('error.log')
        f_handler.setLevel(logging.ERROR)

        # 设置输出日志格式
        f_formatter = logging.Formatter("%(asctime)s - %(levelname)s - %(filename)s[:%(lineno)d] - %(message)s")
        # 为handler指定输出格式
        f_handler.setFormatter(f_formatter)

        # 为logger添加的日志处理器
        logger.addHandler(rf_handler)
        logger.addHandler(f_handler)

    return logger


logger = get_logger()
logger.debug('debug message')
logger.info('info message')
logger.warning('warning message')
logger.error('error message')
logger.critical('critical message')
logger.log(level=logging.ERROR, msg="logger.log message")
```

# 4 常见配置日志的三种方式

- 1）使用Python代码显式的创建loggers, handlers和formatters并分别调用它们的配置函数；
- 2）创建一个日志配置文件，然后使用`fileConfig()`函数来读取该文件的内容；
- 3）创建一个包含配置信息的dict，然后把它传递个`dictConfig()`函数；

# 5 如何移除原配置方案 —— 解决重复记录日志问题







# 参考文献：

[(76条消息) python 日志 logging 模块详解_-出发-的博客-CSDN博客](https://blog.csdn.net/happyjacob/article/details/109922504)

[Python之路(第十七篇)logging模块 - Nicholas-- - 博客园](https://www.cnblogs.com/Nicholas0707/p/9021672.html#_label1_1)

[(76条消息) python之logging配置日志的三种方式_蜗牛style的博客-CSDN博客_python logging](https://blog.csdn.net/SnailPace/article/details/125144289)
