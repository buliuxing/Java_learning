# 第1节：常用命令



## 命令：grep

**作用**：查询文本

**常用参数**：

​       -R 以递归方式读取每个目录的文件

​       -A 匹配到搜索行以及该行后面的num行

​       -B 匹配到搜索行以及该行前面的num行

**常用场景**：

​      查找日志文件中包含的字段：

```shell
grep "a" a.log
```



## 命令：netstat

**作用**：显示网络连接和信息

**常用参数**：

​       -a 显示所有socket，包括正在监听的

​       -l 显示有在 Listen (监听) 的服务状态

　　-n 以网络IP地址代替名称，显示网络连接情形

　　-p 显示建立相关连接的程序名和PID

　　-t 显示TCP协议的连接情况

　　-u 显示UDP协议的连接情况

**常用场景**：

​      查询占用端口号情况：

```shell
netstat -nlp | grep port
```



## 命令：ps

**作用**：显示当前系统存在的进程

**常用参数**：

​       -aux是显示详细信息的参数

**常用场景**：

​      查询占用端口号情况：

```shell
ps -aux | grep process
```



## 命令：kill

**作用**：显示当前系统存在的进程

**常用参数**：

​       -aux是显示详细信息的参数

**常用场景**：

​      查询占用端口号情况：

```shell
ps -aux | grep process
```



## 命令：top

**作用**：查看服务器负载的命令

**常用参数**：

​       -d 指定刷新时间间隔

​      -p 指定监控PID   

**常用场景**：

​      查看系统运行情况：

```shell
top
```



## 命令：tail

**作用**：查看文件末尾，默认十行

**常用参数**：

​	-f 监控日志文件的显示

**常用场景**：

​      监控日志：

```shell
tail -f console.log
```



## 命令：find

**作用**：查找文件

**常用参数**：

​       -name 依据文件名

**常用场景**：

​      查找当前文件夹下的文件：

```shell
find . -name "name"
```



## 命令：vi/vim

**作用**：新建&修改文件

**三种模式**：

 + 命令模式  —> 按下`i`切换到输入模式
 + 输入模式 —> ESC 退出输入模式，切换到命令模式
 + 底线命令模式 —> 按下：进入底线命令模式

**常用操作**：

|     命令     |             说明             |
| :----------: | :--------------------------: |
|      :q      |            离开vi            |
|     :q!      |       强制离开，不存储       |
|      :w      |     保存编辑的数据到文档     |
|     :wq!     |        强制保存并退出        |
|    /word     |    搜索名称为word的字符串    |
|      dd      |       删除游标所在的行       |
|      yy      |       复制游标所在的行       |
|      p       | 将复制的数据在光标下一行贴上 |
| :s/old/new/  |   替换当前行第一个old为new   |
| :s/old/new/g |    替换当前行所有old为new    |
| :%s/old/new/ |  替换每一行的第一个old为new  |



## 命令：scp

**作用**：远程跨机拷贝文件

**常用参数**：

​	-r 递归复制整个目录

**常用场景**：

​      拷贝本地文件到远程机器：

```shell
scp -r /home/work/a.txt work@10.0.0.1:/home/work/a.txt
```



## 命令：rz/sz

**作用**：上传本地文件到服务器/发送选定文件到本地机器

**常用工具**：

​      SecureCRT  /   iTerm2



## 命令：wget

**作用**：下载单个文件

```shell
#下载redis源码包
wget http://download.redis.io/releases/redis-5.0.3.tar.gz 
```



## 命令：df

**作用**：查看硬盘空间

```shell
df -h
```



## 命令：crontab

**作用**：定时任务命令

```shell
crontab -e 

#命令格式，每天12点执行脚本
0    12   *   *   *    /home/work/*.sh
#分  时   日   月  周  |《=====脚本========》|
```



## 命令：alias

**作用**：创建临时别名，可以方便输入避免路径切换

```shell
alias mysql=/usr/local/mysql/bin/mysql 
```



## 命令：df/du

**作用**：查看磁盘的使用情况

```shell
//查看系统中文件的使用情况
df -h
//查看当前目录下各个文件及目录占用空间大小
du -sh *
//使用指定目录的层数查看文件夹的占用空间的大小
du -h --max-depth=1 /home
```



## 命令：lsof

**作用**：列出当前系统打开文件的工具

```shell
lsof -i 用以显示符合条件的进程情况
//查看当前端口的占用
lsof -i:8080
```



## 命令：sed

**作用**：文本处理

```shell
//想替换大文件中的字符串
sed -i "s/tf_user/tf_user_index/g" access.log 
```

