[TOC]

## 变量

### 基本变量数据类型

* Java中有八种基本类型：

  整型 （4种）

  字符型 （1种）

  浮点型 （2种）

  布尔型（1种）

* `float f = 54.321`会出现编译错误，因为54.321的默认类型是 double，其类型长度为64，超过了float的长度32
  在数字后面**加一个字母f**，直接把该数字声明成float类型。`float f2 = 54.321f`,这样就不会出错了。

### 字面量                    （给基本类型的变量赋值的方式叫做字面值）

* e2表示10的二次方，即100。1.234e2 = 1.234x100
* 整数字面值：当以l或者L结尾的时候，一个整数字面值是long类型，否则就是int类型。 建议使用**大写的L**而非小写的l，因为容易和1混淆。byte,short,int和long的值都可以通过int类型的字面值来创建。
* 十六进制：用0x开头。二进制：用0b开头。
* 浮点数字面值：当以f或者F结尾的时候，就表示一个float类型的浮点数，否则就是double类型（以d或者D结尾，写不写都可以）。
* 字符和字符串字面值：字符的字面值放在单引号中。**字符串**的字面值放在双引号中。
* \表示转义，比如需要表示制表符，回车换行，双引号等就需要用 \t \r \n \\" 的方式进行

### 数据类型转换

* 自动类型转换：![image-20240706160706977](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240706160706977.png)
* 强制转换：`b =(byte) i2;`
* **整型和整型进行运算的时候，如果两边的值都是小于或者等于int的，那么其结果就是int。**两个short相加也是int。相关知识点在操作符章节。

### 命名规则

