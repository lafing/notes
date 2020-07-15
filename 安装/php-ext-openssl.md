# 源码安装

> 进入源码包ext目录
```
cd /home/src/php-7.4.8/ext/openssl
```

> phpize找不到config.m4
```
cp ./config0.m4 ./config.md
```

> Cannot find autoconf
Cannot find autoconf. Please check your autoconf installation and the
$PHP_AUTOCONF environment variable. Then, rerun this script.
```
yum install autoconf
```