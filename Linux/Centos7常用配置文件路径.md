# centos7常用的配置文件路径

## 网络部分
> Ip地址，子网掩码等配置文件路径： /etc/sysconfig/network-scripts  tips: BOOTPROTO=none #等号后面写：dhcp表示动态获取ip地址，satic表示静态IP，none表示不指定，默认就是静态IP。
> DNS配置文件：/etc/resolv.conf
> 设置主机和IP绑定信息：/etc/hosts
> 设置主机名： /etc/hostname