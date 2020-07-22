# 源码安装

## 下载源码包
> 国内镜像
http://mirrors.sohu.com/
```
wget http://mirrors.sohu.com/php/php-7.4.8.tar.gz
```

## 安装
> 官方安装教程
https://www.php.net/manual/en/install.unix.nginx.php
```
tar zxf php-7.4.8.tar.gz
cd php-7.4.8
./configure --enable-fpm --with-mysqli
make
sudo make install

```

