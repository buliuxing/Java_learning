# 第8节：序列化工具



###简介

**序列化**：将结构数据或对象转换成能够被存储和传输的格式，同时保证这个序列化结果之后能够被重建回原来的结构数据或对象。

### Jackson



###Gson



### Fastjson



### ProtoBuf

ProtoBuf是结构数据序列化方法，可简单类比XML，具有特点：

+ 语言无关、平台无关
+ 高效
+ 扩展性、兼容性好

使用ProtoBuf前需要在pom文件中增加依赖

```java
第一步：创建.proto文件，定义数据结构
//声明版本号
synyax = "protoxx";
message xxx{
    //字段规则：required -> 字段只能也必须出现1次
    //字段规则：optional -> 字段出现0次或多次
    //字段规则：repeated -> 字段可能出现任意多次包括0
    //类型：int32、int64、sint32、sint64、string、32-bit ....
    //字段编号：0～536870911 （除去 19000 到 19999 之间的数字）
    字段规则 类型 名称 = 字段编号；
}

第二步：protoc编译.proto文件生成读写接口
// $SRC_DIR: .proto 所在的源目录
// --java_out: 生成 java 代码
// $DST_DIR: 生成代码的目标目录
// xxx.proto: 要针对哪个 proto 文件生成接口代码

protoc -I=$SRC_DIR --java_out=$DST_DIR $SRC_DIR/xxx.proto

第三步：调用接口实现序列化、反序列化

```



### Protostuff

protostuff不需要依赖.proto文件，可以直接对POJO进行序列化和反序列化。

protostuff的使用

```java
第一步：pom文件中引入依赖
    <dependency>
      <groupId>com.dyuproject.protostuff</groupId>
      <artifactId>protostuff-runtime</artifactId>
      <version>1.0.8</version>
    </dependency>
    <dependency>
      <groupId>com.dyuproject.protostuff</groupId>
      <artifactId>protostuff-core</artifactId>
      <version>1.0.8</version>
    </dependency>
    
 第二步：简单序列化
 //创建第三方工具类
 private RuntimeSchema<Class> schema = RuntimeSchema.createFrom(xxxx.class);
//序列化，并添加缓冲区
byte[] bytes = ProtobufIOUtil.toByteArray(good, schema,
                        LinkedBuffer.allocate(LinkedBuffer.DEFAULT_BUFFER_SIZE));
//反序列化
 Class testClass = schema.newMessage();
                    ProtobufIOUtil.mergeFrom(bytes, testClass, schema);


```







