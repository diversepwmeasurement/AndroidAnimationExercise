
# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.22.1)

# Declares and names the project.

project("cpp_native")

#定义一个全局变量包含了所有要编译的C文件
file(GLOB BZIP bzip/*.c)
message("11111")
message("${BZIP}")
message("22222")
#导入头文件
include_directories(bzip)
include_directories(logcat)
# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
# You can define multiple libraries, and CMake builds them for you.
# Gradle automatically packages shared libraries with your APK.

add_library( # Sets the name of the library.
        cpp_native

        # Sets the library as a shared library.
        SHARED
        #将bzip下的.c文件添加到library
#        ${BZIP}
        bspatch.c
        # Provides a relative path to your source file(s).
        cpp_native.cpp)

# Searches for a specified prebuilt library and stores the path as a
# variable. Because CMake includes system libraries in the search path by
# default, you only need to specify the name of the public NDK library
# you want to add. CMake verifies that the library exists before
# completing its build.

find_library( # Sets the name of the path variable.
        log-lib

        # Specifies the name of the NDK library that
        # you want CMake to locate.
        log)

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in this
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries( # Specifies the target library.
        cpp_native

        # Links the target library to the log library
        # included in the NDK.
        ${log-lib})
