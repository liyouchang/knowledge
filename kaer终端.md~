Kaer 终端操作
=================================================

telnet 用户名 root 密码 970326@dmin


在终端可以使用tftp从PC上获取文件,如
>tftp -g -r libstdc++.so.6.0.12 10.10.0.193

终端的tmp目录是内存，其他目录是flash，这该死的终端内存比flash要大。


###arm 编程

直接用int指针进行内存操作，int指针会进行字节对齐，导致读到的数据不正确。
>int msgLen= *((int*)&headBuf[2]); //arm will failed with this
          > int msgLen;
           > memcpy(&msgLen,&headBuf[2],4);
