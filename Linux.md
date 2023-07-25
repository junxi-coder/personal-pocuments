#### 一、kill -9 端口号     ‘杀死进程’

#### 二、tar

tar命令用来打包一个目录，它支持三种格式：".tar"、".bz2"和".gz"

```Linux
压缩
tar -cvf [文件名].tar [文件目录] //打包成.tar文件
tar -jcvf [文件名].tar.bz2 [文件目录] //打包成.bz2文件
tar -zcvf [文件名].tar.gz [文件目录] //打包成.gz文件
```

```Linux
解压
tar -xvf [文件名].tar //解压到当前文件
tar -xvf [文件名].tar -C [文件目录] //将.tar文件解压到指定目录
tar -jxvf [文件名].tar.bz2 -C [文件目录] //解压.bz2文件到指定目录
tar -zxvf [文件名].tar.gz -C [文件目录] //解压.gz文件到指定目录
```

#### 三、tail -f test.log   ’一旦有更新便输出‘



#### 四、ps -ef | grep xxx 



#### 五、安装nginx

**1.安装依赖包**

```
//一键安装上面四个依赖
yum -y install gcc zlib zlib-devel pcre-devel openssl openssl-devel
```

**2.下载并解压安装包**

```
//创建一个文件夹
cd /usr/local
mkdir nginx
cd nginx
//下载tar包
wget http://nginx.org/download/nginx-1.13.7.tar.gz
tar -xvf nginx-1.13.7.tar.gz
```

**3.安装nginx**

```
//进入nginx目录
cd /usr/local/nginx
//进入目录
cd nginx-1.13.7
//执行命令 考虑到后续安装ssl证书 添加两个模块
./configure --with-http_stub_status_module --with-http_ssl_module
//执行make命令
make
//执行make install命令
make install
```

**4.启动nginx服务**

```
 /usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
```

**5.修改nginx.conf**

![image-20230407112604486](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230407112604486.png)

**6.重启nginx**

```
/usr/local/nginx/sbin/nginx -s reload
```

**7.ps -ef | grep nginx**

查看nginx进程是否启动

**8.若想使用外部主机访问nginx，需要关闭服务器防火墙或开放nginx服务端口，端口为上一步nginx.conf的配置端口：**

centOS6及以前版本使用命令： systemctl stop iptables.service

centOS7关闭防火墙命令： systemctl stop firewalld.service

关闭防火墙会导致服务器有一定风险，所以建议是单独开放服务端口 ：

开放80端口：

firewall-cmd --zone=public --add-port=80/tcp --permanent

查询端口号80 是否开启：

firewall-cmd --query-port=80/tcp

(开放完端口号需要重启防火墙)重启防火墙：

firewall-cmd --reload

随后访问该ip:端口 即可看到nginx界面。
————————————————安装完成一般常用命令

进入安装目录中，

命令： cd /usr/local/nginx/sbin

启动，关闭，重启，命令：

./nginx 启动

./nginx -s stop 关闭

./nginx -s reload 重启