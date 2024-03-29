## centos7中安装python3
1. 安装编译工具(root)
```shell
yum -y groupinstall "Development tools"
yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel
yum install -y libffi-devel zlib1g-dev
yum install zlib* -y
```
2. 下载安装包
```shell
wget wget https://www.python.org/ftp/python/3.7.2/Python-3.7.2.tar.xz
```
**linux中wget命令没有找到:**
`yum -y install wget`

3. 解压
```shell
tar -xvJf  Python-3.7.2.tar.xz
```
报错:`bzip2: (stdin) is not a bzip2 file.`,使用`tar -jxvf Python-3.7.2.tar.xz`
报错:`gzip: stdin: not in gzip format`, 使用`tar -xvf Python-3.7.2.tar.xz`

4. 创建编译安装目录
`mkdir /usr/local/python3`

5. 安装
```shell
cd Python-3.7.2
./configure --prefix=/usr/local/python3 --enable-optimizations --with-ssl
#第一个指定安装的路径,不指定的话,安装过程中可能软件所需要的文件复制到其他不同目录,删除软件很不方便,复制软件也不方便.
#第二个可以提高python10%-20%代码运行速度.
#第三个是为了安装pip需要用到ssl,后面报错会有提到.
make && make install
```

6. 创建软链接
```shell
ln -s /usr/local/python3/bin/python3 /usr/local/bin/python3
ln -s /usr/local/python3/bin/pip3 /usr/local/bin/pip3
```

7. 验证是否安装成功
```shell
python3 -V
pip3 -V
```

8. 安装pipenv

[几个命令](https://www.cnblogs.com/ZGreMount/p/7668749.html)
[虚拟机不能联网问题](https://blog.csdn.net/cyn_653620/article/details/80301540)
[ssh登陆虚拟机](https://www.cnblogs.com/lxg0/p/6413965.html)
[安装git](https://www.cnblogs.com/flying_bat/p/11088113.html)
报错:`致命错误：curl/curl.h：没有那个文件或目录 #include "curl/curl.h`
解决方案:`yum -y install curl-devel`
SSH登陆VirtualBox:`ssh -p 9022 root@localhost`
