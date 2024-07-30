# java

## 方法

1. 什么是可变长参数？

   从java5开始，java支持可变长参数。可变长参数是指调用方法时允许传入不定长度的参数，可以是零个也可以是多个。

   遇到方法重载时，会优先匹配固定参数的方法。

2. 重载和重写有什么区别？

   重载：

   * 发生在编译期，是同一个类中多个同名方法根据不同的传参来执行不同的逻辑处理。

   * 方法名必须相同，参数类型、个数、顺序不同，方法返回值和访问修饰符可以不同。

   * Java 允许重载任何方法， 而不只是构造器方法。

   重写：

   * 发生在运行期，是子类对父类允许方法的方法的实现过程进行重新编写。

   * 方法名，参数类别必须相同，子类方法返回值类型应该比父类方法返回值类型**更小或者相等**，抛出的异常范围**小于等于**父类，访问修饰符范围**大于等于**父类。如果父类方法访问修饰符为private/final/static则子类不能重写该方法，但是被static修饰的方法能够被再次声明。“两同两小一大”

   * 构造方法无法被重写。

3. 静态方法和实例方法有何不同？
   1. 调用方式不同。在外部调用静态方法时，可以使用类名.方法名的方式，也可以使用对象.方法名的方式，而调用实例方法仅可以使用对象.方法名的方式，因为实例方法是属于某个对象的，而实例方法不属于某个方法而是属于这个类。
   2. 访问类成员是否存在限制。静态方法仅可以访问静态方法和静态成员变量，不可以访问实例成员，而实例方法不存在这个限制。

4. 方法有哪几种类型？什么是方法返回值？

   方法返回值：某个方法体中代码执行后产生的结果！返回值的作用是接收结果，使得它可以用于其他的操作。

   **无参数无返回值的方法** **有参数无返回值的方法** **有返回值无参数的方法** **有返回值有参数的方法**

5. 静态方法为什么不能调用非静态方法？

   1. 静态方法是属于类的，在类加载的时候就分配内存了，可以通过类名直接访问。而非静态成员属于实例对象，只有在对象实例化之后才存在，需要通过类实例去访问。
   2. 在类的非静态方法还不存在时静态方法就已经存在了，此时调用在内存中还不存在的非静态方法，属于非法操作。



## 变量

## 基本数据类型

## 基本语法

## 面向对象基础

1. 面向对象的三大特征？

   * 继承性

     继承是使用已存在的类的定义作为基础建立新类的技术，新类的定义可以增加新的数据或新的功能，也可以使用父类的功能，但不能选择性的继承父类。子类可以使用父类所有的属性和方法包括私有属性和私用方法，但是父类中的私有属性和私有方法子类是**无法访问的，只是拥有**。

   * 封装性

     封装是把对象的状态信息隐藏到对象内部，不允许外部直接访问对象的内部信息。但是提供一些可以被外界访问的方法来操作属性。

   * 多态性

     表示一个对象具有多种的状态，具体表现为父类的引用指向子类的实例。

2. 接口和抽象类有什么共同点和区别？

   共同点

   * 实例化。接口和抽象类都不能直接实例化，只能在被实现或继承后才能创建具体的对象。
   * 抽象方法。接口和抽象类都包含抽象方法，抽象方法用Abstract关键字修饰，必须被实现类或子类实现。

   区别

   * 设计目的：接口主要用于对类的行为进行约束，一个类实现了该接口就表明该类具备了这种行为。抽象类主要用于代码的复用，强调的是所属关系。
   * 继承和实现：一个类只能继承一个类，可以实现多个接口，一个接口也可以实现多个接口。
   * 成员变量：接口中的成员变量只能是public static final类型的，不可以被修改且**必须有初始值**。抽象类的成员变量可以被任意修饰符修饰（private，protected，public），可以在子类中被重新定义或赋值。
   * 方法：
     * 在java8之前，接口中的方法默认是public Abstract，也就是只能有方法声明。java8，可以在接口中定义default方法和static方法。java9，接口可以定义private方法。
     * 抽象类可以包含抽象方法和非抽象方法。

3. 深拷贝和浅拷贝区别了解吗？什么是引用拷贝？

   * 浅拷贝：浅拷贝会在堆上创建一个新的对象（区别于引用拷贝），不过，如果原对象内部的属性是引用数据类型，浅拷贝会直接复制其引用地址。
   * 深拷贝：深拷贝会完全复制整个对象，包括这个对象所包含的内部对象。
   * 引用拷贝：复制对象的引用地址，并不在堆上开辟新的内存。

## Object

1. Object类常见方法有哪些？

   主要有 equals，hashCode，wait，notify，notifyAll，toString

