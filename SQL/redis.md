# 第2节：Redis



+ ### 概述

  NoSQL（Not Only SQL）数据库，是基于内存的数据库，每秒支持十几万次的读/写操作，其性能远超数据库，并支持集群、分布式和主从同步等配置。因此在高速读/写场合，比如秒杀、抢红包等，出现高并发情况，此时需要将高速读写的数据，缓存到Redis中，当业务结束（即秒杀结束时），再异步批量写入数据库，完成持久化。

+ ### Redis 的安装

  ```shell l
  #下载安装包
  wget http://download.redis.io/releases/redis-5.0.3.tar.gz
  tar -xzvf redis-5.0.3.tar.gz
  cd redis-5.0.3
  #编译后产生src文件夹和conf文件
  make
  
  #修改conf文件，设置后台启动
  vi redis.conf
  daemonize yes  #设置后台启动redis
  
  #启动redis服务
  src/redis-server redis.conf
  
  #redis-cli命令设置为全局,启动客户端
  cp src/redis-cli /usr/local/bin/
  redis-cli -h host -p port
  
  #关闭redis
  redis-cli shutdown
  ```

+ ###基本类型

  |  数据结构  |     常用命令     | 命令 |
  | :--------: | :--------------: | :--: |
  |   String   | 可以存储任何形式 |      |
  |    List    |                  |      |
  |    Set     |                  |      |
  |    Hash    |                  |      |
  | Sorted Set |                  |      |

  

