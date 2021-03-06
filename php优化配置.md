# PHP优化配置

## opcache

> 关闭注释缓存
我们需要注意一个事情，在PHP开发中，一般会有大段的注释，也会被缓存到OPCache中。

> opcache不要设置过期时间
OPCache的更新策略非常简单，到期数据置为Wasted，达到设定值，清空缓存，重建缓存。
这里需要注意：在高流量的场景下，重建缓存是一件非常耗费资源的事儿。
OPCache 在创建缓存时并不会阻止其他进程读取。
这会导致大量进程反复新建缓存。所以，不要设置OPCache过期时间。

> 避免发布新代码时重复新建缓存的情况
代码预热，比如使用脚本批量调PHP 访问URL，或者使用OPCache 暴露的API 如opcache_compile_file() 进行编译缓存。