* 变量命名只能使用**字母 数字 $ _**，变量第一个字符 不能使用数字。
* 在命名的时候，尽量使用完整的单词进行命名，比如name,moveSpeed，而不是使用缩写 n,m。
* 关键字列表：[变量系列教材 （五）- Java的命名规则 (how2j.cn)](https://how2j.cn/k/variable/variable-nameing/260.html#nowhere)

### 变量作用域

* 变量三分类：字段,属性,成员变量,Field 、 参数、局部变量.
* 成员变量作用域：作用域就是从其声明的位置开始的整个类。（不严谨吧，还得看变量的权限修饰符吧）
* 参数作用域：如果一个变量，是声明在一个方法上的，就叫做**参数**，参数的作用域即为该**方法内的所有代码**，其他方法不能访问该参数，类里面也不能访问该参数
* 局部变量作用域：声明在方法内的变量，叫做局部变量，其作用域在声明开始的位置，到其所处于的**块结束位置**
* 当访问的变量被多个作用域影响的时候，**按照就近原则取**

### final修饰符

*  当一个变量被final修饰的时候，该变量**只有一次赋值的机会**
*  final 除了修饰变量，还可以修饰**类**，修饰**方法**
*  如果final修饰的是**参数**，**不能在方法里给这个参数赋值**

以;结尾的一段代码，即为一个表达式

从**{** 开始 到对应的**}** 结束，即一个块

### 深拷贝 浅拷贝 引用拷贝

深拷贝 是建立一个对象的完全的副本

浅拷贝 是建立一个对象的副本，但是对象属性是引用数据类型的话，还是引用的之前对象的对象属性

引用拷贝

## 操作符

### Scanner

* Scanner类的使用

```java
package org.example.java.how2j;

import java.util.Scanner; //使用Scanner类,导入这个类，才能够正常使用

public class ScannerTest {

    public static void main(String[] args) {
        // 使用Scanner读取整数
        Scanner s = new Scanner(System.in);
        int a = s.nextInt();
        System.out.println("第一个整数："+a);
        int b = s.nextInt();
        System.out.println("第二个整数："+b);
        //使用Scanner读取浮点数
        float c = s.nextFloat();
        System.out.println("读取的浮点数的值是："+c);
        //使用Scanner读取字符串
        String d = s.nextLine();
        System.out.println("读取的字符串是："+d);
        //这种情况下读出来的是回车换行:"\r\n",
        // 因为nextInt、nextFloat仅仅读取数字信息，而不会读取回车换行"\r\n".

        //再读取了"\r\n"，接下来，才开始读取真正的字符串
        String  f= s.nextLine();
        System.out.println("读取的字符串是："+f);
        //所以，如果在业务上需要读取了整数后，接着读取字符串，
        // 那么就应该连续执行两次nextLine()，
        // 第一次是取走回车换行，第二次才是读取真正的字符串
    }
}

```

### 算数操作符

* ```java
  + - * / % ++ -- 
  // 单目运算符优先级      高于     * / %，
  // * / %              高于     强制类型转换
  // 强制类型转换         高于       + - 
  // + -                高于      移位运算符 >>、<<
  // 移位运算符           高于      关系运算符 > >= ...
  // 关系运算符 > >= ...  高于      等价运算符 ==  !=
  // 等价运算符 ==  !=   高于       &按位与      高于    ^    高于   |按位或    高于     &&  高于   ||
  // 赋值运算符 优先级最低 =、+=、-=...
  ```

  **如果任何运算单元的数据类型都不超过int,那么运算结果就按照int来计算**

* `i++;` **先取值，再运算**
  `++i;` **先运算，再取值**

  ![image-20240706165200101](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240706165200101.png)

* ```java
  int i = 1;
  int j = ++i + i++ + ++i + ++i + i++;
  System.out.println(j);
  //分析：因为++ 的优先级比 + 高，
  //所以int j = ++i + i++ + ++i + ++i + i++; ===》int j = (++i) + (i++) + (++i) + (++i) + (i++);
  //                                              i 值      2       3       4       5       6
  //                                    (++i)或(i++) 值   	 2      2        4      5        5  
  ```

  

### 逻辑操作符 运算时的两边单元是布尔值

* 长路与&、短路与&&：

  共同点：无论长路与还是短路与两边的运算单元都是布尔值都为真时，才为真任意为假，就为假

  区别：长路与两侧，都会被运算短路与 只要第一个是false，第二个就不进行运算了

```java
public class ScannerTest {

    public static void main(String[] args) {
        int aa = 2;
        System.out.println( aa== 1 & aa++ ==2  ); //aa++ ==2 这个是true
        System.out.println(aa);// 3
        
        int aaa = 2;
        System.out.println( aaa== 1 && aaa++ ==2  ); //aaa++ ==2 这个是true
        System.out.println(aaa);// 2
    }
}
```

* 长路或| 和 短路或||

  共同点：无论长路或还是短路或两边的运算单元都是布尔值都为假时，才为假任意为真，就为真

  区别：长路或 两侧都会被运算短路或 只要第一个是true的，第二个就不进行运算了

* 异或 ^

```java
public class HelloWorld {
	public static void main(String[] args) {
		boolean a = true;
		boolean b = false;
		
		System.out.println(a^b); //不同返回真
		System.out.println(a^!b); //相同返回假

	}
}
```

### 位运算符 运算时的两边单元是二进制

* | 位或
* & 位与
* ^  异或
* ~ 取非
* << 左移 
* \>\> 带符号右移
* \>\>\> 无符号右移

```java
public class HelloWorld {
	public static void main(String[] args) {
		int i  =-10;
		
		//-10的二进制是11111111111111111111111111110110
		//第一位是1，即符号位，代表这是一个负数
		System.out.println(Integer.toBinaryString(i));
		
		//对于正数， 带符号右移 >> 会把所有的位右移，并在最前面补0
		//对于负数， 带符号右移 >> 会把所有的位右移，并在最前面补1
		
		//-10带符号右移1位，移动后前面补齐1
		//得到11111111111111111111111111111011
		//因为第一位是1，所以依然是一个负数，对应的十进制是-5
		int j = i>>1;
		System.out.println(Integer.toBinaryString(j));
		System.out.println(j);
		
		//-10无符号向右移1位，符号位也会向右移，第一位就变成了0
		//得到01111111111111111111111111111011，对应的十进制是2147483643
		int k = i>>>1;
		System.out.println(Integer.toBinaryString(k));		
		
		System.out.println(k);
	}
	
}

```

### 赋值运算符

```java
int i = 1;
i+=++i; //i? 运算顺序是按左至右依次赋值、进行单目运算符计算，然后向右赋值下一个变量、进行单目运算符计算....,最后按双目运算符优先级计算。
```

## 数组

* 数组定义：数组是一个**固定长度**的，包含了**相同类型**数据的 **容器**。

### 创建数组

1. 声明数组
2. 创建数组
3. 数组元素赋值： 分步赋值与同时赋值
4. 获取数组长度 ，使用长度属性获取。`a.length`

```java
public class HelloWorld {
	public static void main(String[] args) {
		//声明一个引用
		int[] a; 
		//创建一个长度是5的数组，并且使用引用a指向该数组
		a = new int[5];
		
		int[] b = new int[5]; //声明的同时，指向一个数组
        
        //分步赋值
        a[0] = 100;
        a[1] = 101;
        a[2] = 103;
        a[3] = 120;
        a[4] = 140;
        
        System.out.println(a.length); //打印数组的长度
        
        
        //写法一： 分配空间同时赋值
        int[] c = new int[]{100,102,444,836,3236};
 
        //写法二： 省略了new int[],效果一样
        int[] d = {100,102,444,836,3236};
         
        //写法三：同时分配空间，和指定内容
        //在这个例子里，长度是3，内容是5个，产生矛盾了
        //所以如果指定了数组的内容，就不能同时设置数组的长度
        int[] e = new int[3]{100,102,444,836,3236};
		
	}
}

```

### 排序 选择和冒泡排序

### 增强for循环

* **增强型for循环只能用来取值，却不能用来修改数组里的值**

```java
public class HelloWorld {
    public static void main(String[] args) {
        int values [] = new int[]{18,62,68,82,65,9};
        //常规遍历
        for (int i = 0; i < values.length; i++) {
			int each = values[i];
			System.out.println(each);
		}
        
        //增强型for循环遍历
        for (int each : values) {
			System.out.println(each);
		}
        
    }
}

```

### 复制数组

* `System.arraycopy(src, srcPos, dest, destPos, length)`

src: 源数组
srcPos: 从源数组复制数据的起始位置
dest: 目标数组
destPos: 复制到目标数组的起始位置
length: 复制的长度

### 二维数组

* 二维数组

```java
int b[][] = new int[][]{
   {1,2,3},
   {4,5,6,9},
   {7,8,9}

};
```

* 二维数组声明、创建、赋值

```java
public class HelloWorld {
	public static void main(String[] args) {
	   //初始化二维数组，
	   int[][] a = new int[2][3]; //有两个一维数组，每个一维数组的长度是3
	   a[1][2] = 5;  //可以直接访问一维数组，因为已经分配了空间
	     
	   //只分配了二维数组
	   int[][] b = new int[2][]; //有两个一维数组，每个一维数组的长度暂未分配
	   b[0]  =new int[3]; //必须事先分配长度，才可以访问
	   b[0][2] = 5;
	   
	   //指定内容的同时，分配空间
	   int[][] c = new int[][]{
			   {1,2,4},
			   {4,5},
			   {6,7,8,9}
	   };

    }
}

```

### Arrays

* Arrays是针对数组的工具类，可以进行 排序，查找，复制填充等功能。 大大提高了开发人员的工作效率。

* 方法介绍：

  - ```java
    // 数组复制
    Arrays.copyOfRange(a, 0, 3);
    // 参数a 原始数组
    // 参数0 开始复制的索引
    // 参数3 结束复制的索引，3取不到
    // 返回一个新的数组
    ```

  * ```java
    // 数组转为字符串
    // Arrays.toString(a)
    // 参数a 原数组
    // 返回字符串
    import java.util.Arrays;
     
    public class HelloWorld {
        public static void main(String[] args) {
            int a[] = new int[] { 18, 62, 68, 82, 65, 9 };
            String content = Arrays.toString(a);
            System.out.println(content);
     
        }
    }
    ```

  * ```java
    // 排序
    // Arrays.sort(a)
    // 参数a 原数组
    // 改变原数组
    import java.util.Arrays;
     
    public class HelloWorld {
        public static void main(String[] args) {
            int a[] = new int[] { 18, 62, 68, 82, 65, 9 };
            System.out.println("排序之前 :");
            System.out.println(Arrays.toString(a));
            Arrays.sort(a);
            System.out.println("排序之后:");
            System.out.println(Arrays.toString(a));
     
        }
    }
    
    ```

  * ```java
    // 查找：二分查找
    // Arrays.binarySearch(a, 62)
    // 参数a 原数组
    // 参数62 要查找的元素
    // 返回目标元素的索引
    // 注意：使用binarySearch进行查找之前，必须使用sort进行排序；如果数组中有多个相同的元素，查找结果是不确定的。
    import java.util.Arrays;
    
    public class HelloWorld {
    	public static void main(String[] args) {
    		int a[] = new int[] { 18, 62, 68, 82, 65, 9 };
    
    		Arrays.sort(a);
    
    		System.out.println(Arrays.toString(a));
    		//使用binarySearch之前，必须先使用sort进行排序
    		System.out.println("数字 62出现的位置:"+Arrays.binarySearch(a, 62));
    	}
    }
    
    ```

  - ```java
    // 判断是否相同
    // Arrays.equals(a, b)
    // 参数a 原数组
    // 参数b 另一个数组
    // 返回布尔值
    import java.util.Arrays;
    
    public class HelloWorld {
    	public static void main(String[] args) {
    		int a[] = new int[] { 18, 62, 68, 82, 65, 9 };
    		int b[] = new int[] { 18, 62, 68, 82, 65, 8 };
    
    		System.out.println(Arrays.equals(a, b));
    	}
    }
    
    ```

  - ```java
    // 使用同一个值，填充整个数组
    // Arrays.fill(a, 5);
    // 参数a 原数组
    // 参数5 用5填充
    import java.util.Arrays;
     
    public class HelloWorld {
        public static void main(String[] args) {
            int a[] = new int[10];
     
            Arrays.fill(a, 5);
     
            System.out.println(Arrays.toString(a));
     
        }
    }
    
    ```

    

## 类和对象

### 方法重载

* 方法的重载指的是方法名一样，但是参数类型不一样
* 可变数量的参数：`public void attack(Hero... heros)` 在方法里，使用操作数组的方式处理参数heros即可，方法接收为数组。

 

### 构造方法

* 实例化是通过调用**构造方法**(又叫做**构造器**)实现的。实例化一个对象的时候，必然调用构造方法
* 在不显示提供构造器时，会默认提供一个隐式的无参构造器。如果显示提供了一个构造器，那么默认的无参的构造方法，就“木有了“。
* 和普通方法一样，构造方法也可以重载

### this

* this：代表当前对象。this使用的一个原因是为了解决：属性标识符和形参标识符一致时指代不清的问题。

* 通过this访问属性：
* 通过this调用其他构造方法：

### 方法传参

* 基本数据类型作为实参，传给形参，实参变量赋给形参，形参是新开辟的内存空间，方法内的表达式无法改变实参值
* 引用数据类型作为实参，传给形参，实参引用赋给形参，形参是新开辟的内存空间，。

### 包package

* 把比较接近的类，规划在同一个包下
* 在java文件中最开始的地方声明该类所处于的包名
* 使用同一个包下的其他类，直接使用即可，使用同一个包下的其他类，直接使用即可

### 访问修饰符（修饰成员变量）

* 类之间的关系：自身、同包子类、不同包子类、同包类、其他
* 红色字体表示不行。![image-20240710093904328](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240710093904328.png)

### 类属性（用static修饰的成员变量）

* 如果一个属性，**所有的英雄都共享**，都是一样的，那么就应该设计为类属性。比如血量上限，所有的英雄的血量上限都是 9999，不会因为英雄不同，而取不同的值。 这样的属性，就适合设计为类属性



### 类方法（用static修饰的成员方法，还可以修饰代码块）

* 如果在某一个方法里，调用了对象属性，那么这个方法，就必须设计为对象方法。如果一个方法，没有调用任何对象属性，那么就可以考虑设计为类方法。这样的方法，更带有**功能性**色彩就像取随机数一样，random()是一个功能用途的方法.。这个类有什么功能，而不是这个类实例的对象有什么功能。

### 属性初始化

* 对象属性初始化有三种：初始化顺序也是1-2-3

  \1. 声明该属性的时候初始化

  \2. 初始化块 {}

  \3. 构造方法中初始化

* 类属性初始化有两种：

  \1. 声明该属性的时候初始化
  \2. 静态初始化块static{}

### 单例模式（目的是实现一个类只被实例化一次）

饿汉式：实现目的的思路

1. 私有化构造方法，将在外部可多次new对象的能力禁掉。
2. 利用类属性一个类只有一个的特征，一个实例化对象赋值给类属性
3. 外部如何获取这个对象呢？建立一个公有静态方法，返回类属性。

懒汉式：实现目的的思路

1. 私有化构造方法，将在外部可多次new对象的能力禁掉。
2. 创建一个类属性，但不实例化对象赋值给类属性。
3. 创建一个类方法，在类方法中将实例化对象赋值给类属性。

什么时候使用饿汉式 什么时候使用懒汉式

**饿汉式**是立即加载的方式，无论是否会用到这个对象，都会加载。
如果在构造方法里写了性能消耗较大，占时较久的代码，比如建立与数据库的连接，那么就会在启动的时候感觉稍微有些卡顿。

**懒汉式**，是延迟加载的方式，只有使用的时候才会加载。 并且有[线程安全](https://how2j.cn/k/thread/thread-synchronized/355.html#step793)的考量(鉴于同学们学习的进度，暂时不对线程的章节做展开)。
使用懒汉式，在启动的时候，会感觉到比饿汉式略快，因为并没有做对象的实例化。 但是在第一次调用的时候，会进行实例化操作，感觉上就略慢。

看业务需求，如果业务上允许有比较充分的启动和初始化时间，就使用饿汉式，否则就使用懒汉式

### 枚举类型 枚举也是个类

```java
public enum Season {
	SPRING,SUMMER,AUTUMN,WINTER
}// SPRING是常量
```

## 接口与继承

### 接口

* **接口就像是一种约定**，我们使一个类实现这个接口，就约定这个类具有该接口的功能

### 对象转型



* 子类（接口实现类）到父类自动转型（接口），一定成功
* 父类（接口）到子类强制转型（接口实现类），可能成功，可能失败
* 没有继承关系的两个类，互相转换，一定会失败

总结 

**一个引用标识符，它有一个引用类型，还有一个它指向的对象类型，只有当它的引用类型层级低于它指向的对象类型才可以，若引用类型高于它指向的对象类型，编译时它可以调用它指向对象类型没有的方法等，执行时会报错。**



| 引用类型   | 对象类型   |      |
| ---------- | ---------- | ---- |
| 相同       | 相同       | ok   |
| 父类       | 子类       | ok   |
| 接口       | 接口实现类 | ok   |
| 子类       | 父类       | no   |
| 接口实现类 | 接口       | no   |
| 其他       |            | no   |

*  `a instanceof  A` 判断a引用指向的**对象**，是否是A类型或者A的向上类型（父类）。

### 重写

### 多态

* 多态中的方法默认为抽象，公开方法，jdk8也推出了默认方法、静态方法、私有方法。

* 操作符的多态
  \+ 可以作为算数运算，也可以作为字符串连接

* 类的多态
  父类引用指向子类对象

* 多态：**都是同一个类型，调用同一个方法，却能呈现不同的状态**

* 要实现类的多态，需要如下条件
  \1. 父类（接口）引用指向子类对象
  \2. 调用的方法有[重写](https://how2j.cn/k/interface-inheritance/interface-inheritance-override/309.html)

* 例子

  如果物品的种类特别多，那么就需要设计很多的方法
  比如useArmor,useWeapon等等

  这个时候采用多态来解决这个问题
  设计一个方法叫做useItem，其参数类型是Item
  如果是使用血瓶，调用该方法
  如果是使用魔瓶，还是调用该方法
  无论英雄要使用什么样的物品，**只需要一个方法**即可

  

  **对象使用另一个对象的方法，并且希望不同对象调用的其他对象的方法不同，即实现相同类的对象，调用同一个方法，却呈现出不同的状态**

  ```java
  package charactor;
  
  import property.Item;
  import property.LifePotion;
  import property.MagicPotion;
    
  public class Hero {
      public String name; 
      protected float hp;
  
      public void useItem(Item i){ //对象使用另一个对象的方法，并且希望不同对象调用的其他对象的方法不同，实现相同类的对象，调用同一个方法，却呈现出不同的状态
      	i.effect();
      }
  
      public static void main(String[] args) {
      	
      	Hero garen =  new Hero();
          garen.name = "盖伦";
      
      	LifePotion lp =new LifePotion();
      	MagicPotion mp =new MagicPotion();
      	
      	garen.useItem(lp);
      	garen.useItem(mp);    	
      	
      }
        
  }
  
  ```

  

### 隐藏

与重写类似，方法的**重写是**子类覆盖父类的**对象方法**

**隐藏**，就是子类覆盖父类的**类方法**



`Hero h =new ADHero();`

h.battleWin(); //battleWin是一个类方法
h是父类类型的引用
但是指向一个子类对象
h.battleWin(); 会调用父类的方法？还是子类的方法？



父类方法 



**怎么理解？**

不需要过于复杂的理解，按照C#语言规定，静态方法（类方法）只能使用类来调用，不能通过实例来调用。 因此，无论如何，h的类型为Hero，h.battleWin()  =>等价于   Hero.battleWin();   所以，判断某个实例调用的静态方法（类方法）是什么，只用知道这个实例属于哪个类，就显然知道调用的是该类的静态方法。 总结：类方法，也叫类的静态方法，与实例无关，只与类型有关。

### super

* 子类构造方法会默认调用父类的 无参的构造方法，并且是父类构造方法**先调用**
* 使用关键字**super** 显式调用父类带参的构造方法
* **通过super调用父类的方法与属性**

### Object类

* Object类是所有类的父类，声明一个类的时候，默认是继承了Object。

* Object类方法

  1. `toString()`toString()的意思是返回当前对象的**字符串表达**。**通过 System.out.println 打印对象就是打印该对象的toString()返回值**

  2. **finalize()** 当一个对象没有任何引用指向的时候，它就满足垃圾回收的条件

     当它被垃圾回收的时候，它的finalize() 方法就会被调用。

     finalize() 不是开发人员主动调用的方法，而是由虚拟机JVM调用的。

  3. **equals()** 用于判断两个对象的内容是否相同 

     ==  这不是Object的方法，但是用于判断两个对象是否相同
     **更准确的讲**，用于判断两个引用，是否指向了同一个对象

  4. **hashCode()** hashCode方法返回一个对象的哈希值

  5. 线程同步相关方法 `wait()  notify()   notifyAll()`

  6. **getClass()**  getClass()会返回一个对象的[类对象](https://how2j.cn/k/reflection/reflection-class/108.html)

### final（修饰类、方法、基本类型变量，引用类型变量）

* 修饰类：当Hero被修饰成final的时候，表示Hero不能够被继承
  其子类会出现编译错误
* 修饰方法：Hero的useItem方法被修饰成final,那么该方法在ADHero中，不能够被重写
* 修饰基本类型变量：final修饰基本类型变量，表示该变量只有一次赋值机会
* 修饰引用：h引用被修饰成final，表示该引用只有**1**次指向对象的机会
* 常量指的是可以公开，直接访问，不会变化的值`publicstaticfinalintitemTotalNumber = 6;`

### 抽象类

* 当一个类有抽象方法的时候，该类必须被声明为抽象类

* 在类中声明一个方法，这个方法没有实现体，是一个“空”方法。这样的方法就叫抽象方法，使用修饰符“abstract"

* 类可以在不提供抽象方法的前提下，声明为抽象类
  一旦一个类被声明为抽象类，就不能够被直接实例化

* 抽象类和接口的区别

  成员变量上：

  ​	抽象类可以定义public,protected,package,private静态和非静态属性，final和非final属性。

  ​	但是接口中声明的属性，只能是public静态final的，且public静态final可省略。

  方法上：

  ​	抽象类和接口都可以有实体方法。 接口中的实体方法，叫做[默认方法](https://how2j.cn/k/interface-inheritance/interface-inheritance-default-method/676.html)

  

### 内部类

* 非静态内部类：非静态内部类可以直接在一个类里面定义。

  * 适用的情况：只有一个外部类对象存在的时候，才有意义。战斗成绩只有在一个英雄对象存在的时候才有意义

  * 语法：**new 外部类().new 内部类()**

  * 内部类的访问权限：可以直接访问外部类的**private**实例属性

* 静态内部类：在一个类里面声明一个静态内部类

  * 适用情况：比如敌方水晶，当敌方水晶没有血的时候，己方所有英雄都取得胜利，而不只是某一个具体的英雄取得胜利。
  * 语法：**new 外部类.静态内部类();**
  * 内部类的访问权限：因为没有一个外部类的实例，所以在静态内部类里面**不可以访问外部类的实例属性和方法**，可以访问私有静态成员。

  

* 匿名类：匿名类指的是在**声明一个类的同时实例化它**。将（创建子类实现接口，重写方法、）（实例化子类）的两个过程简化成一个。格式为

  `接口 对象=new 接口（）{ 重写接口中的方法 }；`为什么叫匿名？是因为新创建的子类没有名字

* 本地类：本地类可以理解为有名字的匿名类。内部类与匿名类不一样的是，内部类必须声明在成员的位置，即与属性和方法平等的位置。本地类和匿名类一样，直接声明在代码块里面，可以是主方法，for循环里等等地方。将将（创建子类实现接口，重写方法、）（实例化子类）的两个过程都写在了外部类的代码块里。

* 在匿名类中使用外部的局部变量：在匿名类中使用外部的局部变量，外部的局部变量必须修饰为final。在jdk8中，已经不需要强制修饰成final了，如果没有写final，不会报错，因为编译器**偷偷的**帮你加上了看不见的final

### 默认方法

* 默认方法是JDK8新特性，指的是接口也可以提供具体方法了，而不像以前，只能提供抽象方法

* ```java
  package charactor;
  
  public interface Mortal {
  	public void die();
  
  	default public void revive() {
  		System.out.println("本英雄复活了");
  	}
  }
  
  ```

  

### 综合练习

## 数字与字符串

### 装修拆箱

* 数字封装类有Byte,Short,Integer,Long,Float,Double这些类都是抽象类Number的子类
* 自动装箱与自动拆箱：**通过=符号****自动**把 基本类型 转换为 类类型 就叫装箱，通过=就自动转换成int类型，就叫拆箱。
* int的最大值可以通过其对应的封装类Integer.MAX_VALUE获取

### 字符串转换

* 数字转字符串

  ```java
  package digit;
   
  public class TestNumber {
   
      public static void main(String[] args) {
          int i = 5;
          
          //方法1
          String str = String.valueOf(i);
          
          //方法2
          Integer it = i;
          String str2 = it.toString();
          
      }
  }
  
  ```

* 字符串转数字

  ```java
  package digit;
   
  public class TestNumber {
   
      public static void main(String[] args) {
  
      	String str = "999";
      	
      	int i= Integer.parseInt(str);
      	
      	System.out.println(i);
          
      }
  }
  
  ```

  

### 数学方法

* java.lang.Math提供了一些常用的数学运算方法，并且都是以静态方法的形式存在。

* ```java
  package digit;
   
  public class TestNumber {
   
      public static void main(String[] args) {
      	float f1 = 5.4f;
      	float f2 = 5.5f;
      	//5.4四舍五入即5
      	System.out.println(Math.round(f1));
      	//5.5四舍五入即6
      	System.out.println(Math.round(f2));
      	
      	//得到一个0-1之间的随机浮点数（取不到1）
      	System.out.println(Math.random());
      	
      	//得到一个0-10之间的随机整数 （取不到10）
      	System.out.println((int)( Math.random()*10));
      	//开方
      	System.out.println(Math.sqrt(9));
      	//次方（2的4次方）
      	System.out.println(Math.pow(2,4));
      	
      	//π
      	System.out.println(Math.PI);
      	
      	//自然常数
      	System.out.println(Math.E);
      }
  }
  
  ```

  

### 格式化输出

* 和字符串拼接功能一样，只不过时简便一点。

* System.out.printf和 System.out.format格式化效果一样。

* 使用方法是：`System.out.printf(带占位符的字符串，占位符处的值...)`

* 占位符 %s 表示字符串
  %d 表示数字
  %n 表示换行

* 换行符

* 其他常用格式化方式

  ```java
  package digit;
   
  import java.util.Locale;
    
  public class TestNumber {
    
      public static void main(String[] args) {
          int year = 2020;
          //总长度，左对齐，补0，千位分隔符，小数点位数，本地化表达
           
          //直接打印数字
          System.out.format("%d%n",year);
          //总长度是8,默认右对齐
          System.out.format("%8d%n",year);
          //总长度是8,左对齐
          System.out.format("%-8d%n",year);
          //总长度是8,不够补0
          System.out.format("%08d%n",year);
          //千位分隔符
          System.out.format("%,8d%n",year*10000);
   
          //小数点位数
          System.out.format("%.2f%n",Math.PI);
           
          //不同国家的千位分隔符
          System.out.format(Locale.FRANCE,"%,.2f%n",Math.PI*10000);
          System.out.format(Locale.US,"%,.2f%n",Math.PI*10000);
          System.out.format(Locale.UK,"%,.2f%n",Math.PI*10000);
           
      }
  }
  
  ```

  

### 字符

* Character常见方法

  ```java
  package character;
  
  public class TestChar {
  
  	public static void main(String[] args) {
  		
  		System.out.println(Character.isLetter('a'));//判断是否为字母
  		System.out.println(Character.isDigit('a')); //判断是否为数字
  		System.out.println(Character.isWhitespace(' ')); //是否是空白
  		System.out.println(Character.isUpperCase('a')); //是否是大写
  		System.out.println(Character.isLowerCase('a')); //是否是小写
  		
  		System.out.println(Character.toUpperCase('a')); //转换为大写
  		System.out.println(Character.toLowerCase('A')); //转换为小写
  
  		String a = 'a'; //不能够直接把一个字符转换成字符串
  		String a2 = Character.toString('a'); //转换为字符串
  		
  	}
  }
  
  ```

* \ 转义  \t制表符用来对齐

  

### 字符串

* 字符串创建的方法有两种：一是字面量，二是new
* String类是被final修饰的，不能被继承
* 字符格式化`String.format(带占位符的字符串，占位符处的值...)`返回一个新的字符串
* 字符串长度是通过length()方法获得的，与数组不一样。
* 

### 操纵字符串

* ![image-20240710163958137](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240710163958137.png)

* ```java
  char c = sentence.charAt(0);
  char[] cs = sentence.toCharArray(); //获取对应的字符数组
  
  //左闭右开
  String subString2 = sentence.substring(3,5);//截取子字符串
  //根据,进行分割，得到3个子字符串
  String subSentences[] = sentence.split(",");
  //去掉首尾空格
  System.out.println(sentence.trim());
  
  //全部变成小写
  System.out.println(sentence.toLowerCase());
  //全部变成大写
  System.out.println(sentence.toUpperCase());
  
  System.out.println(sentence.indexOf('8')); //字符第一次出现的位置
  
  System.out.println(sentence.indexOf("超神")); //字符串第一次出现的位置
  
  System.out.println(sentence.lastIndexOf("了")); //字符串最后出现的位置
  
  System.out.println(sentence.indexOf(',',5)); //从位置5开始，出现的第一次,的位置
  
  System.out.println(sentence.contains("击杀")); //是否包含字符串"击杀"
  
  replaceAll 替换所有的
  replaceFirst 只替换第一个
      
  System.out.println(str1.startsWith(start));//以...开始
  System.out.println(str1.endsWith(end));//以...结束
  ```

### 比较字符串

### StringBuffer

StringBuffer是可变长的字符串

* append追加
  delete 删除
  insert 插入
  reverse 反转

  ```java
  package character;
   
  public class TestString {
   
      public static void main(String[] args) {
          String str1 = "let there ";
  
          StringBuffer sb = new StringBuffer(str1); //根据str1创建一个StringBuffer对象
          sb.append("be light"); //在最后追加
          
          System.out.println(sb);
          
          sb.delete(4, 10);//删除4-10之间的字符
          
          System.out.println(sb);
          
          sb.insert(4, "there ");//在4这个位置插入 there
          
          System.out.println(sb);
          
          sb.reverse(); //反转
          
          System.out.println(sb);
  
      }
   
  }
  
  ```

  

### MyStringBuffer

## 日期

### Date

* Date类
  注意：是**java.util.Date;**
  而非 java.sql.Date，此类是给数据库访问的时候使用的

* 时间原点：1970年1月1日 8点0分0秒。每过一毫秒，就+1。

* 创建时间对象：`Date d1 = new Date();`  `d1`是当前时间 输出d1看到的是“Tue Jan 05 09:51:48 CST 2016” 这样的格式。

* `d1.getTime();`

  ```java
  //得到一个long型的整数
  //这个整数代表 1970.1.1 08:00:00:000，每经历一毫秒，增加1
  ```

* `new Date().getTime()` 和 `System.currentTimeMillis()` 是一样的

### 日期格式化

* Date对象转字符串

  ```java
  package date;
   
  //
  import java.text.SimpleDateFormat;
  import java.util.Date;
   
  public class TestDate {
   
      public static void main(String[] args) {
           
          //y 代表年
          //M 代表月
          //d 代表日
          //H 代表24进制的小时
          //h 代表12进制的小时
          //m 代表分钟
          //s 代表秒
          //S 代表毫秒
          SimpleDateFormat sdf =new SimpleDateFormat("yyyy-MM-dd HH:mm:ss SSS" );
          Date d= new Date();
          String str = sdf.format(d);
          System.out.println("当前时间通过 yyyy-MM-dd HH:mm:ss SSS 格式化后的输出: "+str);
          
          SimpleDateFormat sdf1 =new SimpleDateFormat("yyyy-MM-dd" );
          Date d1= new Date();
          String str1 = sdf1.format(d1);
          System.out.println("当前时间通过 yyyy-MM-dd 格式化后的输出: "+str1);
          
      }
  }
  
  ```

  

* 字符串转Date对象

  ```java
  package date;
   
  //
  import java.text.ParseException;
  import java.text.SimpleDateFormat;
  import java.util.Date;
   
  public class TestDate {
   
      public static void main(String[] args) {
          SimpleDateFormat sdf =new SimpleDateFormat("yyyy/MM/dd HH:mm:ss" );
   
          String str = "2016/1/5 12:12:12";
           
          try {
              Date d = sdf.parse(str);
              System.out.printf("字符串 %s 通过格式  yyyy/MM/dd HH:mm:ss %n转换为日期对象: %s",str,d.toString());
          } catch (ParseException e) {
              // TODO Auto-generated catch block
              e.printStackTrace();
          }
           
      }
  }
  
  ```

  

### Calender

* Calendar类即日历类，常用于进行“翻日历”，比如**下个月的今天是多久**

* Calendar与Date进行转换和采用[单例模式](https://how2j.cn/k/class-object/class-object-singleton/349.html)获取日历对象Calendar.getInstance();

* ```java
  package date;
   
  //
  import java.util.Calendar;
  import java.util.Date;
   
  public class TestDate {
   
      public static void main(String[] args) {
          //采用单例模式获取日历对象Calendar.getInstance();
          Calendar c = Calendar.getInstance();
           
          //通过日历对象得到日期对象
          Date d = c.getTime();
   
          Date d2 = new Date(0);
          c.setTime(d2); //把这个日历，调成日期 : 1970.1.1 08:00:00
      }
  }
  
  ```

* 翻日历

  ```java
  package date;
  
  import java.text.SimpleDateFormat;
  //
  import java.util.Calendar;
  import java.util.Date;
  
  public class TestDate {
  
  	private static SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
  
  	public static void main(String[] args) {
  		Calendar c = Calendar.getInstance();
  		Date now = c.getTime();
  		// 当前日期
  		System.out.println("当前日期：\t" + format(c.getTime()));
  
  		// 下个月的今天
  		c.setTime(now);
  		c.add(Calendar.MONTH, 1);
  		System.out.println("下个月的今天:\t" +format(c.getTime()));
  
  		// 去年的今天
  		c.setTime(now);
  		c.add(Calendar.YEAR, -1);
  		System.out.println("去年的今天:\t" +format(c.getTime()));
  
  		// 上个月的第三天
  		c.setTime(now);
  		c.add(Calendar.MONTH, -1);
  		c.set(Calendar.DATE, 3);
  		System.out.println("上个月的第三天:\t" +format(c.getTime()));
  
  	}
  
  	private static String format(Date time) {
  		return sdf.format(time);
  	}
  }
  
  ```

  

## 异常处理

* 异常分类：可查异常，运行时异常和错误

* 可查异常：编译器可以查出来的异常，作为程序员必须手动处理

  异常处理常见手段： try catch finally throws

  * try-catch-finally

    1.将可能抛出FileNotFoundException **文件不存在异常**的代码放在try里
    2.如果文件存在，就会顺序往下执行，并且不执行catch块中的代码

    3. 如果文件不存在，try 里的代码会立即终止，程序流程会运行到对应的catch块中
    4. e.printStackTrace(); 会打印出方法的调用痕迹，如此例，会打印出异常开始于TestException的第16行，这样就便于定位和分析到底哪里出了异常

  * throws 将异常抛给上层方法处理

  * throw：throws 出现在方法声明上，而throw通常都出现在方法体内。throws 表示出现异常的一种可能性，并不一定会发生这些异常；throw则是抛出了异常，执行throw则一定抛出了某个异常对象。

* 运行时异常：在编写代码的时候，依然可以使用try catch throws进行处理，与可查异常不同之处在于，**即便不进行try catch，也不会有编译错误**。

  比如：除数不能为0异常:ArithmeticException
  下标越界异常:ArrayIndexOutOfBoundsException
  空指针异常:NullPointerException

* 错误Error，指的是**系统级别的异常**，通常是内存用光了

* ![image-20240710171608455](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240710171608455.png)

* ![image-20240710201515310](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240710201515310.png)Throwable

### 自定义异常

```java

package charactor;
 
public class Hero {
    public String name; 
    protected float hp;

    public void attackHero(Hero h) throws EnemyHeroIsDeadException{
    	if(h.hp == 0){
    		throw new EnemyHeroIsDeadException(h.name + " 已经挂了,不需要施放技能" );
    	}
    }

    public String toString(){
    	return name;
    }
    
    class EnemyHeroIsDeadException extends Exception{
        
    	public EnemyHeroIsDeadException(){
    		
    	}
        public EnemyHeroIsDeadException(String msg){
            super(msg);
        }
    }
     
    public static void main(String[] args) {
    	
        Hero garen =  new Hero();
        garen.name = "盖伦";
        garen.hp = 616;

        Hero teemo =  new Hero();
        teemo.name = "提莫";
        teemo.hp = 0;
        
        try {
			garen.attackHero(teemo);
			
		} catch (EnemyHeroIsDeadException e) {
			// TODO Auto-generated catch block
			System.out.println("异常的具体原因:"+e.getMessage());
			e.printStackTrace();
		}
        
    }
}

```



## IO

## 泛型

* 泛型的用法是在容器后面添加<Type> Type可以是类，抽象类，接口。
* 假设容器的泛型是Hero,那么**Hero的子类**APHero,ADHero**都可以放进去**
* 泛型简写：为了不使编译器出现警告，需要前后都使用泛型，像这样：`ArrayList<Hero> heros = new ArrayList<Hero>();`
* 不过JDK7提供了一个可以略微减少代码量的泛型简写方式 `ArrayList<Hero> heros2 = new ArrayList<>();`

### 通配符

* <? extends Hero>容器里面可能是Hero或者它的子类。所以 可以确凿的是，**从heroList取出来的对象，一定是可以转型成Hero的**，所以可以从容器中取东西，不能往容器放东西。
* <? super Hero>容器里面可能是Hero或者它的父类。所以可以往容器里放东西，从容器中取东西有风险。
* <?> 代表任意泛型,这个容器什么泛型都有可能.所以只能以Object的形式取出来并且不能往里面放对象，因为不知道到底是一个什么泛型的容器
* <u>疑问，这个容器什么泛型都有可能，是这个容器内元素引用类型不一定？是这个意思。还是说容器内每个元素引用类型不一样？容器中元素引用类型一样</u>（对象类型是父类和子类转型成父类（多态）），对象类型只在new的时候确定。

如果希望只取出，不插入，就使用? extends Hero
如果希望只插入，不取出，就使用? super Hero
如果希望，又能插入，又能取出，就不要用通配符？

### 泛型转型

<u>所以子类泛型**不可以**转换为父类泛型（还是有可能成功的把？）</u>

父类泛型不能转型为子类泛型

## Lambda

## 集合

### List方法

* List接口 继承了 Collection接口

* List接口中的抽象方法有

  ```java
  //重载方法都列出来了
  int size();
  Object[] toArray();
  <T> T[] toArray(T[] a); //toArray可以把一个ArrayList对象转换为数组。看一下这个函数的使用例子，形参传的是一个空数组。
  //增
  boolean add(E e);
  void add(int index, E element);
  boolean addAll(Collection<? extends E> c);
  boolean addAll(int index, Collection<? extends E> c);//把另一个容器所有对象都加进来，不是加容器。
  //删
  boolean remove(Object o); //也可以根据对象删除
  E remove(int index); //可以根据下标删除ArrayList的元素
  void clear(); //clear 清空一个ArrayList
  //改
  E set(int index, E element);//用于替换指定位置的元素//Set接口没这个方法
  //查
  boolean contains(Object o); //判断标准： 是否是同一个对象，而不是name是否相同
  boolean containsAll(Collection<?> c);
  int indexOf(Object o);// 用于判断一个对象在ArrayList中所处的位置，与contains一样，判断标准是对象是否相同，而非对象的name值是否相等
  E get(int index);//通过get获取指定位置的对象
  
  //....
  ```

* ArrayList是List的常用实现类，实现了上述方法

### 泛型

* 不指定泛型的容器，可以存放任何类型的元素
  指定了泛型的容器，只能存放指定类型的元素以及其子类

### 遍历

* 可以用size()和get()分别得到大小，和获取指定位置的元素，结合for循环就可以遍历出ArrayList的内容

  ```java
  package collection;
  
  import java.util.ArrayList;
  import java.util.Iterator;
  import java.util.List;
  
  import charactor.Hero;
  
  public class TestCollection {
  
  	public static void main(String[] args) {
  		List<Hero> heros = new ArrayList<Hero>();
  
  		// 放5个Hero进入容器
  		for (int i = 0; i < 5; i++) {
  			heros.add(new Hero("hero name " + i));
  		}
  
  		// 第一种遍历 for循环
  		System.out.println("--------for 循环-------");
  		for (int i = 0; i < heros.size(); i++) {
  			Hero h = heros.get(i);
  			System.out.println(h);
  		}
  
  	}
  
  }
  
  ```

  

* 使用迭代器Iterator遍历集合中的元素

  ```java
  package collection;
  
  import java.util.ArrayList;
  import java.util.Iterator;
  import java.util.List;
  
  import charactor.Hero;
   
  public class TestCollection {
  
      public static void main(String[] args) {
      	List<Hero> heros = new ArrayList<Hero>();
      	
      	//放5个Hero进入容器
      	for (int i = 0; i < 5; i++) {
  			heros.add(new Hero("hero name " +i));
  		}
      	
      	//第二种遍历，使用迭代器
      	System.out.println("--------使用while的iterator-------");
      	Iterator<Hero> it= heros.iterator();
      	//从最开始的位置判断"下一个"位置是否有数据
      	//如果有就通过next取出来，并且把指针向下移动
      	//直到"下一个"位置没有数据
      	while(it.hasNext()){
      		Hero h = it.next();
      		System.out.println(h);
      	}
      	//迭代器的for写法
      	System.out.println("--------使用for的iterator-------");
      	for (Iterator<Hero> iterator = heros.iterator(); iterator.hasNext();) {
  			Hero hero = (Hero) iterator.next();
  			System.out.println(hero);
  		}
      	
      }
       
  }
  
  ```

* 使用增强型for循环可以非常方便的遍历ArrayList中的元素，这是很多开发人员的首选。不过增强型for循环也有不足：
  无法用来进行ArrayList的初始化
  无法得知当前是第几个元素了，当需要只打印单数元素的时候，就做不到了。 必须再自定下标变量。

  ```java
  package collection;
  
  import java.util.ArrayList;
  import java.util.Iterator;
  import java.util.List;
  
  import charactor.Hero;
  
  public class TestCollection {
  
  	public static void main(String[] args) {
  		List<Hero> heros = new ArrayList<Hero>();
  
  		// 放5个Hero进入容器
  		for (int i = 0; i < 5; i++) {
  			heros.add(new Hero("hero name " + i));
  		}
  
  		// 第三种，增强型for循环
  		System.out.println("--------增强型for循环-------");
  		for (Hero h : heros) {
  			System.out.println(h);
  		}
  
  	}
  
  }
  
  ```

  

### Vector VS ArrayList VS LinkedList

#### Vector

**底层：**使用的是**`Object` 数组**；

**线程安全**；

**实践中使用频率**：很少使用；

#### ArrayList

**底层：**使用的是**`Object` 数组**；

**线程不安全；**

**实践中使用频率**：经常使用；

#### LinkedList

**底层：**使用的是**双向链表**；

**线程不安全；**

#### 面试题

##### 为什么数组索引从0开始呢？假如从1开始不行吗？

* 因为寻址公式是：数组的首地址+索引乘以存储数组的类型大小，数组索引结合寻址公式可以得到对应元素的内存地址。
* 如果数组的索引从1开始，寻址公式中，就需要增加一次减法操作，对于CPU来说就多了一次指令，性能不高。

##### 操作数组的时间复杂度（查找，插入，删除）？

* 随机查询（按索引查）

  数组元素的访问是通过索引来访问的，计算机通过数据的首地址和寻址公式可以很快速的找到想要访问的元素。O(1)

* 未知索引查询

  如果不对数组进行排序操作，那么只能按顺序查找元素，时间复杂度是O(n)

  如果对数据进行排序操作，使用二分查找的方式查找元素，时间复杂度是O(logn)

* 插入和删除

  需要挪动数据，最好情况是O(1)，最坏情况下是O(n)，平均情况下时间复杂度是O(n)

##### 往ArrayList里面添加数据（第一次添加数据、添加第2-10次数据、添加第11次数据）面试题：ArrayList底层的实现原理是什么？

ArrayList add方法源码jdk8：

![image-20240712110541729](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240712110541729.png)

add方法：首先确保内部容量（当前ArrayList容量+1），然后向elementData中添加数据。

确保内部容量方法：确定明确的容量（计算容量）

计算容量：如果elementData空 返回容量为10，否则返回当前ArrayList容量+1

确定明确的容量：返回值与当前ArrayList容量做差，如果大于0，扩容

所以扩容有两类时间点：一是第一次添加数据时，一是后续容量不够时。

![image-20240712111735637](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240712111735637.png)

##### ArrayList list=new ArrayList(10)中的list扩容几次？

源码：![image-20240712112212041](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240712112212041.png)

回答：

* 该语句只是声明和实例了一个ArrayList，指定了容量为10，未扩容。

##### 如何实现数组和List之间的转换？

* 数组转List  使用Array一个静态方法asList

  ![image-20240712114256998](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240712114256998.png)

  返回的List的实现类，不是我们常使用的ArrayList，它在Arrays类中写了一个静态内部类，该内部类继承了了List接口，且没有创建新的数组来存储容器元素，还是指向了传进构造器的数组

* List转成数组：使用List的toArray()方法

  ![image-20240712115122933](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240712115122933.png)

有参的toArray()方法可以通过参数的类型帮助确定返回数组的类型，要不然就返回Object类型数组。

回答：

* 数组转list，使用JDK中java.util.Arrays工具类的asList方法
* List转数组，使用List的toArray方法。无参toArray方法返回Object数组，传入初始化长度的数组对象，返回该对象数组

再问：

* 用Array.asList转成List后，如果修改了数组内容，list受影响吗？
* List用toArray转数组后，如果修改了List内容，数组受影响吗？

再答：

* 用Array.asList转成List后，如果修改了数组内容，list受影响。因为它的底层使用的Arrays类中的一个内部类ArrayList来构造的集合，在这个集合的构造器中，把我们传入的这个集合进行了包装而已，最终指向的都是同一个内存地址。
* List用toArray转数组后，如果修改了List内容，数组不受影响。当调用toArray以后，底层它进行了数组的拷贝，跟原来的元素就没什么关系了，所以即使list修改了以后，数组也不受影响。

##### ArrayList和LinkedList的区别是什么？五颗星出现频率

* 底层数据结构
* 效率
* 空间
* 线程是否安全

![image-20240712154603271](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240712154603271.png)

![image-20240712154650597](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240712154650597.png)

每个线程都一份自己的局部变量

包装类？？？？

### Set

* Set中的元素不能重复
* Set中的元素没有顺序，严格的说，是没有按照元素的插入顺序排列
* Set不提供get()来获取指定位置的元素，所以遍历需要用到迭代器，或者增强型for循环

### Map方法

```java
//增
public V put(K key, V value)
public void putAll(Map<? extends K, ? extends V> m)
    
//删
public V remove(Object key)
    
//改
public V put(K key, V value)
public void putAll(Map<? extends K, ? extends V> m)
    
//查
public V get(Object key)
    
//遍历

```

![image-20240712164245318](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240712164245318.png)



#### 使用的数据结构

* 红黑树：红黑树是对二叉排序树的改进。二叉排序树和红黑树都是为了加快数据查找速度而设计的数据结构。红黑树比二叉排序树优秀在是自平衡的，不会出现树变成链表的极端情况，将查找的时间复杂度保存在O(logn)

* 散列表：用数组来实现。 key====》数组下标======》得到要查找的内容。

  将键（key）映射为数字下标的函数叫做**散列函数**。可以表示为：hashValue = hash(key)

* 散列函数的基本要求：

  * 散列函数计算得到的散列值必须是**大于等于0的正整数**。因为hashValue需要作为数组的下标。
  * 如果key1 == key2，那么讲过hash后得到的哈希值也必相同即：hash(key1) == hash(key2)
  * **如果key1 != key2，那么经过hash后得到的哈希值也必不相同即：hash(key1) != hash(key2)**    不易实现

  散列冲突：多个key映射到同一个数组下标位置：

  解决哈希冲突的方法：

  * 链表法（拉链法）

  * ![image-20240714184716712](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240714184716712.png)

  * 用链表法解决冲突的时间复杂度：

  * 插入操作

    ![image-20240714185052176](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240714185052176.png)

  * 查找和删除操作

    ![image-20240714185117837](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240714185117837.png)

#### 面试题

##### 说一下HashMap的实现原理？五颗星出现频率

* HashMap的数据结构：底层使hash表数据结构，即数组和链表或红黑树
* 当我们往HashMap中put元素时，利用key的hashCode重新hash计算出当前元素在数组中的下标
* 存储时，如果出现hash值相同的key，此时有两种情况：
  * 如果key相同，则覆盖原始值；
  * 如果key不同（出现冲突），则将当前的key-value放入链表或红黑树中。（链表长度大于8且数组长度大于64转换为红黑树）
* 获取时，直接找到hash值对应的下标，在进一步判断key是否相同，从而找到对应值。

##### HashMap的jdk1.7和jdk1.8有什么区别？五颗星出现频率

* JDK1.8之前采用的是拉链法。拉链法：将链表和数组相结合。也就是说创建一个链表数组，数组中每一格就是一个链表。若遇到哈希冲突。则将冲突的值加到链表中即可。
* jdk1.8在解决哈希冲突时有了较大的变化，当链表长度大于阈值（默认为8）时并且数组长度达到64时，将链表转化为红黑树，以减少搜索时间。扩容resize()时，红黑树拆分成的树的节点数小于等于临界值6个，则退化成链表。

 ##### HashMap的put方法的具体流程？五颗星出现频率

![image-20240714210548292](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240714210548292.png)

##### 讲一讲HashMap的扩容机制？四颗星出现频率



![HashMap扩容操作](C:\Users\DELL\Pictures\Screenshots\HashMap扩容操作.png)



##### HashMap的寻址算法？四颗星出现频率

* 计算对象的hashCode()
* 再进行调用hash()方法进行二次哈希，hashcode值右移16位再异或运算，让哈希分布均匀
* 最后(capacity-1)&hash得到索引

##### 为何HashMap的数组长度一定是2的次幂？四颗星出现频率

* 计算索引是效率更高：如果是2的n次幂可以使用位与运算代替取模
* 扩容时重新计算索引效率更高：hash&oldCap == 0的元素留在原来位置。负责新位置 = 旧位置 + oldCap

#####  hashmap在1.7情况下的多线程死循环问题？

![image-20240714221704582](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240714221704582.png)



## 反射

* 类对象 ：首先是一个对象，什么类型的对象？Class类型的对象。**类对象**，就是用于描述这种类，都有什么属性，什么方法的

* 不同对象，他们属性的具体值不同。不同类，他们属性不同，方法不同。
* 每个类，只用一个类对象，描述他们有什么属性，有什么方法
* 获取类对象有3种方式
  \1. Class.forName 通过类名字获取类对象
  \2. Hero.class 通过类的静态属性获取类对象
  \3. new Hero().getClass() 通过对象的方法获取类对象 返回的时对象类型（rountime type）奥，不是引用类型
* 正常的属性在实例化的时候会被初始化。正常属性初始化有三个地方，声明处，代码块处，构造器处。
* 类属性在被获取类对象的时候会被初始化，而且只会执行一次（如果多次获取类对象，只会执行一次）。（除了直接使用 Class c = Hero.class 这种方式，这种方式不会导致静态属性被初始化）

### 创建对象

* 传统创建对象的方法是new
* 有了类对象，可以用反射的方式创建对象
* 反射机制，会先拿到Hero的“类对象”,然后通过类对象获取“构造器对象”再通过构造器对象创建一个对象

```java
package reflection;
import java.lang.reflect.Constructor;
import charactor.Hero;
public class TestReflection {
 
    public static void main(String[] args) {
    	//传统的使用new的方式创建对象
        Hero h1 =new Hero();
        h1.name = "teemo";
        System.out.println(h1);
         
        try {
        	//使用反射的方式创建对象
            String className = "charactor.Hero";
            //类对象
            Class pClass=Class.forName(className);
            //构造器
            Constructor c= pClass.getConstructor();
            //通过构造器实例化
            Hero h2= (Hero) c.newInstance();
            h2.name="gareen";
            System.out.println(h2);
        } catch (Exception e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
    }
}

```

思考一件事情，在写java代码的时候，一定要给出变量的数据类型，但是却希望声明一样类型的变量，表现处不同的状态，这时就有了多态的思想，利用了向上类型转换。这是实现的时有子夫类关系的类，表现出来的不同状态，但是如果我希望没有子父类关系，我也能在不需要重新编译的情况下（不修改原本代码）表现出不同状态，这时候就可以反射机制了，不在代码中声明变量，给出数据类型，而是把数据类型信息放到配置文件里，然后再代码中通过反射机制得来该类型的对象。

* 当获取到类对象后，就可以通过这个类对象的方法获得类的方法，属性和构造器