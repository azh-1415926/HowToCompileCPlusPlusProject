# C++ 项目指南

**从零开始编译 C++ 项目**

编译一个项目，首先要熟悉工具，其次对整个编译流程有所了解。

在遇到问题时，排查问题需要了解一些知识。比如在编译过程中，少量的语法错误，可以通过修改代码完成，大量的语法错误，就得排查问题了，比如说编译器版本、依赖库版本、项目的环境不符（有些项目只能在Linux上跑），严格遵循项目的编译文档，可以避免很多麻烦。

所以想要跑通大多数项目，需要准备 Linux 和 Windows 系统都搭建好基本的环境。

**工具介绍**

在正式开始实战前，需要了解一些常用工具的用途。
1. 编译器
    * Windows：MinGW（Minimalist GNU for Windows）、MSVC（Microsoft Visual C++）
        * MinGW 提供了一个类Unix的编程环境

        * MSVC 是 Microsoft 公司推出的开发 Win32 环境程序
    * Linux：GCC（GNU Compiler Collection）

2. 构建工具
    * make（在 GCC、MinGW 有该工具，依赖 Makefile）
    * cmake（跨平台构建工具，依赖 CMakeLists 生成 Makefile、build.ninja、*.vcxproj 等项目文件）
    * ninja（依赖 build.ninja）
    * meson（依赖 meson.build）
    * qmake（Qt 公司开发的构建工具）

3. IDE
    * VSCode（Visual Studio Code）
        * 轻量化的 IDE,不带编译器，但是可以通过安装插件，手动安装编译器及其构建工具，即可构建项目
    * VS（Visual Studio）
        * Windows 下微软开发的 IDE，可安装 MSVC 编译器

4. 其他工具
    * git
        * 用于拉取代码以及代码的版本管理

编译一个项目，编译器必不可少。

由于某项目的开发基于某个编译器开发，而我们编译的时候没有按照作者要求的环境，可能导致项目无法编译通过，这时可以换个编译器，或者换个编译器版本试试，一般编译文档里会提到。

**工具详情**

给大家推荐了一些更详细的文章，用于扩展阅读。
1. [捋一捋gcc/g++/MingW/MSVC与make/CMake的关系](https://zhuanlan.zhihu.com/p/448884264)
2. [MingW-W64-builds不同版本之间的区别](https://blog.csdn.net/zhangjiuding/article/details/129556458)
3. [为什么要用make？为什么要用cmake？Linux源码编译的一般流程？](https://blog.csdn.net/qq_27825451/article/details/103392719)
4. [CMake是什么？有什么用？](https://blog.csdn.net/Torres_10/article/details/80371425)
5. [Visual Studio和Visual Studio Code(VSCode)的区别及如何选择-前端开发自学笔记(7)](https://zhuanlan.zhihu.com/p/565412998)

**搭建开发环境**

下载软件

1. Windows
    * [MinGW Release](https://github.com/niXman/mingw-builds-binaries/releases)
        * 可以下载这个版本的[x86_64-13.2.0-release-posix-seh-ucrt-rt_v11-rev1.7z](https://github.com/niXman/mingw-builds-binaries/releases/download/13.2.0-rt_v11-rev1/x86_64-13.2.0-release-posix-seh-ucrt-rt_v11-rev1.7z)
        * 解压后，需要把 MinGW 的 bin 目录的路径添加到 PATH 里，这样才能让 cmake 找到 gcc g++ make
    * [VSCode官网](https://code.visualstudio.com/)
        * [VSCode 下载页面](https://code.visualstudio.com/Download)
        * [VSCode Windows 下载](https://code.visualstudio.com/docs/?dv=win64user)
        * 安装完 VSCode，需要安装一些插件，比如 `C/C++`、`C/C++ Extension Pack`、`CMake`、`CMake Tools`

2. Linux
    * 安装 VSCode
    * 使用包管理器安装 gcc、g++、make、cmake
        * 比如在 Ubuntu 下是 apt，则使用命令`sudo apt install gcc g++ make cmake git -y`

**编译基础**

编译一个 C++ 程序，需要了解一些基本的编译知识。

1. 预处理
    * 处理源文件中的预处理命令
        * 比如 #include，将从源文件中包含指定文件的内容，大部分情况都是包含 *.h*、*.inl（头文件、内联函数的源文件），有些项目里还会包含 *.c* 文件，还有一些条件语句，会把部分代码去除
        * #define 会把代码中匹配到的字符串直接替换
        * 等等预处理命令
    * 去除代码中的空白字符

2. 编译
    * 将预处理过的代码转换为汇编代码

3. 汇编
    * 将汇编代码转换为机器语言，得到中间目标文件

4. 链接
    * 将得到的一个或多个中间目标文件链接起来，得到库文件（不能有 main 函数）或可执行文件（有且只能有一个 main 函数）
   
**编译详情**

1. [C/C++：编译全过程——预处理、编译、汇编、链接（包含预处理指令：宏定义，文件包括、条件编译）](https://blog.csdn.net/qq_40765537/article/details/105940800)
2. [C/C++预处理过程详细梳理（预处理步骤+宏定义#define/#include+inline函数+宏展开顺序+条件预处理+其它预处理定义）](https://blog.csdn.net/luolaihua2018/article/details/124067982)
3. [帮 C/C++ 程序员彻底了解链接器](https://blog.csdn.net/u012248972/article/details/78823165)

**项目实战**

[fisheyeStitcher](https://github.com/drNoob13/fisheyeStitcher)
