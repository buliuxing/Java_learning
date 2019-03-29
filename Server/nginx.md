# 第2节：Nginx



## nginx

Nginx(engine x)是一个高性能的HTTP和反向代理服务器，，也是一个IMAP/POP3/SMTP服务器。Nginx 既可以在内部直接支持 Rails 和 PHP 程序对外进行服务，也可以支持作为 HTTP代理服务器对外进行服务。

Nginx 做为 HTTP 服务器，有以下几项基本特性：

- 处理静态文件，索引文件以及自动索引；打开文件描述符缓冲．

- 无缓存的反向代理加速，简单的负载均衡和容错．

- FastCGI，简单的负载均衡和容错．

- 模块化的结构。包括 gzipping, byte ranges, chunked responses,以及 SSI-filter 等 filter。如果由 FastCGI 或其它代理服务器处理单页中存在的多个 SSI，则这项处理可以并行运行，而不需要相互等待。

- 支持 SSL 和 TLSSNI．

  

### 安装

```shell
#下载安装包
wget http://nginx.org/download/nginx-XX.XX.XX.tar.gz
#解压源码目录
tar -xzvf nginx-XX.XX.XX.tar.gz
#进入源码目录、配置、编译和安装
cd nginx-XX.XX.XX
./configure
make
make install
```

### 常用命令

```shell
ngnix 启动
nginx -s command
-- stop: 关闭
-- reload： 重新加载配置文件
```

### 核心配置文件

```shell
#配置工作模式
events{
     worker_connections 1024;
}

#http块
http{

    #设置转发服务器
    server{
        #监听的端口
        listen 8080;
        #匹配域名/IP
        server_name www.baidu.com;
        #匹配的路由
        location /{
        	#返回给客户端资源文件的根目录
            root html;
            #默认返回的文件名
            index index.html
        }
    }
    
    #设置转发服务器
    server{
         ......
    }
}
```

### 工作原理

Ngnix采用多线程+异步非阻塞IO事件模型处理连接请求。多进程模型包括：一个master进程，多个worker进程。

+ **Ngnix的负载均衡模块采用方式：**

  ```
  轮转法： 它处理请求就像纸牌从头到尾分发；
  IP哈希法： 众多请求下，确保同一IP的请求分发到相同的后端服务器；
  ```

+ **Ngnix高并发的处理**

  ```
  Nginx采用了Linux的epoll模型，epoll模型基于事件驱动机制，它可以监控多个事件是否准备完毕，如果OK，那么放入epoll队列中，这个过程是异步的。worker只需要从epoll队列循环处理即可。
  ```

+ **Ngnix的高可用**

  ```
  Keepalived + Ngnix实现高可用；
  1、请求不直接打到Ngnix上，先通过Keepalived（虚拟IP，VIP）
  2、Keepalived应该监控Ngnix的生命状态，进行权重分配，实现Ngnix的故障切换
  ```

  

