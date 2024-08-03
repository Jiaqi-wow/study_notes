# 业务

![image-20240731145847100](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240731145847100.png)

本项目（苍穹外卖）是专门为餐饮企业（餐厅、饭店）定制的一款软件产品，包括 **系统管理后台** 和 **小程序端应用** 两部分。其中系统管理后台主要提供给餐饮企业内部员工使用，**可以对餐厅的分类、菜品、套餐、订单、员工等进行管理维护，对餐厅的各类数据进行统计，同时也可进行来单语音播报功能。**小程序端主要提供给消费者使用，可以在线浏览菜品、添加购物车、下单、支付、催单等。



## 管理端业务功能模块 

![image-20240731150341006](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240731150341006.png)

具体介绍：

| 模块          | 描述                                                         |
| ------------- | ------------------------------------------------------------ |
| **登录/退出** | 内部员工必须登录后,才可以访问系统管理后台                    |
| 员工管理      | 管理员可以在系统后台对员工信息进行管理，包含查询、新增、编辑、禁用等功能 |
| 分类管理      | 主要对当前餐厅经营的 **菜品分类** 或 **套餐分类** 进行管理维护， 包含查询、新增、修改、删除等功能 |
| 菜品管理      | 主要维护各个分类下的菜品信息，包含查询、新增、修改、删除、启售、停售等功能 |
| 套餐管理      | 主要维护当前餐厅中的套餐信息，包含查询、新增、修改、删除、启售、停售等功能 |
| **订单管理**  | **主要维护用户在移动端下的订单信息，包含查询、取消、派送、完成，以及订单报表下载等功能** |
| **数据统计**  | 主要完成对餐厅的各类数据统计，如营业额、用户数量、订单等     |

技术选型：

![image-20240731150933347](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240731150933347.png)

**1). 用户层**

本项目中在构建系统管理后台的前端页面，我们会用到H5、Vue.js、ElementUI、apache echarts(展示图表)等技术。而在构建移动端应用时，我们会使用到微信小程序。



**2). 网关层**

Nginx是一个服务器，主要用来作为Http服务器，部署静态资源，访问性能高。在Nginx中还有两个比较重要的作用： 反向代理和负载均衡， 在进行项目部署时，要实现Tomcat的负载均衡，就可以通过Nginx来实现。



**3). 应用层**

SpringBoot： 快速构建Spring项目, 采用 "约定优于配置" 的思想, 简化Spring项目的配置开发。

SpringMVC：SpringMVC是spring框架的一个模块，springmvc和spring无需通过中间整合层进行整合，可以无缝集成。

Spring Task:  由Spring提供的定时任务框架。

httpclient:  主要实现了对http请求的发送。

Spring Cache:  由Spring提供的数据缓存框架

JWT:  用于对应用程序上的用户进行身份验证的标记。

阿里云OSS:  对象存储服务，在项目中主要存储文件，如图片等。

Swagger： 可以自动的帮助开发人员生成接口文档，并对接口进行测试。

POI:  封装了对Excel表格的常用操作。

WebSocket: 一种通信网络协议，使客户端和服务器之间的数据交换更加简单，用于项目的来单、催单功能实现。



**4). 数据层**

MySQL： 关系型数据库, 本项目的核心业务数据都会采用MySQL进行存储。

Redis： 基于key-value格式存储的内存数据库, 访问速度快, 经常使用它做缓存。

Mybatis： 本项目持久层将会使用Mybatis开发。

pagehelper:  分页插件。

spring data redis:  简化java代码操作Redis的API。



**5). 工具**

git: 版本控制工具, 在团队协作中, 使用该工具对项目中的代码进行管理。

maven: 项目构建工具。

junit：单元测试工具，开发人员功能实现完毕后，需要通过junit对功能进行单元测试。

postman:  接口测工具，模拟用户发起的各类HTTP请求，获取对应的响应结果。

# 环境搭建

![image-20240731152513334](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240731152513334.png)

开发环境搭建主要包含**前端环境**和**后端环境**两部分。作为服务端开发工程师， 我们课程学习的重心应该放在后端的业务代码上， 前端的页面我们只需要导入资料中的nginx， 前端页面的代码我们只需要能看懂即可。



