AMH V4.5 重新部署了一次安装脚本，修改一系列BUG，已完美支持CENTOS7,树莓派，

Fedora，Aliyun，Amazon，debian，Ubuntu，Raspbian，Deepin等等.....

修复CENTOS7,不显示系统，IP，内存使用量，等等，增加一系列模块扩展：

IonCube_loaders(这个模块官方没有支持PHP7以上的所以暂时不支持PHP7,PHP7.1，

其他目前都已修复，支持到安装包的PHP5.3-PHP7.1)，Memcache-3.0.8，Memcached-2.2.0，

Memcached-1.4.15（服务端），Redis-3.0.7，php-redis2.7.7（服务端），Swoole-1.9.9，Qiniu-1.1（七牛备份），

增加了Nginx-1.10.3和Tengine-2.2.0选择安装（注：由于Tengine目前暂不支持openssl-1.1.0版本的编译，

所以选择Tengine时候安装的openssl是1.0.2e版本）

增加本地安装，可现行下载安装包到本地后再执行脚本，有利于节约安装时间。


---------------------------------------------------------------------------------------------------------------

一键安装包下载地址：

http://soft.im/amh/amh4.5.tar.gz

一键安装包下载后执行:

yum install -y wget

yum install -y screen

yum install -y vim

screen -S amh

本地包解压：

tar -zxf /root/amh4.5.tar.gz -C /home;

再运行脚本安装，选择localhost或者Online随意，优先执行本地安装包，如果没下载安装包在线安装请选择(Online)

wget http://soft.im/amh/amh.sh && chmod 775 amh.sh && ./amh.sh 2>&1 | tee amh.log

---------------------------------------------------------------------------------------------------------------

很多人机子配置差或者网络差，安装时候SSH断线，安装前最后执行screen

screen -S amh  #创建

万一SSH断线，恢复连接后

screen -r amh #恢复

---------------------------------------------------------------------------------------------------------------

对于小内存的机子建议设置交换区再安装

dd if=/dev/zero of=/swapfile bs=1k count=2048000 --获取要增加的2G的SWAP文件块（2048000可以自行定义需要多大自行修改）

mkswap /swapfile     -- 创建SWAP文件

swapon /swapfile     -- 激活SWAP文件

swapon -s            -- 查看SWAP信息是否正确

echo "/var/swapfile swap swap defaults 0 0" >> /etc/fstab     -- 添加到fstab文件中让系统引导时自动启动

注意, swapfile文件的路径在/var/下 

编译完后, 如果不想要交换分区了, 可以删除:

swapoff /swapfile

rm -fr /swapfile

---------------------------------------------------------------------------------------------------------------

Shadowsocks模块

解压后放入

/root/amh/modules/目录，面板或者SSH安装，（注：SSH安装可自选端口）

模块下载地址：http://soft.im/amh/amh-ss.zip