[TOC]

## sql

### DDL

<img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240715214808432.png" alt="image-20240715214808432" style="zoom:80%;" />

### DML

![image-20240715223053301](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240715223053301.png)

### DQL

![image-20240716101834300](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716101834300.png)

![image-20240716101908683](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716101908683.png)

![image-20240716101931806](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716101931806.png)

注意： like **'_'**  要加‘’号

![image-20240716102041087](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716102041087.png)

注意：作用于表中的某一列，null值不参与运算

![image-20240716101101975](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716101101975.png)

![image-20240716101711349](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716101711349.png)

例子：

<img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716101510054.png" alt="image-20240716101510054" style="zoom:80%;" />



注意： group by **分组字段名**

![image-20240716102323115](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716102323115.png)

![image-20240716102836480](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716102836480.png)

![image-20240716104203461](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716104203461.png)

### DCL

* 用户管理

  ![image-20240716105321188](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716105321188.png)

  <img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716105344958.png" alt="image-20240716105344958" style="zoom:70%;" />

  

* 用户权限管理

![image-20240716105942973](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716105942973.png)

### 字符串函数

![image-20240716111734771](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716111734771.png)

CHAR_LENGTH(content)  功能：返回字符串长度

注意：sql中字符串的索引从1开始

![image-20240716112038616](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716112038616.png)

### 数值函数

![image-20240716112857619](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716112857619.png)

![image-20240716112841170](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716112841170.png)

### 日期函数

![image-20240716145751859](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716145751859.png)

![image-20240716145815695](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716145815695.png)

![image-20240716145840460](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716145840460.png)

### 流程函数

![image-20240716150909470](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716150909470.png)

注意 第二个应该是如果value1不是null。

![image-20240716151116724](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716151116724.png)

![image-20240716151130392](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716151130392.png)

![image-20240716151732268](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716151732268.png)

### 约束

* 约束是作用在字段上的规则

<img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716152116947.png" alt="image-20240716152116947" style="zoom:80%;" />

![image-20240716153140743](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716153140743.png)

![image-20240716154153973](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716154153973.png)

![image-20240716154615644](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716154615644.png)

### 多表查询

* 两个表的关系

  

![image-20240716161140344](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716161140344.png)

关联一对一的两张表，与关联一对多两张表的方式一样，都是在1的那个表上添加另一个表的主键作为外键，不同的是1对1要求外键唯一。

![image-20240716161358748](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716161358748.png)

![image-20240716161415166](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716161415166.png)

* 多表查询时，使用的是笛卡尔积（比如一张表4行记录，一张表5行记录，多表查询会查出20行记录），需要通过where消除无用的笛卡尔积。

* 多表查询分类：

  ![image-20240716162436047](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716162436047.png)

* **内连接**

![image-20240716163604314](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716163604314.png)

注意：隐式内连接和显式内连接查询的结果相同，只是写法不同。

注意：内连接查询的是两张表交集的部分。

* **外连接**

![image-20240716165700767](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716165700767.png)

* **自连接**

  ![image-20240716171203639](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716171203639.png)

* **联合查询**

  ![image-20240716172212628](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716172212628.png)

* **子查询**

  ![image-20240716172457681](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716172457681.png)

  ​	

  * **标量子查询**

    ![image-20240716173014895](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716173014895.png)

  * **列子查询**

    ![image-20240716173135268](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716173135268.png)

    any与some一样

    ![image-20240716173606616](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716173606616.png)

  * **行子查询**

    ![image-20240716195718244](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716195718244.png)

  * **表子查询**

    ![image-20240716200529188](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716200529188.png)

    ![image-20240716200805106](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240716200805106.png)

    

    

### 事务

* 事务简介

![image-20240717095412898](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717095412898.png)

注意：默认mysql的事务是自动提交的，也就是说，当执行一条DML语句，mysql会立即隐式的提交事务。

* 事务操作 两种方式

  * 自动提交设置为0

    ![image-20240717100954425](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717100954425.png)

    

  * 开始事务

    ![image-20240717100822769](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717100822769.png)

    