2. ==和equals()的区别？

   ==

   * 比较基本数据类型是比较值，不比较数据类型，整形和浮点型也可能相等。
   * 比较引用数据类型是比较对象内存地址

   equels()

   * 不能比较基本数据类型，仅能比较引用数据类型。
   * equels()方法存在于Object类中，Object类中的equals方法，是比较的对象内存对象地址，等价于==。String类重写了equals方法，比较的是字符串是否相同。

3. hashCode有什么用？

   hashCode用来计算对象的哈希码（int整数）。这个哈希码的作用是确定该对象在哈希表中的索引位置。

   3.1 hashCode和equals有什么千丝万缕的关系？

   在向哈希表如HashSet和HashMap中添加对象时，第一步需要判断该对象是否已经在哈希表中存在。如果存在则覆盖添加，否则需要添加。

   判断的方法是：首先使用hashCode方法计算对象的哈希值，如果哈希值相同，则表明这两个对象有相同的可能性（因为存在哈希碰撞现象），进一步的在使用equals方法判断两个对象是否真的相同，如果相同，则覆盖添加，否则需要添加，而这是发生哈希碰撞了如何添加？可使用拉链法。

   这种先使用hashCode再使用equals的判断方法大大缩小了查找方法。

## String

1. String，StringBuffer，StringBuilder的区别？
   * 可变性。String对象是不可变的。StringBuffer和StringBuilder是可变的。他们两个都基础AbstractStringBuilder类，在AbstractStringBuilder中也是使用字符数组保存字符串，不过没有final/private关键字修饰。AbstractStringBuilder也提供了很多修改字符串的方法比如append方法。
   * 线程安全性。String对象线程安全，StringBuffer线程安全，因为它对方法加了同步锁。StringBuilder线程不安全，没有对方法加同步锁。
   * 性能。每次对String对象进行改变的时候，都会生成一个新的String对象，并将指针指向新的String对象。StringBuilder和StringBuffer在修改对象的时候会在原有的对象上改变，并且不修改对象引用。相同情况下使用StringBuilder相比使用StingBufffer仅能获得10%-15%左右的性能提升，却要冒很多线程不安全的风险。

## 异常

## 反射

## 注解

## 泛型

## SPI

## 序列化和反序列化

## I/O

## 语法糖

# 集合

1. 说说List，Set，Queue，Map四者的区别？

   List：存储的元素是有序的，可重复

   Set：存储元素不可重复

   Queue：按特定的排队规则来确定先后顺序，存储元素是有序的，可重复的

   Map：使用键值对存储，key是无序的、不可重复的，value是无序的可重复的

2. 集合框架底层数据结构总结

   List

   * ArrayList：Object[]数组
   * Vector：Object[]数组
   * LinkedList：双向链表。（jdk1.6之前为循环数组，1.7取消了循环数组）

   Set

   * HashSet：它无序，基于HashMap实现的，底层采用HashMap来保存元素。
   * LinkedHashSet：LinkedHashSet是HashSet的子类，其内部通过LinkedHashMap实现的。
   * TreeSet：它有序，红黑树。

   Queue

   * PriorityQueue：Object[]数组实现小顶堆
   * DelayQueue：PriorityQueue
   * ArrayDeque：可扩容动态双向数组。

   Map

   * HashMap：jdk1.8之前，数组+链表。jdk1.8之后，数组+链表/红黑树，当链表长度>8并且数据长度>64转换为红黑树，当链表长度>8并且数据长度<=64时，会对数组扩容。
   * LinkedHashMap：继承自HashMap，所以底层也是数组+链表/红黑树，另外，在上面的结构的基础上，添加了一个双向链表，使得上面的结构可以保持键值对的插入顺序。
   * HashTable：数组+链表组成的，数组是 `Hashtable` 的主体，链表则是主要为了解决哈希冲突而存在的。
   * TreeMap：红黑树

## List

1. ArrayList和Array的区别？

   ArrayList内部基于动态数组实现，比Array静态数组用起来更灵活

   * ArrayList会根据实际存储元素动态地扩容或缩容，而Array被创建之后就不能改变他的长度了
   * ArrayList允许使用泛型来确保类型安全，Array则不可以
   * ArrayList只能存储对象，对于基本数据类型，需要使用其对应的包装类。Array可以直接存储基本数据类型，也可以存储对象。
   * ArrayList支持插入，删除，遍历等常见操作，并且提供了丰富的api操作方法。array只是一个固定长度的数组，只能按照下标访问其中的元素，不具备动态添加，删除的能力
   * ArrayList创建时不需要指定大小，Array创建时必须指定大小。

