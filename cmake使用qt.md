https://qt.developpez.com/doc/5.0-snapshot/cmake-manual/



```
find_package(Qt5 REQUIRED Widgets) 
qt5_wrap_cpp( MOC widget.h) 
qt5_wrap_ui( UIC widget.ui) 
qt5_add_resources(RCC resources.qrc) 

target_link_libraries(helloworld Qt5::Widgets)//链接库
```



# vs

使用CMake生成Qt工程，编译运行的时候需要注意一些事情。如果机器上装了多个版本的Qt库的话，使用CMake生成Qt工程的时候，最容易出错了。CMake在生成工程的时候，会去搜索用户和系统的Path路径，查找系统上安装的Qt库。如果工程编译后，再去修改PATH中的Qt版本路径，会出现一些诡异的现象。像我碰到的一些情况包括：**（1）**程序启动不起来或者报错“xxx找不到符号入口点”；**（2）**资源加载不到，典型的特征是使用QRC路径（如“**:/style/default.qss**”）来加载资源会失败；**（3）**程序无故崩溃或执行结果不正常。但凡出现了这样一些情况，而恰好工程又是采用CMake管理的，那么就要考虑下Qt库版本是不是混淆了。