* 事务的四大特性 面试题

  * 原子性
  * 一致性
  * 隔离性
  * 持久性

* 并发事务引发的问题：多个事务并发执行时遇到的问题 

  ![image-20240717101932684](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717101932684.png)

  幻读是发生在解决了不可重复读问题情况下发生的情况。

  这三个问题是指出现在一个事务当中。

* 事务隔离级别：用来解决并发事务引发的问题。

  ![image-20240717104626995](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717104626995.png)

  ‘x’:表示没有脏读，没有不可重复读等。。。。

  session：会话级别，指对当前客户端有效。

  有幻读这个问题是表明：虽然数据库解决了事务中的不可重复读的问题，但是数据库已经知道了数据已经改变，只是没有告诉事务，保证事务可重复读。但是当事务操作自己以为可以操作的数据时（事务不知道数据改变了），数据库会报错。（数据库知道已经改变了）。这样再在下一次事务中，能够发现上次事务为什么报错。



​		serializable：实现的方式是并发几乎改成串行了，只允许一个事务在操作，该事务提交了，下个事务的操作才能进行。

## 进阶篇

### 存储引擎

#### Mysql体系结构

<img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717111435769.png" alt="image-20240717111435769" style="zoom:80%;" />

<img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717111508728.png" alt="image-20240717111508728" style="zoom:80%;" />



#### 存储引擎简介

* 存储引擎就是存储数据，建立索引，更新/查询数据等技术的实现方式。

* 存储引擎是**基于表的**，而不是基于库的，所以存储引擎也可被称为表类型。

* 指定存储引擎

* 查看数据库提供的存储引擎

  <img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717112442957.png" alt="image-20240717112442957" style="zoom:80%;" />

  

#### 存储引擎特点

* InnoDB  

  <img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717113117071.png" alt="image-20240717113117071" style="zoom:80%;" />

  mysql旧版本表结构存在frm为后缀名的文件中，现在存在sdi后缀名的文件中，并集成到ibd文件中。

  参数innodb_file_per_table 表示是否为每一个表建立一个对应的ibd文件，现在参数值为true，表示为每一个表建立一个ibd文件。

  <img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717113650106.png" alt="image-20240717113650106" style="zoom:80%;" />

  

* MyISAM

  <img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717113930811.png" alt="image-20240717113930811" style="zoom:80%;" />

* Memory

  <img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717114031918.png" alt="image-20240717114031918" style="zoom:80%;" />

  ![image-20240717114120616](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717114120616.png)

  

#### 存储引擎选择

![image-20240717114430553](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240717114430553.png)

myISAM 被MongoDB替代  

Memory被redis替代

### 索引 重要

#### 索引概述

![image-20240718150828167](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718150828167.png)

无索引情况：全表扫描

有索引情况：如对age字段建立索引，假设建立二叉排序树，树的每个节点指向一条记录。

![image-20240718153641247](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718153641247.png)



#### 索引结构

![image-20240718153859069](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718153859069.png)

![image-20240718153937464](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718153937464.png)

![image-20240718154001937](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718154001937.png)

* **B-tree的构建，给一串数据，怎么根据他们的大小构建出B-tree？**五阶B-tree是指，4个key，5个指针。

  ![image-20240718170421663](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718170421663.png)

  

* **B+tree的构建，给一串数据，怎么根据他们的大小构建出B+tree？**

  ![image-20240718171909316](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718171909316.png)

  

* mysql索引数据结构对经典B+tree进行了优化

  ![image-20240718172151563](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718172151563.png)

  此图中的页与innoDB逻辑存储结构中的页相同。

* hash索引数据结构

  ![image-20240718191144689](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718191144689.png)

  ![image-20240718191420435](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718191420435.png)

  #### 为什么innoDB存储选择使用B+tree索引结构？

  ![image-20240718192848565](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718192848565.png)

  

#### 索引分类

![image-20240718193113581](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718193113581.png)

* InnoDB存储引擎中，将索引根据存储形式分为以下两种：

