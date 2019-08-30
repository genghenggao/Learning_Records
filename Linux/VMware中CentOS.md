# VMware中CentOS7.6

## 一、安装CentOS7.6



## 二、设置网络NAT

1、针对Windows宿主机防火墙（可以关闭，我这里是打开的），windows下CMD中ipconfig命令查看。

![](IMG/微信截图_20190827084253.png)



DNS设置，在目录

```shell
vi /etc/resolv.conf 
nameserver 8.8.8.8
nameserver 8.8.4.4
```

参考：

https://blog.csdn.net/llluluyi/article/details/79041791



## 三、CentOS时间设置

1、安装ntp服务软件包：

```shell
yum install ntp
```

2、将ntp设置为缺省启动：

```shell
systemctl enable ntpd
```

3、修改启动参数，增加-g -x参数，允许ntp服务在系统时间误差较大时也能正常工作：

```
vi /etc/sysconfig/ntpd
```

4、启动ntp服务：

```
service ntpd restart
```

5、将系统时区改为上海时间（即CST时区）：

```
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

6、输入date命令查看时间是否正确



启动自动同步时间

```shell
timedatectl set-ntp yes
```









