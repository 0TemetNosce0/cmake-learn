**out-of-source** build，与in-source build相对，即将编译输出文件与源文件放到不同目录中；


1,CMAKE_INCLUDE_CURRENT_DIR
自动添加 CMAKE_CURRENT_BINARY_DIR 和 CMAKE_CURRENT_SOURCE_DIR 到当前处理
的 CMakeLists.txt。相当于在每个 CMakeLists.txt 加入:
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_BINARY_DIR}
${CMAKE_CURRENT_SOURCE_DIR})