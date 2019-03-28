# 第2节：Maven



### 简介

Maven 是项目构建工具，通过POM（project object model）对项目进行构建、打包和文档化操作，解决项目需要类库的依赖管理。Maven 的核心是pom.xml，通过XML方式描述项目模型：

|   groupId    |     表示项目所属的组，通常是公司或组织的名称     |
| :----------: | :----------------------------------------------: |
|  artifactId  |                  项目唯一的标识                  |
|  packaging   | 项目类型，常用jar和war两种，Spring Boot默认为jar |
|   version    |                   项目的版本号                   |
| dependencies |        声明项目的依赖，包含多个dependency        |
|  dependency  |     包含在dependencies中，声明项目的具体依赖     |



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
  mvn archetype:generate \
  	-DgroupId=org.goodskill \
      -DartifactId=goodskill \
      -DarchetypeArtifactId=maven-archetype-webapp \
      -DarchetypeCatalog=internal
  
  #参数 -DarchetypeCatalog=internal 让它不要从远程服务器上取catalog
  ```

+ ### 常用命令

  | mvn compile |    编译Maven工程     |
  | :---------: | :------------------: |
  | mvn package |    编译并打包工程    |
  | mvn install | 打包并安装到本地仓库 |
  | mvn deploy  | 同install（不常用）  |
  |  mvn clean  |    删除target目录    |

  





