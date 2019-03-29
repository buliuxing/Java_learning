# 第4节：Jmeter



### 简介

JMeter是开源软件Apache基金会下的一个性能测试工具，用来测试部署在服务器端的应用程序的性能。

### 安装

```shell
官网（http://jmeter.apache.org/）下载安装包，配置环境变量
1. 命令 vim ~/.bash_profile （编辑环境变量配置文件）

2. 配置export JMETER_HOME=/Users/.../apache-jmeter-5.1.1

       export PATH=$PATH:$JMETER_HOME/bin 

3. 输入 source .bash_profile生效
```

GUI界面需要进入apache-jmeter-5.1.1/bin/jmeter启动。

### 添加测试计划

+ 右击“测试计划”>添加>Threads（Users）>线程组

  ```
  线程数：指模拟的线程数
  Ramp-Up Period：虚拟用户增长时长，指这段时间内完成线程数的请求，单位为s。
  循环次数：设置线程循环的次数，默认为1
  ```

### 添加测试页面

+ 右击“线程组” > “添加” > “Sampler” > “HTTP请求”

  ```
  服务器名称或IP
  端口号
  HTTP请求的方式
  请求传递的参数
  ```

### 添加结果监听器

+ 右击“线程组” > “监听器” > “察看结果树”来查看性能测试过程中请求和响应信息

### 界面

![](https://ww1.sinaimg.cn/large/007rAy9hly1g1ji0lzmnzj31c00u0dlc.jpg)

