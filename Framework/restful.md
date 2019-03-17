# 第10节：Restful API



### 概述

一种优雅的URI表述方式，表示资源的状态和状态的转移。

### 特征

+ 通过POST、GET、PUT、DELETE对服务器资源操作
+ URL中通常不出现动词，只有名词
+ 使用JSON不使用XML

### 设计

```
/模块/资源/{标示}/集合/...

e.g.
GET /user/{uid}/frends ——> 好友列表
GET /seckill/{id}/detail --> 详情页
POST /seckill/{id}/exposer --> 暴露秒杀
POST /seckill/{id}/{md5}/execution -->执行秒杀
```

