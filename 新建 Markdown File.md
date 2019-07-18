**out-of-source** build，与in-source build相对，即将编译输出文件与源文件放到不同目录中；


1,CMAKE_INCLUDE_CURRENT_DIR
自动添加 CMAKE_CURRENT_BINARY_DIR 和 CMAKE_CURRENT_SOURCE_DIR 到当前处理
的 CMakeLists.txt。相当于在每个 CMakeLists.txt 加入:
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_BINARY_DIR}
${CMAKE_CURRENT_SOURCE_DIR})





```
file(GLOB_RECURSE code_sources "./*.cpp")
file(GLOB_RECURSE code_inc "./*.h")
#aux_source_directory("./" MY_SOURCE)
```



`get_filename_component` 得到一个完整文件名中的特定部分。

```
  get_filename_component(<VAR> FileName
                         PATH|ABSOLUTE|NAME|EXT|NAME_WE|REALPATH
                         [CACHE])
```

cmake中对环境变量读写都是通过ENV前缀来访问环境变量
读取环境变量则要使用 $ENV{JAVA_HOME}这样的格式
写环境变量如下：

set( ENV{PATH} /home/martink )

    1

if语句判断环境变量是否定义要用下面的格式

if(NOT DEFINED ENV{JAVA_HOME})
    # 没有找到JAVA_HOME环境变量
    message(FATAL_ERROR "not defined environment variable:JAVA_HOME")  
endif()
#不能用if(ENV{JAVA_HOME})形式来判断是否定义 
#但可以用if($ENV{JAVA_HOME})


总结一下，就可以看出来，读取环境变量时要在ENV前加$符号，而写和if判断是否定义时,ENV{JAVA_HOME}指代变量名所以不加$符号。
--------------------- 
# 文件拷贝
```
第一种
file(GLOB texture "${CMAKE_CURRENT_SOURCE_DIR}/texture/*.*")
file(COPY  ${texture} DESTINATION  "${CMAKE_BINARY_DIR}"  )

第二种
add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD  COMMAND ${CMAKE_COMMAND} -E copy_directory "${CMAKE_CURRENT_SOURCE_DIR}/texture" "${CMAKE_CURRENT_BINARY_DIR}" )
```
