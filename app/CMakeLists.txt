# cmake参考 https://www.jianshu.com/p/528eeb266f83

cmake_minimum_required(VERSION 3.4.1)


# 需要引入我们头文件,以这个配置的目录为基准
include_directories(src/main/jniLibs/include)

# 添加共享库（so）搜索路径
LINK_DIRECTORIES(${CMAKE_SOURCE_DIR}/src/main/jniLibs/armeabi-v7a)

# 指定源文件目录，把当前工程目录下的 src/main/cpp 目录的下的所有 .cpp 和 .c 文件赋值给 SRC_LIST
AUX_SOURCE_DIRECTORY(${CMAKE_SOURCE_DIR}/src/main/cpp SRC_LIST)


#这个一般不用怎么改，最终把cpp编译成共享库 native-lib
add_library(
        # 编译生成的库的名称叫native-lib，对应System.loadLibrary("native-lib");
        native-lib
        # Sets the library as a shared library.
        SHARED
        # Provides a relative path to your source file(s).
        ${SRC_LIST}
)


#为native-lib 链接额外的库，例如ffmpeg、ndk库
target_link_libraries(
        native-lib
        # 编解码(最重要的库)
        avcodec
        # 设备信息
        avdevice
        # 滤镜特效处理库
        avfilter
        # 封装格式处理库
        avformat
        # 工具库(大部分库都需要这个库的支持)
        avutil
        # 后期处理
#        postproc-54
        # 音频采样数据格式转换库
        swresample
        # 视频像素数据格式转换
        swscale
        # 链接 android ndk 自带的一些库
        android
        # Links the target library to the log library
        # included in the NDK.
        log)