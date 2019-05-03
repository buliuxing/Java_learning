# 第1节：Spring



## Spring简介

Spring作为Java最常用的框架，主要在于其理念包括IoC（Inversion of Control，控制反转）和AOP（Aspect Oriented Programming，面向切面编程）。

+ **IoC简介**

  > IoC是一个容器，用于管理Java Bean和它们之间的关系。Spring IoC通过描述创建，也就是说Spring是依靠描述来完成对象的创建和依赖关系的。这是一种被动的行为，而需要资源通过描述信息就可以得到，其中的控制权在Spring IoC容器中，根据描述找到使用者需要的资源，这就是控制反转的含义。

+ **AOP**

  > 对于影响多个OOP( 面向对象)的条件称为切面。管理在切面上的某些对象间的协作称为面向切面编程。Spring AOP常用于数据库事务的编程，并以异常作为消息，只要Spring接收到异常信息，他就将数据库事务进行回滚，从而保证数据的一致性。

+ 