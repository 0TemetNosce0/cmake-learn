https://qt.developpez.com/doc/5.0-snapshot/cmake-manual/



```
find_package(Qt5 REQUIRED Widgets) 
qt5_wrap_cpp( MOC widget.h) 
qt5_wrap_ui( UIC widget.ui) 
qt5_add_resources(RCC resources.qrc) 

target_link_libraries(helloworld Qt5::Widgets)//链接库
```