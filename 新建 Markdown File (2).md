<https://sourceforge.net/projects/qmake2cmake/> --qmake转换cmake小工具





```
# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

# 项目信息
project (Demo1)
# 指定生成目标
add_executable(Demo main.cc)


    cmake_minimum_required：指定运行此配置文件所需的 CMake 的最低版本；
    project：参数值是 Demo1，该命令表示项目的名称是 Demo1 。
    add_executable： 将名为 main.cc 的源文件编译成一个名称为 Demo 的可执行文件。
    
    
    aux_source_directory 命令，该命令会查找指定目录下的所有源文件，然后将结果存进指定变量名。
    # 查找当前目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
aux_source_directory(. DIR_SRCS)


# 添加 math 子目录
add_subdirectory(math)
使用命令 add_subdirectory 指明本项目包含一个子目录 math，这样 math 目录下的 CMakeLists.txt 文件和源代码也会被处理


# 添加链接库
target_link_libraries(Demo MathFunctions)
target_link_libraries 指明可执行文件 main 需要连接一个名为 MathFunctions 的链接库 。

# 生成链接库
add_library (MathFunctions ${DIR_LIB_SRCS})
add_library 将 src 目录中的源文件编译为静态链接库。
```





一般CMake 在Vision studio2008 上 构建的工程（.sln “solution”）包含 三个工程（project），分别是：**ALL_BUILD**； **工程本身**如：HelloCMake； **ZERO_CHECK**。HelloCMake就不用说了，自己要建立的那个工程；ALL_BUILD是管理整个项目的工程；ZERO_CHECK是实时监视CMakeLists.txt文件变化的工程，一旦CMakeLists.txt里的内容发生了任何变化，ZERO_CHECK就会告诉编译器要重新构建整个工程环境。详见<http://blog.163.com/jacky_ling0/blog/static/1373925712011072375418/?latestBlog>

  如我们只有一个工程（project）在解决方案（solution）中，那么ALL_BUILD 和 ZERO_CHECK工程可以删除掉。

一般由CMAKE构建的解决方案（Solution）中包含三工程（Project），分别是ALL_BUILD、ZERO_CHECK、INSTALL

ALL_BUILD只要编译这个工程，所有的工程均会编译；

ZERO_CHECK监视CMakeLists.txt文件的变化，一旦发生变化，它会告诉编译器重新构建整个工程环境。

INSTALL:将工程编译后生成的dll和exe等安装到指定目录中，具体安装位置和安装内容详见该工程的Build Event->Post-Build Event->Command Line。
--------------------- 



打印

`message("arg = ${arg}")`