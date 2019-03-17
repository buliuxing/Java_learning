# 第1节：MySQL



### MySQL的安装

+ 官网下载mac版的mysql，链接：https://dev.mysql.com/downloads/mysql/5.7.html#downloads

+ 点击安装，安装目录默认为/usr/local/mysql/bin；

+ 进入mac的偏好设置，启动mysql服务；

+ 配置环境变量

  ```shell
  打开配置文件 vim ~/.bash_profile
  添加 PATH=$PATH:/usr/local/mysql/bin
  生效配置文件 source ~/.bash_profile
  ```

### 常用命令

+ 更改root密码

  ```mysql
  mysqladmin -uroot -p旧密码 password 新密码
  ```

+ 查看端口号

  ```
  show global variables like 'port';
  ```

+ 修改列名

  ```
  alter table tb_name change old_name new_name column_definition;
  ```

  