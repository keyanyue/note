env: VMware Redhat or centos
技术：逻辑卷管理（LVM）
具体步骤：
1.查看磁盘空间：df -Th
2.创建磁盘分区：fdisk -l
               fdisk /dev/sdb
               p-->n-->1-->t-->L-->8e-->w
               partprobe #将磁盘分区表变化信息通知内核，请求操作系统重新加载分区表，有些小报错不要紧。
3.创建物理卷：
    fdisk -l
    pvcreeate /dev/sdb1     #由fdisk -l查到LVM卷时/dev/sdb1，所以用/dev/sdb1来创建物理卷
4.扩展卷组
    pvdisplay
    vgextend
    vgdisplay
5.扩展逻辑卷
    lvextend -l +100%free /dev/mapper/volGroup-lv-root #free也可以大写
    blkid /dev/mapper/volGroup-lv-root  #查看分区文件系统类型
    e2fxck -f /dev/mapper/volGroup-lv-root  #e2fsck -f 检查分区
    resize2fs /dev/mapper/VolGroup-lv-root  #如果分区是xfs系统，则用xfs_growfs命令对文件系统进行扩展
    df -h