2. ArrayList可以添加null值吗？

   ArrayList可以存储任意类型的对象，包括null值。

3. ArrayList插入和删除元素的复杂度。

   对于插入：

   - 头部插入：由于需要将所有元素都依次向后移动一个位置，因此时间复杂度是 O(n)。
   - 尾部插入：当 `ArrayList` 的**容量未达到极限**时，往列表末尾插入元素的时间复杂度是 O(1)，因为它只需要在数组末尾添加一个元素即可；当容量已达到极限并且需要扩容时，则需要执行一次 O(n) 的操作将原数组复制到新的更大的数组中，然后再执行 O(1) 的操作添加元素。
   - 指定位置插入：需要将目标位置之后的所有元素都向后移动一个位置，然后再把新元素放入指定位置。这个过程需要移动平均 n/2 个元素，因此时间复杂度为 O(n)。

   对于删除：

   - 头部删除：由于需要将所有元素依次向前移动一个位置，因此时间复杂度是 O(n)。
   - 尾部删除：当删除的元素位于列表末尾时，时间复杂度为 O(1)。
   - 指定位置删除：需要将目标元素之后的所有元素向前移动一个位置以填补被删除的空白位置，因此需要移动平均 n/2 个元素，时间复杂度为 O(n)。

4. LinkedList插入和删除元素的时间复杂度？

   - 头部插入/删除：只需要修改头结点的指针即可完成插入/删除操作，因此时间复杂度为 O(1)。
   - 尾部插入/删除：只需要修改尾结点的指针即可完成插入/删除操作，因此时间复杂度为 O(1)。
   - 指定位置插入/删除：需要先移动到指定位置，再修改指定节点的指针完成插入/删除，因此需要遍历平均 n/2 个元素，时间复杂度为 O(n)。

5. LinkedList为什么不能实现RandomAccess接口？

   RandomAccess接口是一个标记接口，用来表明实现该接口的类支持随机访问。LinkedList底层是双向链表，存储空间不连续，无法使用索引来访问元素，不支持随机访问，

6. ArrayList和LinkedList的区别？

   * 底层数据结构
   * 效率
   * 空间
   * 线程是否安全

   ![image-20240712154603271](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240712154603271.png)

   ![image-20240712154650597](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240712154650597.png)

   每个线程都一份自己的局部变量

   包装类？？？？

7. **说一说ArrayList的扩容机制？**扩容方法是grow（）

   * 往ArrayList里面添加数据（第一次添加数据、添加第2-10次数据、添加第11次数据）

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

     问扩容几次是指grow那个方法调用了几次。初始化是没有调用grow不算扩容

8. **如何实现数组和list之间的转换？**

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

9. 为什么数组索引从0开始呢？假如从1开始不行吗？

   * 因为寻址公式是：数组的首地址+索引乘以存储数组的类型大小，数组索引结合寻址公式可以得到对应元素的内存地址。
   * 如果数组的索引从1开始，寻址公式中，就需要增加一次减法操作，对于CPU来说就多了一次指令，性能不高。

## Set

1. Comparable和Comparator的区别

   Comparable和Comparator都是java中用于自定义排序的接口。

   - `Comparable` 接口实际上是出自`java.lang`包 它有一个 `compareTo(Object obj)`方法用来排序
   - `Comparator`接口实际上是出自 `java.util` 包它有一个`compare(Object obj1, Object obj2)`方法用来排序

   ```java
   
   //自定义排序
   ArrayList<Integer> arrayList = new ArrayList<Integer>();
   arrayList.add(-1);
   arrayList.add(3);
   arrayList.add(3);
   arrayList.add(-5);
   arrayList.add(7);
   arrayList.add(4);
   arrayList.add(-9);
   arrayList.add(-7);
   System.out.println("原始数组:");
   System.out.println(arrayList);
   // void reverse(List list)：反转
   Collections.reverse(arrayList); //Collections工具类的使用
   System.out.println("Collections.reverse(arrayList):");
   System.out.println(arrayList);
   
   // void sort(List list),按自然排序的升序排序
   Collections.sort(arrayList);//Collections工具类的使用，
   System.out.println("Collections.sort(arrayList):");
   System.out.println(arrayList);
   // 定制排序的用法
   Collections.sort(arrayList, new Comparator<Integer>() { //sort重载方法，对arrayList使用特定的方法排序
       @Override
       public int compare(Integer o1, Integer o2) {
           return o2.compareTo(o1); //或者自定义什么情况返回-1，什么情况返回1，什么情况返回1
       }
   });//匿名内部类写法
   System.out.println("定制排序后：");
   System.out.println(arrayList);
   ```