##  前端环境搭建

## 后端环境噶搭建

## 浏览器到后端请求流程

![image-20240731160735990](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240731160735990.png)

**nginx 反向代理的好处：**

- 提高访问速度

  因为nginx本身可以进行缓存，如果访问的同一接口，并且做了数据缓存，nginx就直接可把数据返回，不需要真正地访问服务端，从而提高访问速度。

- 进行负载均衡

  所谓负载均衡,就是把大量的请求按照我们指定的方式均衡的分配给集群中的每台服务器。

- 保证后端服务安全

  因为一般后台服务地址不会暴露，所以使用浏览器不能直接访问，可以把nginx作为请求访问的入口，请求到达nginx后转发到具体的服务中，从而保证后端服务的安全。

  ![image-20240731160851515](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240731160851515.png)

  **nginx 反向代理的配置方式：**

  ```nginx
  server{
      listen 80;
      server_name localhost;
      
      location /api/{
          proxy_pass http://localhost:8080/admin/; #反向代理
      }
  }
  ```

  **proxy_pass：**该指令是用来设置代理服务器的地址，可以是主机名称，IP地址加端口号等形式。

  如上代码的含义是：监听80端口号， 然后当我们访问 http://localhost:80/api/../..这样的接口的时候，它会通过 location /api/ {} 这样的反向代理到 http://localhost:8080/admin/上来。

  

  接下来，进到nginx-1.20.2\conf，打开nginx配置

  ```nginx
  # 反向代理,处理管理端发送的请求
  location /api/ {
  	proxy_pass   http://localhost:8080/admin/;
      #proxy_pass   http://webservers/admin/;
  }
  ```

  当在访问http://localhost/api/employee/login，nginx接收到请求后转到http://localhost:8080/admin/，故最终的请求地址为http://localhost:8080/admin/employee/login，和后台服务的访问地址一致。

  **2). nginx 负载均衡**

  当如果服务以集群的方式进行部署时，那nginx在转发请求到服务器时就需要做相应的负载均衡。其实，负载均衡从本质上来说也是基于反向代理来实现的，最终都是转发请求。

  **nginx 负载均衡策略：**

  | **名称**   | **说明**                                               |
  | ---------- | ------------------------------------------------------ |
  | 轮询       | 默认方式                                               |
  | weight     | 权重方式，默认为1，权重越高，被分配的客户端请求就越多  |
  | ip_hash    | 依据ip分配方式，这样每个访客可以固定访问一个后端服务   |
  | least_conn | 依据最少连接方式，把请求优先分配给连接数少的后端服务   |
  | url_hash   | 依据url分配方式，这样相同的url会被分配到同一个后端服务 |
  | fair       | 依据响应时间方式，响应时间短的服务将会被优先分配       |

  具体配置方式：

  **轮询：**

  ```nginx
  upstream webservers{
      server 192.168.100.128:8080;
      server 192.168.100.129:8080;
  }
  ```

  **weight:**

  ```nginx
  upstream webservers{
      server 192.168.100.128:8080 weight=90;
      server 192.168.100.129:8080 weight=10;
  }
  ```

  **ip_hash:**

  ```nginx
  upstream webservers{
      ip_hash;
      server 192.168.100.128:8080;
      server 192.168.100.129:8080;
  }
  ```

  **least_conn:**

  ```nginx
  upstream webservers{
      least_conn;
      server 192.168.100.128:8080;
      server 192.168.100.129:8080;
  }
  ```

  **url_hash:**

  ```nginx
  upstream webservers{
      hash &request_uri;
      server 192.168.100.128:8080;
      server 192.168.100.129:8080;
  }
  ```

  **fair:**

  ```nginx
  upstream webservers{
      server 192.168.100.128:8080;
      server 192.168.100.129:8080;
      fair;
  }
  ```

  



# 远程git服务器管理

我的流程是：

1. 在github上建库；
2. 在本地用gitbash，进入想要放库的目录，输入git clone url 将远程库复制下来；
3. 将需要管理的文件放到远程复制下来的库中
4. 或许 git add 。。。 git commit 。。。git push。。。

# 完善功能

