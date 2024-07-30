# Spring学习内容

![image-20240726153403764](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726153403764.png)

![image-20240726153435482](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726153435482.png)

IOC： service对象和Dao对象交给IOC容器管理。

DI：将Dao对象注入到Service对象中。

使用xml文件告诉springIOC中应该管理哪些对象。

使用接口获取容器，然后从容器中拿到对象来执行方法。





知识点索引

##  bean



1. bean标签，其中的id，name属性，scope属性

2. spring实例化bean的三种方法1.通过反射使用无参的构造器实例化bean2.通过 静态工厂（一个工厂类，里面有一个静态方法，该方法new对象并返回对象，则调用该工厂类的静态方法就可以得到对象）实例化，了解为主。3.通过实例工厂实例化

   <img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726182840593.png" alt="image-20240726182840593" style="zoom:50%;" />

   

3. bean生命周期

   ![image-20240726183932907](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726183932907.png)

   

## DI



1. 使用setter注入简单数据类型与引用数据类型

   ![image-20240726185149760](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726185149760.png)

   这里面的name取值首字母变大写，前面再加上set，要与类中的setter方法名一致。

2. 使用构造器注入简单数据类型与引用数据类型

   <img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726185820029.png" alt="image-20240726185820029" style="zoom:50%;" />

   name是按照构造器形参的名字，index是按照索引从0开始，type是按照形参的数据类型，选一个就行了吧

3. 自动配置 **仅适用于引用数据类型的注入**

   语法：![image-20240726190553228](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726190553228.png)

   注入那个对象呢？

   byName按名字注入。按哪个名字呢？找容器中管理的**对象name或者id值**与**setter方法名去掉set首字母小写**。找不到则注入Null

   byType注入，必须保障容器中相同类型的bean**唯一**，推荐使用，**不唯一报错**，没有注null吧

   **自动装配优先级低于setter注入与构造器注入，同时出现时自动装配配置失效**

4. 集合注入

   注入数组

   注入list

   注入map

   注入set

   注入properties

   语法就是在<bean>和<property>/<constructor-arg>标签下套<array>/<list>/.....

   ![image-20240726191714660](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726191714660.png)

   ![image-20240726191721208](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726191721208.png)

   ![image-20240726191728696](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726191728696.png)

## IOC/DI配置管理第三方bean



1. 肯定是要在配置文件写明要管理哪个类的对象。

2. 然后进行注入操作。

3. **引入Druid jar后，可以使用连接池操作，想要连接数据库和操作数据库，还要引入mysql的驱动包（mysql-connector-java）。**

4. **加载Properties文件，**Properties文件的作用是将注入的基本数据类型数据，写到Properties文件中，易于维护。不和xml搅和在一起，看起来很舒服。

   1. 要把Properties文件加载进来，

      先开启context命名空间

      ![image-20240726194749096](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726194749096.png)

      在加载Properties文件

      ![image-20240726194825890](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726194825890.png)

      location 写文件地址     ![image-20240726194921009](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726194921009.png)

      ![image-20240726194937927](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726194937927.png)

      ![image-20240726195025775](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726195025775.png)

      

## 核心容器

1. 容器创建方式

   ![image-20240726195401987](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726195401987.png)

   ![image-20240726195849188](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726195849188.png)

   

## IOC/DI注解开发

1. 注解开发定义bean

   ![image-20240726201128770](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726201128770.png)

   

   ![image-20240726200647376](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726200647376.png)

   ![image-20240726200701114](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726200701114.png)

   ![image-20240726200731012](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726200731012.png)

   **名字这里只涉及到三个地方一个是给bean取名字，一个是选bean注入，一个是获取bean。**

2. 纯注解开发

   上一个方法还是有xml文件，纯注解开发把xml文件去掉，用一个类替代。

   ![image-20240726201503015](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726201503015.png)

   ![image-20240726201533161](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726201533161.png)

   

   ![image-20240726201557473](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726201557473.png)

   ![image-20240726201633230](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726201633230.png)

3. 注解开发bean作用范围与生命周期管理

   ![image-20240726202523488](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726202523488.png)

   初始化方法和销毁方法

   ![image-20240726202720522](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726202720522.png)

   ![image-20240726202854595](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726202854595.png)

   

   ![image-20240726202837073](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726202837073.png)

4. 注解开发依赖注入

   **@Autowired**

   写在成员变量上面，默认是按照类型注入，如果该类型有多个对象，则转为按名字注入，找和成员变量名字一样的对象，找不到则报错。

   **@Qualifier（“ ”）**

   必须和@Autowired搭配使用，按照名字注入。

   **@Value**

   用于基本类型和String的注入![image-20240726204148279](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726204148279.png)

   

   **@PropertySource**

   加载Properties文件，不支持通配符

   ![image-20240726204228487](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726204228487.png)

   ![image-20240726204244886](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726204244886.png)

   ![image-20240726204311408](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726204311408.png)

   之后![image-20240726204325121](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726204325121.png)

## 第三方bean怎么用注解开发管理

1. 第三方bean管理

   ![image-20240726210048057](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726210048057.png)

   注意：第三方bean写到spring的配置类里，不用加那个扫包的注解@ComponentScan，用spring配置类获取容器的时候就有这个bean了。

   

   把jdbc配置放到spring配置中不好，给他拿出来，拿出来后的问题是怎么把这个bean放到容器中。用@Import（{}）

   ![image-20240726210412948](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726210412948.png)![image-20240726210432534](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726210432534.png)

   

2. 第三方bean依赖注入

   * 注入简单数据类型

     

     ![image-20240726211122955](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726211122955.png)

   * 引用类型注入

     ![image-20240726211336302](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726211336302.png)

     

   

   spring的功能主要是管理bean和自动注入依赖，spring和第三方整合，就是将第三方的对象，交给spring来管理。

## AOP

实现需要定义切入点，声明切面，编写通知类与通知方法，在方法上声明切面，给通知类添加注解，给springConfig添加注解

1. 切入点表达式的格式

   格式

   通配符

   使用规则

2. AOP通知类型

   前置通知

   后置通知

   环绕通知！增强的业务方法有返回值的处理方式

3. AOP通知获取核心方法相关数据，如形参，返回值

## 事务

1. Spring事务的定义
2. 事务的管理
3. 事务属性



结合ssm目录下的那个笔记看 ，哪个全

# SpringMVC

SpringMVC与Servlet代码上的区别

![image-20240727183450552](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240727183450552.png)



## **@RequestBody** 与 **@RequestParam**   请求参数接收

## **@ResponseBody** 响应

![image-20240727220054580](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240727220054580.png)



**tomcat 与 jdk版本、servlet版本，jsp版本需对应**

![image-20240726160346040](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240726160346040.png)

**servlet版本与javaEE版本也有对应**

## ssm

1. spring整合mybatis，jdbc，事务，springmvc的配置类。
2. 业务模块开发，添加事务，返回数据格式统一
3. 两阶段测试
4. 异常处理
5. 拦截器

# idea

项目 

创建java项目

spring和mybatis 与 web没有关系 ，所以学习spring和mybatis ，创建java项目就可以

创建javaweb项目： 得配置tomcat

springmvc 得创建javaweb项目，因为他设计到了对请求的接收，处理与响应，想要数据的持久化就需要整合mybatis了。

创建SpringBoot项目：不需要配置tomcat了，因为在*springboot*的依赖中spring-boot-starter-web中已经内置了tomcat