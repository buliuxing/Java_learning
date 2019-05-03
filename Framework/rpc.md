# 第9节：RPC工具:Dubbo



### Dubbo 简介

一款分布式服务框架，提供高性能和透明化的RPC远程服务调用方案，SOA服务治理方案。

![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1556637237583&di=88cadbf467d80b9c5566ea6697ea590c&imgtype=0&src=http%3A%2F%2Fimage.bubuko.com%2Finfo%2F201801%2F20180118233049340612.png)

+ Provider：暴露服务的服务提供方；
+ Consumer：调用远程服务的服务消费方；
+ Register：服务注册与发现的注册中心；
+ Monitor：统计服务的调用次数和调用时间的监控中心；

**调用流程**：

1、服务容器负责启动，加载，运行服务提供者；

2、服务提供者在启动时，向注册中心注册自己提供的服务；

3、服务消费者在启动时，向注册中心订阅自己所需的服务；

4、注册中心返回服务提供者地址列表给消费者，如果有变更，注册中心将基于长连接推送变更数据给消费者；

5、服务消费者，从提供者地址列表中，基于软负载均衡算法，选一台提供者进行调用，如果调用失败，再选另一台调用；

6、服务消费者和提供者，在内存中累计调用次数和调用时间，定时每分钟发送一次统计数据到监控中心；

### Dubbo + Zookeeper + Spring 搭建

主要步骤：

1. 安装Zookeeper,启动；
2. 创建MAVEN项目，构建Dubbo+Zookeeper+Spring实现的简单Demo；
3. 安装Dubbo-admin，实现监控。

参考：<https://www.jianshu.com/p/9cbfb8679e1d>

