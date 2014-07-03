GoAgent_Linux  
============================
####依赖Dependence

- 必选
	1. python2(建议安装python2.7，如需在Linux上传或安装gevent需先安装python-dev)
- 可选
	1. gevent 1.0(提升多线程性能，强烈建议安装)
	2. greenlet (gevent的依赖，一般安装gevent会自动安装)
	3. python-vte(基于GTK的简单GUI所需)
	4. python-openssl 0.13(生成证书所需，强烈建议安装，如删除了goagent自动证书则必须安装)
	5. pycrypto(RC4加密所需，建议安装)
	6. python-appindicator(Unity桌面下的托盘组件，其他桌面不必安装)

####Ubuntu

```sudo apt-get install python-dev python-greenlet python-gevent python-vte python-openssl python-crypto python-appindicator```

- 如果gevent版本是0.13则需要用下面的方法安装1.0版，python-appindicator为ubuntu专有，其他系统用户不用管,python-vte 位gtk托盘窗口所需，其他发行版请自行根据对应系统安装所需软件

#####安装gevent
需要在安装 python-dev 之后才能正确安装gevent和上传server，安装gevent需要安装了 gcc(Linux/Unix) 或 xcode(Mac OSX)。

```Bash
sudo apt-get install python-dev python-pip && sudo pip install gevent --upgrade
```

- 也可以手动编译安装

如果greenlet版本低于0.4.0会导致gevent装不上，请先使用以下命令安装greenlet（0.4.2）

```Bash
wget http://mirrors.aliyun.com/pypi/packages/source/g/greenlet/greenlet-0.4.2.zip && unzip greenlet-0.4.2.zip && cd greenlet-0.4.2 && sudo python setup.py install
```

安装gevent（1.0）

```Bash
wget http://mirrors.aliyun.com/pypi/packages/source/g/gevent/gevent-1.0.tar.gz && tar xvzpf gevent-1.0.tar.gz && cd gevent-1.0 && sudo python setup.py install
```

如果不想安装gevent可以下载[gevent-1.0-py2.7-linux.egg](https://github.com/binyuj/gevent-egg/raw/egg/gevent-1.0-py2.7-linux.egg) [gevent-1.0dev-macosx-intel.egg](https://goagent.googlecode.com/files/gevent-1.0dev-macosx-intel.egg)放local文件夹

####上传

[下载goagent](https://nodeload.github.com/goagent/goagent/legacy.zip/3.0)，解压，终端cd至goagent所在目录

- 在server目录下，终端执行
```Bash
python uploader.zip
```
- 根据提示输入你自己创建的appid（若要同时上传多appid在appid之间用|隔开）和你的Gmail帐号和密码(如果开启了两步验证，密码为16位的应用程序专用密码）

####运行客户端

在local目录下，终端执行
```bash
python proxy.py
```
也可以赋予proxy.py可执行权限之后直接双击proxy.py。（在proxy.py上面右击，属性的权限中勾选允许以程序执行文件）

直接运行goagent-gtk.py可以使用gtk托盘方式运行goagent。 运行addto-startup.py即可加入开机启动。也可以自行添加一个启动项，命令为
```bash
python /path/to/goagent/local/goagent-gtk.py
```

其中路径修改为自己系统中goagent-gtk.py的路径 使用sudo提权之后可以自动导入证书，部分浏览器请自行手动导入证书

####退出

如果是直接终端使用"python proxy.py"运行，在终端按"Ctrl+C"组合键可终止运行;如果使用gtk托盘，在托盘图标上右键菜单有退出选项。直接关闭终端窗口也会退出。如果以后台进程运行，先用"ps aux | grep proxy.py"找到goagent的PID，然后直接kill对应的PID 。

```bash
ps aux|grep proxy.py|grep -v "grep"|awk '{print $2}'|xargs kill
```