# PHP性能分析工具 tideway-xhprof 
> tideway-xhprof
https://github.com/tideways/php-xhprof-extension
选择tideway是因为有CLI模式下的工具toolkit

> toolkit CLI模式下的GUI工具
https://github.com/tideways/toolkit

## 一、源码安装
```shell
# 下载
git clone https://github.com/tideways/php-xhprof-extension.git
phpize
./configure
make && make install
```

## 二、在php.ini文件中加入扩展tideways_xhprof.so
```shell
echo tideways_xhprof.so >> php.ini
```
加入新扩展需重启fpm

## 三、官方提供的用法
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

$data = tideways_xhprof_disable();
file_put_contents('/tmp/app.xhprof', json_encode($data));
``` 
用serialize序列化数据会导致toolkit会报错，改成json_encode即可。

## 四、用toolkit分析性能问题
安装在下方

> tk analyze-xhprof /tmp/app.xhprof 
```shell
[root@localhost tmp]# tk analyze-xhprof /tmp/app.xhprof 
Showing XHProf data by Exclusive Wall-Time
+-------------------+-------+-----------+------------------------------+
|     FUNCTION      | COUNT | WALL-TIME | EXCL  WALL-TIME (>= 4.75 MS) |
+-------------------+-------+-----------+------------------------------+
| file_get_contents |     1 | 47.50 ms  | 47.50 ms                     |
+-------------------+-------+-----------+------------------------------+
```

# Toolkit - CLI模式下的GUI工具 

* 先安装好Go（如果还没安装的话）

```shell
# 下载安装
go get github.com/tideways/toolkit

# 环境配置
export GOPATH="/home/$USER/code/golang"

# 安装完后加入到bin目录中
cp /home/$USER/code/golang/bin/toolkit /usr/local/bin/tk
```
