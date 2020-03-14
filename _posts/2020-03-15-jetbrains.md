---
layout: post
title: "JetBrains IDE 通过 SSH 远程调试代码"
tagline: "通过 CLion 和 PyCharm 来介绍如何通过 SSH 远程调试代码 ..."
#categories: 
#author: ""
#meta: ""
---
熟悉 **VS Code** 的都知道，**Remote-SSH** 插件调试远程服务器上的代码非常方便。本文主要是探索如何在 **JetBrains** 全家桶上实现相应的功能。

## **简介**

<hr style="height:5px;" />

自从给 [**JetBrains**](http://www.jetbrains.com) 全家桶 (**学生免费**🎉 🎉 🎉
) 安装了 [**Material Theme UI**](https://plugins.jetbrains.com/plugin/8006-material-theme-ui) 插件后，他们家 **IDE** 的颜值深得我心，再加上 **Sublime Text** 令人不满意的代码高亮和补全，**VS Code** 虽然讲不出哪里不好但是总用不习惯 (感觉它就是一个伪装成编辑器的 IDE)。

综合比较了下，我计划以后写项目代码还是用 **JetBrains** 家的 IDE。当然，一些小的脚本还是用 Sublime Text 比较方便！

因为我们一般都在服务器上跑项目代码，而且我用 **Mac** 写 **CUDA** 也没法本机调试，**VS Code** 可以用 **Remote-SSH** 插件连接远程服务器来 debug，那备受追捧的 **JetBrains** 家的 IDE 当然也有类似的功能。不过二者实现的原理不同：

* **VS Code** 就是把插件上传到服务器上，然后远程修改调试代码，**VS Code** 就仅仅充当一个 **UI**；

* **JetBrains** 则是将代码 **deploy** 在本地和远程服务器上，实时同步项目文件夹，既可以调用本地编译器也可以调用远程服务器上的编译器，以此来实现和 **Remote-SSH** 类似的功能 (好处就是如果断开服务器连接，仍然可以在本地查看或者调试代码)。

就如何配置实现该功能，我以常用的 [**CLion**](http://www.jetbrains.com/clion) 和 [**PyCharm**](http://www.jetbrains.com/pycharm/) 举例：

### **CLion**

<hr style="height:2px;" />

[**CLion**](http://www.jetbrains.com/clion) 是 **JetBrains** 全家桶中的 **C/C++ IDE**，它其实是通过 [**CMake**](http://www.cmake.org) 来编译执行 C/C++ 代码的，如果不了解 **CMake** 如何使用，可以自行百度一下，我在这给出一个简单的 **CMakeLists.txt** 的模板：

[/CMakeLists.txt](https://raw.githubusercontent.com/NoNo721/Configuration/master/CMakeLists.txt) (点击打开源代码):

``` cmake
#
#	Created by WW on 2019-6-27, revised by WW on 2020-02-06.
#	Copyright © WW. All rights reserved.
#
#	This is a general template illustrates how to use Cmake.
#

cmake_minimum_required(VERSION 2.8)  # required cmake version at least

project(Beta) # project name

# Bring the header-files in directory "include" into the project, 
# which equals to "-I<inc>" flag of gcc,
# so you don't need to include these header-files in the "add_executable/library" Command.
# include_directories(include)

# Link current CMakeLists.txt directory, 
# then you can target_link_libraries() in these directories.
# You can also link other directories, which equals to "-L<path>" flag of gcc.
# link_directories(${CMAKE_CURRENT_SOURCE_DIR})

# Add directory "src" into the project, CMake will also execute the CMakeLists.txt file in "src",
# so you can use the files and libraries in "src".
# add_subdirectory(src)

# Cmake C/C++ compiler will use C++ 11, which equals to "set(CMAKE_CXX_STANDARD 11)".	
add_compile_options(-std=c++11)

# Add some new flags into original CXXFLAGS.
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g")

# Compile and creat the executable file.
# add_executable(beta main.cpp)

# Define some variables representing the files.
# GLOB and GLOB_RECURSE can recognize the Regular Expression "*".
file(GLOB LIB_HEADERS *.h)
file(GLOB LIB_SOURCES *.cpp *.c)

# Compile and creat new library (SHARED or STATIC).
add_library(MYLIB STATIC ${LIB_HEADERS} ${LIB_SOURCES})

set(EXTRA_LIBS ${EXTRA_LIBS} MYLIB)  # add libraries into the EXTRA_LIBS

# Define some variables representing the files.
# GLOB and GLOB_RECURSE can recognize the Regular Expression "*".
file(GLOB HEADERS *.cuh)
file(GLOB SOURCES *.cu)

find_package(CUDA) # find cuda packages

# Add some new flags into original NVCC_FLAGS.
set(CUDA_NVCC_FLAGS "${CUDA_NVCC_FLAGS} -g -O3 -std=c++11 -cudart static -gencode arch=compute_60,code=sm_60")

# Use CUDA C/C++ compiler nvcc to creat the executable file.
cuda_add_executable(magnon.exe ${SOURCES} ${HEADERS})

# Link the executable file with all libraries
target_link_libraries(magnon.exe ${EXTRA_LIBS})

# If you already have some libraries, you could link them after link_directories(),
# which equals to -l<libname>
# target_link_libraries(magnon.exe libnrutil.a)

```

**注意**：如果代码显示找不到头文件，可以在 **CMakeLists.txt** 中添加 `include_directories("/PATHTO/INC")` 自行添加头文件目录。

1. 首先打开 `preferences -> Build, Execution, Deployment -> Toolchains` 来找到远程服务器上的各种编译工具。点击右边界面左上角的 `+` 号添加一个除了 Default 之外的 Toolchain，选择 `Remote Host`, 可以自定义修改 `Name`，然后修改 SSH 的 `Credentials`，在弹出窗口中填入 `Host` 、`Port` (默认 22)、 `User name` 和密码。如果你的 SSH 配置比较复杂，比如有[**跳板机**]({{ site.url }}/2019/10/15/ssh.html)或者有[**秘钥文件**]({{ site.url }}/2019/09/17/server.html#ssh_key) 之类的，可以将 `Authentication type` 由 `Password` 改为 `OpenSSH config and authentication agent`，**CLion** 会自行调用本地 `~/.ssh/` 中的设置来连接服务器。

2. 打开 `preferences -> Build, Execution, Deployment -> CMake`，Profiles 中有一个默认的 Debug，点击右边界面左下角的 `+` 号添加，自行修改 `Name`, 一般改为 "Debug-remote"。将 `Build type` 改为 `Debug`，将 `Toolchain` 改为刚才添加的 Toolchain。

至此我们就配置好了编译系统，下面设置如何在本地和服务器两端同步代码：

* 在 `preferences -> Build, Execution, Deployment -> Deployment` 中添加一个 `SFTP` (如果已经设置好了远程 Toolchain，这里就会自动有一个 `SFTP` 类型的连接，就不用另外添加了)。在 `Mappings` 中选择远程服务器上的项目文件夹 `Deployment path` (如果不设置就会把代码同步到服务器根目录下的 `/tmp` 文件夹中)。如果有文件或者文件夹不想同步，在 `Excluded Paths` 中添加就好了。

`APPLY` 以上设置，等文件同步传输和 **CLion** index 完成后，在 `Run` 中选择我们第二步添加的 `CMake` "Debug-remote" 就可以在服务器端编译执行 C/C++ 代码了，同样也可以打断点 debug 了。

**注意**：有时候 **CLion** 高亮也有问题，关闭项目重启就好了。有时候断点可能会失效，选择 `Tools -> CMake -> Reset Cache and Reload Project`，再 debug 就能恢复正常了。服务器端调试时可能某些头文件无法导入，就算在 **CMakeLists.txt** 中添加 `include_directories("/PATHTO/INC")` 也没有作用，必须在 C/C++ 代码中用完整的绝对路径 `#include` 才可以。

### **PyCharm**

<hr style="height:2px;" />

[**PyCharm**](http://www.jetbrains.com/pycharm/) 是 **JetBrains** 全家桶中的 **Python IDE**，它的设置更加简单，不需要 **CLion** 中的 1、2 步设置，直接第 3 步设置 `Deployment`。然后在 `preferences -> Project: XXX -> Project Interpreter` 中将**项目的 Python 解释器**改为**服务器端的 Python 解释器**，第一次修改需要 `Add -> SSH Interpreter -> Existing server configuration` 中选择刚刚配置好的 `Deployment configuration`。

`APPLY` 后等文件同步传输和 **PyCharm** index 完成 (如果 Python packages 很多可能会比较慢)，再在 `Run` 中选择要执行的 Python 文件就可以在服务器端执行 Python 代码了，同样也可以打断点 debug 了。

**注意**：要是代码本来就在服务器端，在配置好 `Deployment` 后，选择 `Tools -> Deployment -> Browse Remote Host` 就可以打开远程服务器端目录，找到代码所在文件夹，右键选择下载就好了。**Pycharm** debug 时在 **Variables** 栏中显示的 [***NumPy***](https://numpy.org)  和 [***Pandas***](https://pandas.pydata.org) 变量，后面会有 **View as Array** 或者 **View as DataFrame** 等，点击就会弹出 **SciView** 的 **Data 窗口**详细显示变量中的所有数据。

## **总结**

<hr style="height:5px;" />

除此之外，**JetBrains** 的代码 **Inspections** 功能非常强大 (不过我建议在 `preferences -> Editor -> Inspections` 中把 `Spelling -> Typo` 给关掉)，根据 IDE 中的提示可以让你的代码更标准！

厌倦了单纯的编辑器，主要还是对它们的代码高亮和补全功能不满意。无聊时研究研究 **JetBrains IDE** 全家桶，以后发现什么有意思的其他功能再做记录！ 🎉 🎉 🎉

&ensp;

[<b><u>Go to the Home Page</u></b>]({{ site.url }}{{ site.baseurl }})

&ensp;

<center class="half">
<font color="#26975b"><b>Sponsor the author </b></font><font color="#08a2e4"><b>if you like the contents!</b></font><br/><br/>
</center>

<center class="half">
    <img src="https://nono721-1300921342.cos.ap-shanghai.myqcloud.com/WechatPay.png" width="251" style="margin-right:10px;margin-left:10px"/><img src="https://nono721-1300921342.cos.ap-shanghai.myqcloud.com/AliPay.png" width="250" style="margin-right:10px;margin-left:10px"/>
</center>

&ensp;













