
[copy-a-file-to-build-directory-after-compiling-project-with-qt](http://stackoverflow.com/questions/19066593/copy-a-file-to-build-directory-after-compiling-project-with-qt)

This is what we are using in QtSerialPort:
```
target_headers.files  = $$PUBLIC_HEADERS
target_headers.path   = $$[QT_INSTALL_HEADERS]/QtSerialPort
INSTALLS              += target_headers

mkspecs_features.files    = $$QTSERIALPORT_PROJECT_ROOT/src/serialport/qt4support/serialport.prf
mkspecs_features.path     = $$[QT_INSTALL_DATA]/mkspecs/features
INSTALLS                  += mkspecs_features
```
Basically, you set the files and path for the target, and then append that into the INSTALLS variable. What you still need is the $$OUT_PWD variable which we are also using extensively in QtSerialPort. That will provide you the root of the build directory.

It is one of those undocumented qmake features, but it is very useful.

Also, for the source directory in general at large, you should not assume "." and so forth because that may be different as you run through a wrapper application in which the "." will point to that and not what you expect: the qmake source project root. In those cases, it is safer to use the PWD variable which points to the source as opposed OUT_PWD which points to the build folder.

Just to give a rough example about the difference o those two variables with a real world scenario, here you can find what we are doing in QtSerialPort:
```
system("echo QTSERIALPORT_PROJECT_ROOT = $$PWD >> $$OUT_PWD/.qmake.cache")
system("echo QTSERIALPORT_BUILD_ROOT = $$OUT_PWD >> $$OUT_PWD/.qmake.cache")
```
where the former is the root for the source project, and the latter for the build directory. They may be the same, but in many cases they are not, e.g. when building through QtCreator just for one of those.


