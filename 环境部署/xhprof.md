# PHP性能分析工具 tideway-xhprof 
选择tideway是因为有CLI模式下的工具toolkit

## 源码安装
```shell
# 下载
git clone https://github.com/tideways/php-xhprof-extension.git
phpize
./configure
make && make install
```

## 在php.ini文件中加入扩展tideways_xhprof.so
```shell
echo tideways_xhprof.so >> php.ini
```
加入新扩展需重启fpm

## 官方提供的用法
```php
<?php

tideways_xhprof_enable();

my_application(); // 这个表示业务代码逻辑

file_put_contents(
    sys_get_temp_dir() . DIRECTORY_SEPARATOR . uniqid() . '.myapplication.xhprof',
    serialize(tideways_xhprof_disable())
);
```

开启CPU和内存监控
```php
<?php

tideways_xhprof_enable(TIDEWAYS_XHPROF_FLAGS_MEMORY | TIDEWAYS_XHPROF_FLAGS_CPU);

my_application();

file_put_contents(
    sys_get_temp_dir() . DIRECTORY_SEPARATOR . uniqid() . '.myapplication.xhprof',
    serialize(tideways_xhprof_disable())
);
``` 