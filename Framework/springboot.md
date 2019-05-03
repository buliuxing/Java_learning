# 第5节：Spring Boot



### Spring Boot简介

使用“习惯优于配置”的理念快速建立项目。

+ 独立运行的Spring项目；
+ 内嵌Servlet容器；
+ 提供starter简化Maven配置；
+ 自动配置Spring；
+ 准生产的应用监控；
+ 无代码生成和xml配置；

### 常用注解

@SpringBootApplication: 开启自动配置，自动配置源码位于spring-boot-autoconfigure.jar

​		|_@Configuratioin

​		|_ @EnableAutoConfiguration

​			|_@Import 导入配置

​				|_@ConditionalOnBean 在容器有指定的Bean条件下

​		|_ @ComponentScan

入口类，包含一个main方法

配置文件格式：properties和yaml文件

修改Tomcat端口号为例，Application.properties

```
server.port=9090
server.context-path=/helloboot
```

Application.yaml

```
server:
	port:9090
	contextPath:/helloboot
```

### starter pom

提供了绝大数场景的starter pom

常用的spring-boot-starter-web内嵌Tomcat以及Spring MVC的依赖

### 外部配置引用

常规配置和安全类配置

###Profile配置

Profile是Spring用来针对不同环境配置提供支持的，全局Profile配置使用application-{profile}.properties

通过在application.properties中设置spring.profiles.active={profile}来指定活动

