# 树莓派安装Centos7

## 1.烧录系统
    系统镜像[下载地址](http://mirror.centos.org/altarch/7/isos/armhfp/)


## 2.开机并扩展到实际的内存卡容量
    fdisk /dev/mmcblk0
    p --> d --> n --> p --> w
    reboot
    resize 2fs /dev/mmcblk0p3
    df -Th

## 3.连接wifi
    ### 安装wifi模块
    /usr/lib/firmware /brcm/
    reboot

    ### 链接无线
    nmcli d
    nmcli d wifi    #查看周围的wifi
    nmcli d wifi connect 要连接的wifi名 password ‘wifi链接密码’
    nmcli d show wlan0 #查看wlan0的状态

    ### 设置静态IP
     设置网络配置信息
     vi /etc/sysconfig/network-script/ifcfg-???   #???是wifi名

        BOOTPROTO = static
        IPADDR = 192.168.43.64
        GATEWAY = 192.168.43.1 #默认网关
        NETMASK = 255.255.255.0 #子网掩码

## 4.修改DNS
     vi /etc/resolv.conf
     nameserver 8.8.8.8
                8.8.4.4
                223.5.5.5
                114.114.114.114

    service network restart

## 5.修改时间
    yum install -y ntp
    systemctl enable ntpd
    systemctl start ntpd

## 6.修改时间
    cp /usr/share/zoneinfo/Asia/shanghai /etc/localtime