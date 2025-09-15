---
title: "Makefile与CMake"
date: 2024-10-02
categories: C++
---

# CMake与Makefile详解

## 概述

CMake是一种跨平台编译工具，比make更为高级，使用起来要方便得多。CMake主要是编写CMakeLists.txt文件，然后用cmake命令将CMakeLists.txt文件转化为make所需要的makefile文件，最后用make命令编译源码生成可执行程序或共享库（so, shared object）。它的作用和Qt的qmake是相似的。

C/C++程序员肯定离不开Makefile和Cmake，因为如果对这两个工具不熟悉，那么你就不是一个合格的C/C++程序员。本文对Makefile和Cmake及它们的使用进行了详细的介绍。

# 一、Makefile详解

Makefile描述了整个工程的编译、连接等规则，makefile定义了一系列规则来指定：哪些文件需要编译以及如何编译、需要创建哪些库文件以及如何创建这些库文件、如何产生我们想要的可执行文件。使用Makefile，整个工程都可以完全自动化编译。而且Makefile可以有效的减少编译和连接的程序，只编译和连接那些修改的文件。

## 1.1 Makefile语法

Makefile包含了五个重要的东西：显示规则、隐晦规则、变量定义、文件指示和注释。

- **显示规则**：说明了如何生成一个或多个目标。由Makefile指出要生成的文件和文件依赖的文件。

- **隐晦规则**：基于Makefile的自动推导功能。

- **变量的定义**：一般是字符串。

- **文件指示**：
  - 在Makefile中引用另外一个makefile文件；
  - 根据某些规则指定Makefile中有效的部分；
  - 多行。

- **注释**：使用#表示注释。

Makefile有三个非常重要的变量：

- `$@`：目标文件
- `$^`：所有依赖文件
- `$<`：第一个依赖文件
- `.PHONY`：伪目标文件

Makefile的执行过程如下：

1. 在当前目录下寻找Makefile或makefile。
2. 找到第一个文件中的第一个目标文件，和目标文件依赖的.o文件。
3. 如果.o文件不存在，或是后面.o文件比target文件更新，那么它就会执行后面的语句来生成这个文件。
4. 最后makefile会根据.o文件依赖的.h和.c文件生成.o文件。

注意事项：
- clean不要放在target前面。
- `-rm edit $(objects)` 可忽略某些文件的问题。
- Makefile中的命令，必须以Tab键分割。文件之间最好使用空格分割。
- 使用`-I`或`--include-dir`参数，make会在这些目录下寻找头文件。
- `-L`指定库目录，相当于load lib dir，`-lfb303`相当于链接libfb303.so。

g++编译常用选项：
- `-g`：调试信息
- `-Wall`：显示所有警告
- `-O1~3`：优化级别
- `-lpthread`：多线程支持
- `-j8`：多线程编译
- `-D`：宏定义，例如-D_YUQIANG，那么#ifdef _YUQIANG为真。

## 1.2 Makefile示例

```makefile
CC = gcc
RM = rm

CFLAGS += -D _YUQIANG
TARGETS := myapp

all:$(TARGETS)

$(TARGETS):main.c
	$(CC) $(CFLAGS) $^ -o $@

clean:
	-$(RM) -f *.o
	-$(RM) -f $(TARGETS)
```

# 二、CMake详解

CMake是一个跨平台的安装（编译）工具，可以用简单的语句描述所有平台的安装（编译过程）。它能输出各种各样的makefile或者project文件，能测试编译器所支持的C++特性，类似UNIX下的automake。

## 2.1 CMake语法

常用CMake命令：

- `PROJECT(project_name)`：设置项目名称
- `INCLUDE_DIRECTORIES(include)`：设置头文件路径
- `SET(TEST_DIR ${DIR_SRCS})`：设置环境变量
- `SET(LIBRARIES libm.so)`：设置外部库
- `ADD_EXECUTABLE(../bin/bin ${TEST_DIR})`：设置可执行文件路径
- `TARGET_LINK_LIBRARIES(../bin/bin ${LIBRARIES})`：设置链接库
- `ADD_SUBDIRECTORY`：添加子目录

## 2.2 CMake示例

```cmake
# project name
PROJECT(test_math)

# head file path
INCLUDE_DIRECTORIES(
    include
)

# source directory
AUX_SOURCE_DIRECTORY(src DIR_SRCS)

# set environment variable
SET(TEST_MATH
    ${DIR_SRCS}
)

# set extern libraries
SET(LIBRARIES
    libm.so
)

# add executable file
ADD_EXECUTABLE(${PROJECT_NAME} ${TEST_MATH})

# add link library
TARGET_LINK_LIBRARIES(${PROJECT_NAME} m)
```

# 三、CMake编译原理

## 3.1 CMake编译步骤

CMake编译基本分为两个步骤：

1. cmake：指向CMakeLists.txt所在目录，例如：

```bash
mkdir build
cd build
cmake ..
```

这会生成编译所需的中间文件及makefile。

2. make：根据生成的makefile编译程序：

```bash
make
```

## 3.2 实际项目示例

我们编写一个关于开平方的C/C++程序项目，即b = sqrt(a)，以此理解整个CMake编译的过程。

项目结构：
```
.
├── build
├── CMakeLists.txt
├── include
│   └── b.h
└── src
    ├── b.c
    └── main.c
```

CMakeLists.txt内容：
```cmake
# cmake verson，指定cmake版本
cmake_minimum_required(VERSION 3.2)

# project name，指定项目的名称，一般和项目的文件夹名称对应
PROJECT(test_sqrt)

# head file path，头文件目录
INCLUDE_DIRECTORIES(
include
)

# source directory，源文件目录
AUX_SOURCE_DIRECTORY(src DIR_SRCS)

# set environment variable，设置环境变量，编译用到的源文件全部都要放到这里
SET(TEST_MATH
${DIR_SRCS}
)

# add executable file，添加要编译的可执行文件
ADD_EXECUTABLE(${PROJECT_NAME} ${TEST_MATH})

# add link library，添加可执行文件所需要的库
TARGET_LINK_LIBRARIES(${PROJECT_NAME} m)
```

编译和运行：
```bash
mkdir build
cd build
cmake ..
make
./test_sqrt
```

# 四、工具链关系说明

gcc是GNU Compiler Collection（GNU编译器套件），可以编译多种编程语言（C、C++、Objective-C、Fortran、Java等）

- 当程序只有一个源文件时，可以直接用gcc命令编译
- 当程序包含多个源文件时，使用make工具来管理编译过程
- make工具是一个智能的批处理工具，通过调用makefile中的命令进行编译和链接
- makefile类似于乐谱，make工具根据makefile中的命令调用编译器
- CMake可以更简单地生成makefile文件，并能跨平台生成对应平台的makefile
- CMake根据CMakeLists.txt文件生成makefile