​	

```java
//Integer类实现Comparable接口，重写了compareTo接口。
public int compareTo(Integer anotherInteger) {
    return compare(this.value, anotherInteger.value); //anotherInteger大返回-1，否则，如果相等返回0，不相等返回1，增序
}
public static int compare(int x, int y) {
    return (x < y) ? -1 : ((x == y) ? 0 : 1);
}
//Collections中的方法源码
public static <T> void sort(List<T> list, Comparator<? super T> c) {
    list.sort(c);
}
//ArrayList中sort源码
public void sort(Comparator<? super E> c) {
    final int expectedModCount = modCount;
    Arrays.sort((E[]) elementData, 0, size, c);
    if (modCount != expectedModCount)
        throw new ConcurrentModificationException();
    modCount++;
}
```

```java
// person对象没有实现Comparable接口，所以必须实现，这样才不会出错，才可以使treemap中的数据按顺序排列
// 前面一个例子的String类已经默认实现了Comparable接口，详细可以查看String类的API文档，另外其他
// 像Integer类等都已经实现了Comparable接口，所以不需要另外实现了
public  class Person implements Comparable<Person> {
    private String name;
    private int age;

    public Person(String name, int age) {
        super();
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    /**
     * T重写compareTo方法实现按年龄来排序
     */
    @Override
    public int compareTo(Person o) {
        if (this.age > o.getAge()) {
            return 1;
        }
        if (this.age < o.getAge()) {
            return -1;
        }
        return 0;
    }
    
    
    
        public static void main(String[] args) {
        TreeMap<Person, String> pdata = new TreeMap<Person, String>();
        pdata.put(new Person("张三", 30), "zhangsan");
        pdata.put(new Person("李四", 20), "lisi");
        pdata.put(new Person("王五", 10), "wangwu");
        pdata.put(new Person("小红", 5), "xiaohong");
        // 得到key的值的同时得到key所对应的值
        Set<Person> keys = pdata.keySet();
        for (Person key : keys) {
            System.out.println(key.getAge() + "-" + key.getName());

        }
    }
    
}
```



2. 比较HashSet、LinkedHashSet和TreeSet三种的异同？
   * 都实现set接口，都能保证元素唯一，并且都不是线程安全。
   * `HashSet`、`LinkedHashSet` 和 `TreeSet` 的主要区别在于底层数据结构不同。`HashSet` 的底层数据结构是哈希表（基于 `HashMap` 实现）。`LinkedHashSet` 的底层数据结构是链表和哈希表，元素的插入和取出顺序满足 FIFO。`TreeSet` 底层数据结构是红黑树，元素是有序的，排序的方式有自然排序和定制排序。
   * 底层数据结构不同又导致这三者的应用场景不同。`HashSet` 用于不需要保证元素插入和取出顺序的场景，`LinkedHashSet` 用于保证元素的插入和取出顺序满足 FIFO 的场景，`TreeSet` 用于支持对元素自定义排序规则的场景。

## Queue

## Map

1. 说一下HashMap的实现原理？五颗星出现频率

   * HashMap的数据结构：底层使hash表数据结构，即数组和链表或红黑树
   * 当我们往HashMap中put元素时，利用key的hashCode重新hash计算出当前元素在数组中的下标
   * 存储时，如果出现hash值相同的key，此时有两种情况：
     * 如果key相同，则覆盖原始值；
     * 如果key不同（出现冲突），则将当前的key-value放入链表或红黑树中。（链表长度大于8且数组长度大于64转换为红黑树）
   * 获取时，直接找到hash值对应的下标，在进一步判断key是否相同，从而找到对应值。

   ```java
   //计算出当前元素在数组中的下标的源码
   (n - 1) & hash
       //n是容器的容量，容量一定为2的幂次方，所有n的二进制中只有一个1，后面全是0.再-1后，变成全1。与hash值做与运算，则hash中的1变1,0变0.其实就是把hash前面多的哪些置为零了。
       //比如 n=16，n-1 二进制为 
       // n-1 二进制为    00000000000000000000000000000000 1111
       // hash二进制为    10110100110000110010001110000111 1011
       //&后			 00000000000000000000000000000000 1011 就是取余了
   ```

   

