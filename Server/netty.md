# 第3节：Netty



### Netty简介

Netty是一个异步事件驱动的网络应用框架，用于快速开发可维护的高性能服务器和客户端，并在RPC框架和消息中间件中广泛应用。

### Netty使用

引入Maven依赖

```java
    <dependency>
        <groupId>io.netty</groupId>
        <artifactId>netty-all</artifactId>
        <version>4.1.6.Final</version>
    </dependency>
```

实现服务端部分

```java
public class NettyServer{
    
    public static void main(String[] args){
        ServerBootstrap serverBootstrap = new ServerBootstrap();
        
        NioEventLoopGroup boos = new NioEventLoopGroup();//创建新链接
        NioEventLoopGroup worker = new NioEventLoopGroup();//读取数据和实现业务逻辑
        
        serverBootstrap
            .group(boos, worker)
            .channel(NioServerSocketChannel.class)
            .childHandler(new ChannelInitializer<NioSocketChannel>(){
                protected void initChannel(NioSocketChannel ch){
                    ch.pipeline().addLast(new StringDecoder());
                    ch.pipeline().addLast(new SimpleChannelInboundHandler<String>() {
                    @Override
                    protected void channelRead0(ChannelHandlerContext ctx, String msg) {
                                System.out.println(msg);
                    }
                    });
                }
            })
            .bind(8000);
    }
}
```

实现客户端部分

```java
public class NettyClient {
    public static void main(String[] args) throws InterruptedException {
        Bootstrap bootstrap = new Bootstrap();
        NioEventLoopGroup group = new NioEventLoopGroup();

        bootstrap.group(group)
                .channel(NioSocketChannel.class)
                .handler(new ChannelInitializer<Channel>() {
                    @Override
                    protected void initChannel(Channel ch) {
                        ch.pipeline().addLast(new StringEncoder());
                    }
                });

        Channel channel = bootstrap.connect("127.0.0.1", 8000).channel();

        while (true) {
            channel.writeAndFlush(new Date() + ": hello world!");
            Thread.sleep(2000);
        }
    }
}
```

### Netty入门

<https://juejin.im/book/5b4bc28bf265da0f60130116/section/5b6a1a9cf265da0f87595521>

