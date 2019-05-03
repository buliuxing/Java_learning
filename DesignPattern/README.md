# 第七章：设计模式



### 动态代理模式

动态代理的意义在于生成一个占位来代理真实对象，从而控制真实对象的访问，其必须分为两个步骤：

+ 代理对象和真实对象建立代理关系；
+ 实现代理对象的代理逻辑方法；

常用的代理为JDK动态代理和CGLIB。其中，JDK实现代理必须使用接口，而

1、**JDK动态代理**

```java
//定义接口
public interface HelloWorld{
    public void sayHelloWorld();
}
//实现接口
public class HelloWorldImpl implements HelloWorld{
    @Override
    public void sayHelloWorld(){
        System.out.println("Hello world!");
    }
}
//动态代理绑定和代理逻辑实现
public class JdkProxyExample implements InvocationHandler{
    //真实对象
    private	Object target = null;
    //建立代理对象和真实对象的代理关系
    public Object bind(Object target){
        this.target = target;
        return Proxy.newProxyInstance(target.getClass().getClassLoader(), 
                                     target.getClass().getinterfaces(), this);
    }
    //代理方法逻辑
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable{
        System.out.println("进入代理逻辑方法");
        System.out.println("在调度真实对象之前的服务");
        Object obj = method.invoke(target,args);
        System.out.println("在调度真实对象之后的服务");
        return obj；
    }
}
```

