---
tags: []
---
# Cmake

1. **创建文件**：`CMakeList.txt`。

```CMake
cmake_minimum_required(VERSION 3.15)
project(test_project)
add_executable(test_project main.cpp)  //(可执行程序,源文件程序)
```

- `cmake_minimum_required`:指定使用的cmake。
- `project`:定义工程名，并且可以指定工程的版本，工程描述，web主页地址，支持的语言。
- `add_executable`:定义工程会生成的一个可执行文件。源文件名字可以是多个，多个源文件名字之间可以使用空格间隔或者使用`;`间隔。
1. **执行cmake文件**：`cmake CMakeList.txt`。
因为执行`cmake`之后会生成一系列文件，所以我们建立一个文件夹：`build`。然后进入`build`目录，执行`cmake ..`即可，多余文件即会进入`build`目录。
由于源程序可能文件过多，我们使用`set`命令设置变量。

## `set`函数作用

### 设置变量

- `set(VARIABLE_NAME value1 value2 value3)`：这会将多个值赋给一个变量，实际效果是将这些值作为一个列表处理。
可以通过以下方式设置变量并获取。

```cmake
set(MY_VARIABLE "Hello, World!")
message(${MY_VARIABLE})
```

### 指定C++版本

1. 通过写入`CMakeList`方式指定C++14版本

```CMake
set(CMAKE_CXX_STANDARD 14)
```

1. 通过`cmake`命令指定

```cmake
cmake CmakeList.txt -DDCMAKE_CXX_STARDARD=14
```

### 指定输出路径

指定输出路径也有一个宏，`EXECUTABLE_OUTPUT_PATH`。

```CMake
set(HOME /home/bin/sort)
set(EXECUTABLE_OUTPUT_PATH &{HOME}/bin)
```