* ![image-20240718193424240](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718193424240.png)

  聚集索引：叶子节点数据部分保存了行数据。<u>节点键值保存的是字段，并且按照这个字段顺序建立树。</u>（这话不确定对不对嗷）

  二级索引：叶子节点数据部分保存的是主键。<u>节点键值保存的是字段，并且按照这个字段顺序建立树。</u>（这话不确定对不对嗷）

* 根据索引查找知道数据的过程

  ![image-20240718194456875](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718194456875.png)

  sql语句为根据name字段查找，所以先用二级索引的B+树查到该name记录的主键，然后再用聚集索引查到该主键的记录，这种先用二级索引再用聚集索引的查询方法称为回表查询。

  ![image-20240718195754930](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718195754930.png)

  一页16k

#### 索引语法

* 创建索引

  ![image-20240718200050778](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718200050778.png)

  不加UNIQUE或者FULLTEXT为常规索引

* 查看索引

  ![image-20240718200100271](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718200100271.png)

* 删除索引

  ![image-20240718200109438](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240718200109438.png)

* 

#### SQL性能分析

* SQL执行频率（性能分析工具语句）-----------》得知该数据库哪类语句执行频率比较高

  ![image-20240719105347003](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240719105347003.png)

  session是指当前会话的访问频次，即此客户端的访问频次

  global是指全局的访问频次

  ![image-20240719105532422](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240719105532422.png)

* 慢查询日志--------------------》确定哪个查询语句比较慢

  ![image-20240719110332718](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240719110332718.png)

  ![image-20240719110355964](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240719110355964.png)![image-20240719112958630](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240719112958630.png)

  

  

  使用`show variable like 'slow_query_log';`查看慢查询日志有没有开启。

  开启慢查询日志需要修改配置文件。

* 慢查询日志只能看到超过某个时间的sql语句，如果想看到所有sql语句的查询时间以及每个sql语句时间耗费在哪里了，使用profile。

  ![image-20240719112432025](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240719112432025.png)

  ![image-20240719112454362](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240719112454362.png)

* explain 执行性能===============》一个sql语句是如何执行的

  ![image-20240719114247644](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240719114247644.png)

  ![image-20240719115937969](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240719115937969.png)

  id，type，possiable_key,key,Key_len是重点。

  type：null不查表时会出现；system查系统表时出现；const使用主键和唯一索引时会出现；ref使用常规索引时出现；all未使用索引扫描全表时出现；index虽然使用了索引，但是也扫描了索引的所有节点时会出现。

  <img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240722120754668.png" alt="image-20240722120754668" style="zoom:50%;" />

  

  ![image-20240719120351488](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240719120351488.png)

  

#### 索引使用

where后怎么写？怎么规避索引失效？

* 最左前缀法则

  ![image-20240722101158169](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240722101158169.png)

  

* 范围查询

  在使用where and的查询时，出现范围查询（>,<），范围查询右侧的列索引失效。

* 索引列运算

  不要在索引列上进行运算操作，索引将会失效

  ![image-20240722102027387](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240722102027387.png)

* 字符串不加引号

  字符串类型字段使用时，不加引号，索引将会失效。

  ![image-20240722102303787](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240722102303787.png)

  



* 模糊查询

  ![image-20240722102546959](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240722102546959.png)

* or连接的条件

  ![image-20240722103045418](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240722103045418.png)

* 数据分布影响

  如果mysql评估使用索引比全表更慢，则不使用索引。如果全表中的数据大多数都能查到，这是不使用索引，否则会走索引。

* sql提示

  ![image-20240722104148498](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240722104148498.png)

  use：建议使用指定索引

  ignore：忽略指定索引

  force：强制使用指定索引

select后字段怎么写？写什么？

* 覆盖索引

  ![image-20240722110420218](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240722110420218.png)

  

  

  

* 前缀索引

  ![image-20240722111416120](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240722111416120.png)

* 单列索引和联合索引

  ![image-20240722113636385](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240722113636385.png)

  尽量使用联合索引。

  联合索引树的构造： key值为联合的字段，value是id，key排序的方法是先排左侧的字段，左侧字段相同，按右侧的排

#### 索引设计原则

![image-20240722114148883](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240722114148883.png)

一百万数据量以上最好要建立索引

### sql优化



