# Centos

## 网络设置

虚拟机新安装的Centos7没有设置网络，要自己设置

VirtualBox 设置：

```
网络设置为 网卡1：网络地址转换(NAT)
          网卡2：仅主机(Host-Only)网络
```

CentOs操作系统

```
1、ip addr 看看有哪几个网卡　　
2、打开 vi /etc/sysconfig/network-scripts/ifcfg-eth0（每个机子都可能不一样，但格式会是“ifcfg-eth数字”），
    把ONBOOT=no，改为ONBOOT=yes
3、重启网络：service network restart
```

## SSH

**安装**  `yum install openssh-server`

**设置SSH服务为开机启动**`chkconfig sshd on`

