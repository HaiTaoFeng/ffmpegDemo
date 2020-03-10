# ffmpegDemo
将ffmpeg编译出来的so包集成到Android项目中，顺便检验动态库是否可以使用
注意事项：
1、编译本项目是需要设置项目中的NDK路径；
2、设置AS中的File | Settings | Appearance & Behavior | System Settings | Android SDK > SDKTOOL 把CMake勾上，使用cmake编译本项目；
3、本项目适配了AndroidX，可能会跟以前的项目不一样；
4、本项目使用的3.6.0版本的Android Studio，不一样的话可以适当改一下编译工具版本。