#### 插入数据

* 批量插入

  ![image-20240723095724636](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723095724636.png)

  用一条语句插入多行，建议一次性插入记录数不要超过500-1000，再多的话，分多个插入语句。

* 手动提交事务

  ![image-20240723095838476](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723095838476.png)

* 主键顺序插入

  

  ![image-20240723095903858](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723095903858.png)

* 大批量插入数据 上百万数量级

  <img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723100716863.png" alt="image-20240723100716863" style="zoom:67%;" />

  

#### 主键优化

![image-20240723102015310](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723102015310.png)

从叶子结点上看，叶子节点中的主键是从左至右按顺序的，因此说表数据是根据主机顺序组织存放的。

从分支节点上看，记录是可以按B+tree/主键索引查找的。

<img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723102248552.png" alt="image-20240723102248552" style="zoom:80%;" />

设计原则重点\*\*\*\*\*, 是实用技巧

#### order by优化

![image-20240723102815524](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723102815524.png)

先按照年龄升序排序，当年龄相同时，按照phone升序排序。

#### 

![image-20240723104140001](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723104140001.png)

优化目标尽量使用using index。using index和using filesort是extra字段内容。

如何优化到using index？

1. 对需要排序的字段创建索引，如果是多个字段需创建联合索引，注意，要遵守最左法则；

2. 若创建age，phone的联合索引，默认age ase，phone ase。

   情况1. ![image-20240723104650166](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723104650166.png)

   情况2.![image-20240723104712250](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723104712250.png)

   情况3.（不遵守最左法则）![image-20240723104737168](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723104737168.png)

   情况4.![image-20240723104818729](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723104818729.png)

   情况4解决方式.![image-20240723104905604](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723104905604.png)

   ![image-20240723104927966](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723104927966.png)

3. 使用覆盖索引。覆盖索引就是select后的字段，在索引中均出现；

   ![image-20240723105128285](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723105128285.png)

   不使用覆盖索引，直接全表扫描了

4. ![image-20240723105207960](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723105207960.png)

#### group by优化

设计原则：

![image-20240723105857201](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723105857201.png)



#### limit优化

![image-20240723111102582](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723111102582.png)



#### count优化

![image-20240723111506883](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723111506883.png)

![image-20240723112358704](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723112358704.png)

#### update优化

 ![image-20240723113202316](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723113202316.png)

innoDB三个特点 事务 外键  行锁

### 视图/存储过程/触发器

#### 视图

* 视图的定义

  ![image-20240723115418957](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723115418957.png)

  

* 视图相关语法

  ![image-20240723115131158](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723115131158.png)

  ![image-20240723115316987](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723115316987.png)

* 检查选项

  ![image-20240723115932737](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723115932737.png)

  cascade n.级联

  ![image-20240723120131709](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723120131709.png)

  **对视图进行增删改操作，实际上操作的是生成视图的那个基表。**为保证对视图进行的增删改操作，在视图中可以体现出来，使用检查选项，来检查增删改操作是否符合视图的定义。

  ![image-20240723120935619](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723120935619.png)

  ![image-20240723121307908](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723121307908.png)

  

  ![image-20240723122041087](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240723122041087.png)

  **local也会递归的查询当前视图所依赖的视图或者表 ，但是不同于cascade将当前视图的检测选项加到上级视图或者表，使用local检查选项，发现上级没有使用检查选项，就不会检查了。**

* 视图更新：![image-20240724213754312](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240724213754312.png)

* 视图的作用：![image-20240724214028645](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240724214028645.png)

  

#### 存储过程

* 定义

  ![image-20240724215028113](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240724215028113.png)

* 特点：

  <img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240724215057397.png" alt="image-20240724215057397" style="zoom:50%;" />

* 基本语法：

  <img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240724215554694.png" alt="image-20240724215554694" style="zoom:67%;" />

  <img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240724215849266.png" alt="image-20240724215849266" style="zoom: 67%;" />

  ![image-20240724220001659](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240724220001659.png)

  ![image-20240724220052393](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240724220052393.png)

  

#### 存储函数

#### 触发器

### 锁

### innoDB引擎