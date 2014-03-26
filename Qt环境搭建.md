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



-xplantform



qmake编译
------------------------
####android编译 ubuntu

* 问题1：
_i686-linux-android-g++: error trying to exec 'cc1plus': execvp: No such file or directory_

     _/usr/android/android-ndk-r9d/toolchains/x86-4.8/prebuilt/linux-x86_64/libexec/gcc/i686-linux-android/4.8_  目录中有cc1和cc1plus，将这两个文件设置可执行权限可解决问题。

