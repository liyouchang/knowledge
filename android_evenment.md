[Ubuntu 14.04 x64 安装 Android SDK](nblogs.com/sink_cup/archive/2011/10/31/ubuntu_x64_android_sdk_java.html)
====================


####安装32位库文件
2013年9月的iPhone 5s是第一款64位手机，而Android手机还都是32位的，落后了一年。

Android SDK中的adb程序是32位的，Ubuntu x64系统需要安装32位库文件，用于兼容32位的程序。如果不安装，adb会出错：java.io.IOException: error=2

sudo apt-get install -y libc6-i386 lib32stdc++6 lib32gcc1 lib32ncurses5 lib32z1


####安装Android SDK
#####安装jre

`sudo apt-get install openjdk-7-jre`

官方下载页面，选择“USE AN EXISTING IDE”，下载不含IDE的纯SDK：[](http://developer.android.com/sdk/index.html)
```
cd ~/Downloads/
wget http://dl.google.com/android/android-sdk_r22.6.2-linux.tgz
tar -zxvf android-sdk_r22.6.2-linux.tgz
echo 'export ANDROID_SDK="/opt/android/adt-bundle-linux-x86_64-20140321/sdk"' >> ~/.bashrc
echo 'export PATH="$PATH:$ANDROID_SDK/tools:$ANDROID_SDK/platform-tools"' >> ~/.bashrc
```

关闭“终端”，再开启一个“终端”，让环境变量生效。

启动Android SDK Manager
```
  android
```

根据需要，选择最新版的Android SDK Platform-tools、Samples for SDK等等下载即可（约2.6GB）。

注意：一定要安装Android Support Repository，否则gradle会报错。

如果下载速度慢，ping g.cn，为dl-ssl.google.com设置hosts，并且在Android SDK Manager——》菜单——》Tools——》Options中选中“Force https to http”





安装android NDK
=================

echo 'export ANDROID_NDK="/opt/android/android-ndk-r9d"' >> ~/.bashrc

