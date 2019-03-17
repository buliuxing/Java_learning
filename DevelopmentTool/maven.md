# 第2节：Maven



+ ### maven 下载

  下载地址：http://maven.apache.org/download.cgi 

+ ###配置settings.xml文件

+ ### 配置环境变量

  1. 命令 vim ~/.bash_profile （编辑环境变量配置文件）

  2. 配置export MAVEN_HOME=/Users/.../apache-maven-3.5.0 

     ​       export PATH=$PATH:$MAVEN_HOME/bin 

  3. 输入 source .bash_profile生效

  4. 输入 mvn -v查看安装

+ ###生成一个新的project

  ```shell
  mvn archetype:generate -DgroupId=org.goodskill -DartifactId=goodskill -DarchetypeArtifactId=maven-archetype-webapp -DarchetypeCatalog=internal
  
  #参数 -DarchetypeCatalog=internal 让它不要从远程服务器上取catalog
  ```

  



