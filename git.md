git 
====================================

这里介绍如何在Windows下创建一个项目，详细的Git使用方式参见
http://git-scm.com/book/zh

1.  安装git客户端，Windows：http://msysgit.github.io/
2.  生成ssh公共密钥，运行Git Bash，运行命令 ‘ssh-keygen’，有三次输入，全部回车使用默认值即可，不要改变生成文件的路径，生成的文件在~/.ssh文件夹下

3. 将生成的pub文件(.ssh/id_rsa.pub)和项目名称交给git服务器管理员，如果有多人需要此项目权限，则应该发多份pub文件给git服务器管理员。git服务器管理员配置项目及权限。
可以将所有人的计算机的ssh密钥登记好，需要增加项目和新的用户权限时，将姓名告诉管理员。
4. 判断权限是否添加：输入如下命令，连接关闭则权限已添加
$ ssh git@MYSERVER
ERROR:gitosis.serve.main:Need SSH_ORIGINAL_COMMAND in environment.
Connection to MYSERVER closed.

5. 创建新档案：在Git Bash运行
mkdir myproject
cd mypyroject
git init
git remote add myserver git@MYSERVER:myproject.git
# do some work, git add and commit files,this is important, with out a commit the push will failed

git push myserver master:refs/heads/master





Git config

git config --global color.ui true
Git config --global core.editor vi
