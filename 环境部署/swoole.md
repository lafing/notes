# 源码安装

> 1. 下载源码包
```
https://github.com/swoole/swoole-src/releases
http://pecl.php.net/package/swoole
http://git.oschina.net/swoole/swoole
```

> 2. 安装命令
```
phpize
./configure // 如果安装多版本需要添加--with-php-config=/路径/php-config
make && make install
```

> 3. 在php.ini文件添加扩展
```
echo "extension=swoole.so" > /路径/php.ini
php -m | grep swoole
```

# 问题收集
> 1. configure: error: C++ preprocessor
错误提示
	configure: error: in `/home/src/php-ext/swoole-src-4.5.2':
	configure: error: C++ preprocessor "/lib/cpp" fails sanity check
	See `config.log' for more details

yum安装
```
　　yum install glibc-headers
　　yum install gcc-c++
```