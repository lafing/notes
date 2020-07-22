# 源码安装
	

> 官网地址&教程 https://getcomposer.org/download/
```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'e5325b19b381bfd88ce90a5ddb7823406b2a38cff6bb704b0acc289a09c8128d4a8ce2bbafcd1fcbdc38666422fe2806') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

> 下载composer-setup.php文件
```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
```

> 执行安装
```
php composer-setup.php 

or

php composer-setup.php --install-dir=/usr/local/bin --filename=composer
```
如果走的第一种方式则需要移动composer.phar
```
mv composer.phar /usr/local/bin/composer
```

> 安装完成
```
composer about
```
Composer - Dependency Manager for PHP
Composer is a dependency manager tracking local dependencies of your projects and libraries.
See https://getcomposer.org/ for more information.