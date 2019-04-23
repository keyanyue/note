# centos7安装python3并与python2共存

## 1.查看已安装的python
    python -V
    which python -->cd   -->ll python*

## 2.修改自带的python为python2&安装依赖包
    mv python python2
    yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make

## 3.编译安装python3
    wget https://www.python.org/ftp/python/3.6.2/Python-3.6.2.tar.xz
    ### 解压
        tar -xvjf Python-3.6.2.tar.xz

        cd Python-3.6.2
    
    ### 编译安装
    ./configure prefix=/usr/local/python3
    make&&make install

    ### 添加软链接到 /usr/bin
    ln -s /usr/local/python3/bin/python3 /usr/bin/python

因为yum 需要python2支撑，所以我们需要修改yum配置
    vim /usr/bin/yum
        修改 #！/usr/bin/python2
        同理 vim /usr/libexec/urlgrabber-ext-down