2. HashMap的jdk1.7和jdk1.8有什么区别？五颗星出现频率

   * JDK1.8之前采用的是拉链法。拉链法：将链表和数组相结合。也就是说创建一个链表数组，数组中每一格就是一个链表。若遇到哈希冲突。则将冲突的值加到链表中即可。

   * jdk1.8在解决哈希冲突时有了较大的变化，当链表长度大于阈值（默认为8）时并且数组长度达到64时，将链表转化为红黑树，以减少搜索时间。扩容resize()时，红黑树拆分成的树的节点数小于等于临界值6个，则退化成链表。

   * 获取哈希值的方法有变化。

     ```java
     //1.8 HashMap的hash方法
     static final int hash(Object key) {
           int h;
           // key.hashCode()：返回散列值也就是hashcode
           // ^：按位异或
           // >>>:无符号右移，忽略符号位，空位都以0补齐
           return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);//前16为不变，后16位变成前16位与后16为的异或
       }
     //1.7 HashMap的hash方法
       static int hash(int h) {
         // This function ensures that hashCodes that differ only by
         // constant multiples at each bit position have a bounded
         // number of collisions (approximately 8 at default load factor).
     
         h ^= (h >>> 20) ^ (h >>> 12);
         return h ^ (h >>> 7) ^ (h >>> 4);
     }
     ```

     

3. HashMap的put方法的具体流程？五颗星出现频率 涉及到**扩容**和**变红黑树**两个事情。扩容的时机？变红黑树的时机？扩容后怎么复制到新数组？

   ![image-20240714210548292](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240714210548292.png)

1. 讲一讲HashMap的扩容机制？**扩容方法是resize()**

   ![HashMap扩容操作](C:\Users\DELL\Pictures\Screenshots\HashMap扩容操作.png)

   

   ```java
   //HashMap 存储元素的变量
   transient Node<K,V>[] table;
   ```

2. HashMap的寻址算法？四颗星出现频率

   * 计算对象的hashCode()
   * 再进行调用hash()方法进行二次哈希，hashcode值右移16位再异或运算，让哈希分布均匀
   * 最后(capacity-1)&hash得到索引

3. 为何HashMap的数组长度一定是2的次幂？四颗星出现频率

   * 计算索引是效率更高：如果是2的n次幂可以使用位与运算代替取模
   * 扩容时重新计算索引效率更高：hash&oldCap == 0的元素留在原来位置。负责新位置 = 旧位置 + oldCap

4. hashmap在1.7情况下的多线程死循环问题？

   ![image-20240714221704582](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240714221704582.png)

   

5. ConcurrentHashMap？？？？



1. HashMap和HashTable的区别

   * 线程是否安全。HashMap线程不安全，HashTable线程安全，方法基本都用synchornized修饰。
   * 效率。因为线程安全的原因，HashMap的效率要比HashTable高一些。
   * 对null key和null value的支持。HashMap能存储null的key和null的value，但null作为键只能有一个，null作为值可以有多个；HashTable不支持null的key和null的值，否则会抛出NullPointerException。
   * 初始容量大小和每次扩充容量大小的不同。 ① 创建时如果不指定容量初始值，`Hashtable` 默认的初始大小为 11，之后每次扩充，容量变为原来的 2n+1。`HashMap` 默认的初始化大小为 16。之后每次扩充，容量变为原来的 2 倍。② 创建时如果给定了容量初始值，那么 `Hashtable` 会直接使用你给定的大小，而 `HashMap` 会将其扩充为 2 的幂次方大小。
   * 底层数据结构。JDK1.8 以后的 `HashMap` 在解决哈希冲突时有了较大的变化，当链表长度大于阈值（默认为 8）时，将链表转化为红黑树（将链表转换成红黑树前会判断，如果当前数组的长度小于 64，那么会选择先进行数组扩容，而不是转换为红黑树），以减少搜索时间（后文中我会结合源码对这一过程进行分析）。`Hashtable` 没有这样的机制。
   * 哈希函数的实现。`HashMap` 对哈希值进行了**高位和低位的混合扰动处理**以减少冲突，而 `Hashtable` 直接使用键的 `hashCode()` 值。

2. HashMap和HashSet区别

   ![image-20240729160645828](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240729160645828.png)

   

3. HashSet如何检查重复？

   ```java
   //HashMap的put方法，会返回value值。value==null表示添加的元素之前不存在，value=对象引用表示添加的元素之前存在。
   public V put(K key, V value) {
   	return putVal(hash(key), key, value, false, true);
   }
   //hashSet的add方法，返回boolean类型值，返回true表示，添加的元素之前不存在，false表示添加的元素之前存在
   public boolean add(E e) {
       return map.put(e, PRESENT)==null;
   }
   ```

   在 JDK1.8 中，实际上无论`HashSet`中是否已经存在了某元素，`HashSet`都会直接插入，只是会在`add()`方法的返回值处告诉我们插入前是否存在相同元素。



# 并发



