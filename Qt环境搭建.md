Qt环境搭建
============================

Qt在线安装：
-------------------------
Qt在线安装更新工具默认使用官方的源，国内访问比较慢，可以在setting中增加国内的源来提高更新速度，如下面的源：

http://mirrors.ustc.edu.cn/qtproject/online/qtsdkrepository/windows_x86/root/qt/

**我将去掉源码包后进行安装，下载速度较快**


qt源码编译
-------------------------
编译32位静态库版本
./configure -no-gtkstyle  -static -no-icu -verbose -platform linux-g++-32 -confirm-license -developer-build -opensource -nomake examples -nomake tests -prefix /usr/local/Qt5-static-gcc_32

windows编译32位静态库
configure  -static -no-icu -platform win32-msvc2010 -confirm-license -developer-build -opensource -nomake examples -nomake tests -prefix D:\Qt\5.2.1\msvc2010-static


configure -prefix D:\Qt\5.2.1\msvc2010-static -platform win32-msvc2010  -confirm-license  -opensource -static -nomake tests -nomake examples  -no-compile-examples -skip declarative -skip doc -skip graphicaleffects  -skip multimedia -skip quick1 -skip quickcontrols -skip script -skip sensors -skip serialport -skip svg -skip tools -skip translations -skip webkit -skip webkit-examples -skip x11extras -skip xmlpatterns



-xplantform


####build for hisi arm
./configure -no-gtkstyle  -static -no-icu -verbose -no-c++11 -xplatform  hisi-linux-arm -confirm-license -developer-build -opensource -nomake examples -nomake tests -prefix /opt/Qt/hisi



qmake编译
------------------------
####android编译 ubuntu

* error 1：
_i686-linux-android-g++: error trying to exec 'cc1plus': execvp: No such file or directory_

     _/usr/android/android-ndk-r9d/toolchains/x86-4.8/prebuilt/linux-x86_64/libexec/gcc/i686-linux-android/4.8_  目录中有cc1和cc1plus，将这两个文件设置可执行权限可解决问题。
     
* error 2：
使用/usr/android/android-ndk-r9d/toolchains/arm-linux-androideabi-4.8/prebuilt/linux-x86_64/bin/arm-linux-androideabi-g++ 编译，出现Fatal error: invalid -march= option： `armv7-a' 错误

    是因为无法执行as命令，将/usr/android/android-ndk-r9d/toolchains/arm-linux-androideabi-4.8/prebuilt/linux-x86_64/arm-linux-androideabi/bin目录中的as软链接到../../bin/arm-linux-androideabi-as上即可解决问题，同样的arm-linux-androideabi-as要有可执行权限。ln -s ../../bin/arm-linux-androideabi-as as
    
    * Ubuntu的ndk解压缩后很多链接和权限都没有设置，需要进行设置才可进行编译，如果遇到相关问题，可以考虑这方面的因素。


