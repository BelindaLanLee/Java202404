# Java 概述

Java 是 IT 研发类招聘需求量最大的语言之一

为什么 Java 需求量最大？

Java 主要做 Web 端服务器开发

99.9 % 项目都是基于 Web

Web 服务器端 Java 是第一语言

C#、PHP、Java、Python、Go

生态的区别，Java 的生态其他语言无法对抗

基于 Java 衍生出来的各种框架、服务、组件......

Spring 框架

# 开发版本

JDK 21

企业主流的 JDK 仍然是 8

分布式事务 阿里的 seata ，只支持 JDK 8

Spring Boot 2.X

MySQL 8

Redis 缓存数据库 NoSQL

Spring Cloud 微服务

Java 基础 打基础 单机

JavaWeb 用 Java 做 Web 开发，Servlet ，Java EE

框架

Spring 全家桶

Spring、SSM、MyBatis Plus、Shiro、Spring Boot、Spring Cloud

实操 做项目

面试题 简历

# JDK

JDK：Java Development Kit Java 开发工具包

JRE：Java Runtime Environment Java 运行环境

只需要运行 Java 项目，安装 JRE

需要开发 Java 项目，必须安装 JDK，包含 JRE

Java 不是解释型语言

HTML JS

Java 需要先编译成字节码文件，再通过 JVM（Java 虚拟机）对字节码文件进行进一步的解析，生成机器码，底层操作系统才能识别机器码进行程序的运行

Java 为什么先需要编译？

为了实现 Java 的一大特性，一次编译，到处运行 跨平台

同一套代码可以在不同的操作系统上运行

如何实现跨平台？

通过编译的方式

Java 源代码编译成字节码文件

字节码文件分别放到不同的操作系统中，由 JVM 将它们各自解析成对应操作系统的机器码进行执行

Test.java ->Test.class ->运行

Java 源代码编译成字节码的命令是什么？

```
javac Test.java
```

Java 字节码运行的命令是什么？

```
java Test
```

都可以省略，由开发工具帮助我们来完成

# 变量

为什么要使用变量？变量是为了解决什么问题？

数据存储地址的问题

数据都是在内存中进行存储的，存在一个问题？

程序会随机分配内存区域

内存地址是 16 进制的数据，随机分配，地址很记住

如何解决这个问题？

使用变量

变量就是为了解决内存地址很难记忆的问题

相当于给内存地址起了一个别名，取数据的时候直接通过变量名取即可，不需要再通过内存地址来取数据了

# 变量

1、声明变量的数据类型和变量名

Java 中有多少种数据类型？

Java 有两大类数据类型

- 基本数据类型（不是对象，可以通过包装类将它改造成对象，8 种）
- 引用数据类型（对象，JDK 类库、框架类库、开发者自定义类，无数种）

Java 开发中使用的对象共有三种来源

- JDK 类库 String Date Integer
- 第三方类库 框架 Application SpringBootApplication DispatcherServlet
- 自定义的类

2、变量的值

```java
int i = 1;
String str = new String("Hello World");
```

基本数据类型和引用类型在内存中的区别

所有的变量都是存储在栈内存中的，无论是基本数据类型还是引用类型，基本数据类型和引用数据类型的区别在于是否使用了堆内存

基本数据类型不需要使用堆内存，直接将变量的值存入栈内存

引用类型需要使用堆内存，对象是创建在堆内存中的，将堆内存的地址引用赋值给变量

# 基本数据类型

数值类型：byte、short、int、long、float、double

非数值类型：char、boolean

byte 空间 1 个字节

byte KB MB GB TB

1KB = 1024 byte

1MB = 1024 KB

1GB = 1024 MB

1TB = 1024 GB

1 个字节 = 8 位二进制

short 空间 2 个字节

int 空间 4 个字节

long 空间 8 个字节

float 空间 4 个字节

double 空间 8 个字节

char 空间 2 个字节

boolean 空间 几个字节？

1/8 个字节 1 位 1bit

bit

1 byte = 8 bit

0/1

boolean 表示逻辑运算的结果，真或者假

0 表示假 false

1 表示真 true

# 数据类型的转换

1、基本数据类型的转换

- 自动转换
- 强制转换

尽量不使用强制类型转换，因为存在数据精度损失的隐患

```java
double num = 10.5;
int i = (int)num;
```

byte -> short -> int -> long -> float -> double

从小向大转

2、引用数据类型的转换

前提是需要转换的两种数据类型必须有继承的关系
强制类型转换的前提是必须拥有父类对象

- 自动转换
- 强制转换

```java
public class Test {
    public static void main(String[] args) {
        Student student = new Student();
        Person person = new Person();
        //自动类型转换
        person = student;
        //强制类转转换
        student = (Student) person;
    }
}
```

实现类和接口也可以进行类型转换，因为接口和实现类本质上也是父类和子类的继承关系

接口就是父类，实现类就是子类

````java
public class Test {
   public static void main(String[] args) {
    MyImplement myImplement = new MyImplement();
    MyInterface myInterface = myImplement; //不会报错，可以进行类型转换
   }
}

接口是由抽象类演变而来的

抽象类：一个类中包含抽象方法就是抽象类

抽象父类

```java
public abstract class Test1 { //抽象类
    public abstract void test(); //抽象方法
}
````

非抽象子类

```java
public class Test2 extends Test1 { //继承
    @Override
    public void test() {

    }
}
```

抽象父类可以优化成接口，也就是说是由抽象类演变而来的
（abstract class -> interface）

```java
public interface Test1 {
    public abstract void test();
}
```

非抽象子类变成实现类
(extends -> implements)

```java
public class Test2 implements Test1 {
    @Override
    public void test() {

    }
}
```

````java
public class Test{
    public static void main(String[] args) {
        MyImplements myImplement = new MyImplement();
        MyInterface myInterface = myImplement; //实现类赋值给接口类型，OK
        MyImplements myImplement1 = new MyInterface();//接口转为实现类，NG
    }
}

接口不能进行强制类型转换，因为接口比较特殊，无法实例化即new对象。而普通父类是可以new的。

接口和抽象类的区别

- 关键字不同
- 抽象类中可以包含非抽象方法，接口中全部是抽象方法
- 具体化的方式不同，接口通过实现类来具体化，抽象类通过继承具体化
- 抽象类只能单继承，接口多实现

父类中的构造器，在创建子类对象的时候会自动调用，
非抽象类，调用构造器来创建对象，会创建父类对象；
抽象类，调用父类构造器，但不会创建对象。
有创建对象的时候，一定会调用构造器，但是调用构造器时，不一定会创建对象。（类似数据库里面的触发trigger）

# 运算符

算术运算符 + - * /（加减乘除）

逻辑运算符 >  <  ==  !=
逻辑运算符只能用于 boolean 类型的数据运算，判断 boolean 数据之间的逻辑关系，包括与、或、非

与：&&（短路与）、&

或：||（短路或）、|

非：! (取反)

与：A 和 B，当A 和 B 都为 true，结果为 true，否则为 false

或：A 和 B，当其中有一个为 true，结果为 true，否则为 false

非：取反

与和短路与的区别，运算逻辑和结果完全一致，短路与的性能更高
或和短路或的区别，运算逻辑和结果完全一致，短路或的性能更高

表达式 A & 表达式 B
同时运算表达式 A 和表达式 B，对结果进行逻辑与运算

表达式 A && 表达式 B
优先运算表达式 A，如果结果为 false，则不需要运算表达式 B

表达式 A | 表达式 B
同时运算表达式 A 和表达式 B，对结果进行逻辑与运算

表达式 A || 表达式 B
优先运算表达式 A，如果结果为 true，则不需要运算表达式 B

```java
public class Test {
    public static void main(String[] args) {
        int num1 = 10;
        int num2 = 11;
        System.out.println((num1++ == num2) && (++num1 == num2));
        System.out.println(num1);
    }
}
````

# 运算符

位运算符

对表达式以二进制为单位进行运算，将数据全部转换成二进制再进行运算

十进制和二进制的转换

十进制转二进制：目标数除以二，若能除尽，该位记作 0，若除不尽，则该位记作 1，再对商继续除以二，以此类推，直到商为 0。从下往上写就是换成二进制后的结果。

10 转为二进制 01010

17 转为二进制 10001

二进制转十进制：从目标数最右侧开始，本位的数值乘以本位的权重（2 的第几位的位数减一次方），把每一位的乘积相加就是十进制的结果。

&（按位与）、|（按位或）、^（按位异或）、<<（左移）、>>（右移）（只有整数数值才有位移运算，float 和 double 没有位移运算。）

A & B：每一位的数字一一对应，若都为 1，则该位记作 1，否则为 0。位数不一致时，前位补零，不影响数值的大小。
eg.
10 -> 01010
17 -> 10001
结果是：00000

A | B：每一位的数字一一对应，只要有 1 个 1，则该位记作 1，否则为 0。位数不一致时，前位补零，不影响数值的大小。
eg.
10 -> 01010
17 -> 10001
结果是：11011

A ^ B：每一位的数字一一对应，相同记作 0，不同记作 1。
eg.
10 -> 01010
17 -> 10001
结果是：11011

A << B：A * 2 的 B 次方，
2 << 3 2*2 的 3 次方 = 16

A >> B：A 除以 2 的 B 次方，
2 >> 3 2/2 的 3 次方 = 0

10：1010

5：101

3：11

1001 -》9

运算符的优先级：
位运算符（位与，位或，位异或，位移）>逻辑运算符（与或非）>算术运算符（+ - \* /）

# 流程控制

if-else switch-case for while do-while foreach

if-else 和 switch-case 都是进行流程控制也就是逻辑控制的分支语法，是构建基本逻辑的基础骨架。
区别：
1、if-else 可以进行等值判断，也可以进行逻辑判断，switch-case 只能进行等值判断；
2、switch-case 代码结构更清晰易懂，if-else 结构相对不是特别清晰。

4 种循环
for、while、do-while、foreach（针对集合遍历的一种优化循环）也叫增强型 for 循环

循环四要素（执行的顺序也是同样的：初始化循环变量->满足循环条件->执行循环体->更新循环变量，一直重复这个过程，直到循环条件不成立结束循环）：

- 初始化循环变量
- 循环条件
- 循环体
- 更新循环变量

```java
public class Test {
    public static void main(String[] args) {
        for(int i = 0; i < 100; i++){
          System.out.println(i);
        }

    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        int i = 0;//赋值运算可以单独写出来,ok
        for(; i < 100; i++){
          System.out.println(i);
        }

    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        int i = 0;//赋值运算可以单独写出来
        System.out.println (i < 100);//条件句写在循环外，语法不报错
        for(;; i++){
          System.out.println(i);
        }

    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        int i = 0;//赋值运算可以单独写出来
        System.out.println (i < 100);//条件句写在循环外，语法不报错
        i++；//循环变量更新的句子写在循环外，语法不报错，但是本循环是死循环。
        for(;;){
          System.out.println(i);
        }

    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        for(;;){ //执行结果是true,0, true,0...的死循环
          int i = 0;
          System.out.println (i < 100);
          System.out.println(i);
          i++；
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        int i = 0;
        for(;i < 100;){//结果和标准版的写法一致
          System.out.println(i);
          i++；
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        int i = 0;
        while (i < 100) {//先判断循环条件，再执行循环体后，更新变量
            System.out.println(i);
            i++;//必须写在循环体内，若写在循环体外，则会变成死循环。
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        int i = 0;
        do{//第一次先执行循环，更新变量，再去判断条件。
            System.out.println(i);
            i++;
        }while (i < 100);
    }
}
```

while 和 do-while 的区别
while 需要先判断循环条件，再执行循环体
do-while 第一次不需要判断循环条件，直接执行循环体，第二次开始判断循环条件
do-while 至少会执行一次，while 有可能一次都不执行

```java
import java.util.Arrays;
import java.util.List;

public class Test {
    public static void main(String[] args) {
        List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }
        System.out.println("*******************************");
        for (Integer i : list) {
            System.out.println(i);
        }
    }
}
```

循环结束

- 循环逻辑结束
- 循环过程中抛出异常
- 使用 break 关键字中断循环
- 使用 continue 关键字中断循环

break 会结束整个循环，continue 只结束当前循环，继续执行下一次循环

```java
import java.util.Arrays;
import java.util.List;

public class Test {
    public static void main(String[] args) {
        List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

        for (int i = 0; i < list.size(); i++) {
        //if(i == 5) break;//break结束循环，输出结果：0 1 2 3 4
        //if(i == 5) continue;//continue跳出当前循环，执行下一次循环输出结果： 1 2 3 4 5 7 8 9 10
            System.out.println(list.get(i));
        }
        System.out.println("*******************************");
        for (Integer i : list) {
            System.out.println(i);
        }
    }
}
```

# 数组

数组由 4 种基本元素构成

- 数组名称(两种写法都 OK)
- 数组元素
- 元素下标
- 数据类型

  int[] array ={1, 2, 3, 4, 5, 6};
  int array[] ={1, 2, 3, 4, 5, 6};
  array.sout 的结果是[I@1b6d3586
  [表示数组
  I 表示·integer,意思是数组里面存储的数据类型是整型
  后面是对象的地址

对象默认的输出方式
Java 输出对象的时候，默认调用对象的 toString 方法，将结果以字符串的形式进行输出

toString 从何而来？-> 来自于 Object 父类,每个类都默认继承了 Object
Java 会有一个根节点，所有的类都是由这个根节点衍生出来的，Java 所有类都有一个默认的父类：Object
Java 类都会有一些共性：如 输出对象的时候，都需要调用 toString 方法；每个对象都可以进行比较，如两个对象是否相等；对象的哈希码

多态、代码复用（即重复使用，重复执行）

都会有共性

打印对象、对象比较、对象的哈希码

![image-20240320215913177](C:\Users\ningn\AppData\Roaming\Typora\typora-user-images\image-20240320215913177.png)

```java
import java.util.Arrays;

public class Test {
    public static void main(String[] args) {
        //String[] array = {"a",1,"c","d","e","f"}; 会报错，因为定义的变量类型是string
        //Object[] array = {"a",1,"c","d","e","f"}; （*多态的概念）就不会报错了，任何类型的数据都可以存放进来，因为Object类是Java所有类的祖先即顶级父类
        String[] array = {"a","b","c","d","e","f"};//定义的左侧一定是在栈内存里面，存储的是右侧一串数据的第一个数据的地址，即首地址；右侧是在堆内存里面的一个连续的空间，方便查询。
        System.out.println(array);//输出的是对象存放的地址

        //遍历数组
        //for
        for (int i = 0; i < array.length; i++) {
            System.out.println(array[i]);//利用数组的下标遍历数组
        }
        System.out.println("********************");

        //while
        int l = 0;//定义变量
        while (l < array.length){
            System.out.println(array[l]);//利用数组的下标遍历数组
            l++;
        }
        System.out.println("*************************");

        //do-while
        int m = 0;//定义变量
        do {
            System.out.println(array[m]);//利用数组的下标遍历数组
            m++;
        } while (m < array.length);
        System.out.println("*********************");

        //foreach循环/增强for循环
        for (String str : array) {
            System.out.println(str);
        }
        System.out.println("***********************");

        //直接调用工具类
        System.out.println(Arrays.toString(array));
    }
}
```

# 数组

为什么数组下标都是从 0 开始的？

提高检索速度，查询取出数据更快
为什么从 0 开始可以提高检索速度呢？
和数组的内存模型相关，参考内存寻址公式

数组常见的异常：数组下标越界，ArrayIndexOutOfBoundsException
异常：Java 用来描述错误的一种机制，告诉我们出了什么类型的问题，但是提供不了解决方法

## 数组常用操作以及方法

- 求数组的最大值
- 求数组的最小值
- 在数组的指定位置插入一个数据
- 数组排序

```java
import java.util.Arrays;

public class Test {
    public static void main(String[] args) {
        int[] array = {100,96,93,87,73,62};
        //求最大值
        int max = array[0];
        for (int i = 1; i < array.length; i++) {//i=0开始的话，会多进行一次没必要的运算，从第二位开始比较会效率更高。
            if(array[i] > max){
                max = array[i];
            }
        }
        System.out.println(max);

        //求最小值
        int min = array[0];
        for (int i = 1; i < array.length; i++) {//i=0开始的话，会多进行一次运算，从第二位开始比较会效率更高。
            if(array[i] < min){
                min = array[i];
            }
        }
        System.out.println(min);

        //在指定位置插入元素
        //将 83 插入到下标为 3 的位置
        /**
         * 1、创建长度+1的新数组
         * 2、导入数据
         * 3、插入新数据
         */

        //数组的长度是不能修改的，因此插入数据的时候需要新创建一个数组。
        int[] array2 = new int[array.length+1];//新数组的长度=原数组的长度+1
        for (int i = 0; i < 3; i++) {
            array2[i] = array[i];
        }
        for (int i = 4; i < array2.length; i++){//疑问？ 为什么不先插入新数据后再对4位以后得数据进行赋值呢？新数据的插入顺序有什么注意事项吗？
            array2[i] = array[i-1];
        }
        //插入新数据
        array2[3] = 83;
        System.out.println("插入之前的数组：" + Arrays.toString(array));
        System.out.println("插入之后的数组：" + Arrays.toString(array2));

        //数组排序
        //将数组升序排列

        System.out.println(Arrays.toString(array));//升序之前输出一次

        //冒泡排序 双层for循环
        for (int j = 0; j < array.length - 1; j++) {
            for (int i = 0; i < array.length-1-j; i++) {
                if(array[i] > array[i+1]){
                    int temp = array[i];
                    array[i] = array[i+1];
                    array[i+1] = temp;
                }
            }
        }


//        for (int i = 0; i < array.length-1; i++) {
//            if(array[i] > array[i+1]){
//                int temp = array[i];
//                array[i] = array[i+1];
//                array[i+1] = temp;
//            }
//        }
//
//
//
//        for (int i = 0; i < array.length-2; i++) {
//            if(array[i] > array[i+1]){
//                int temp = array[i];
//                array[i] = array[i+1];
//                array[i+1] = temp;
//            }
//        }
//
//
//        for (int i = 0; i < array.length-3; i++) {
//            if(array[i] > array[i+1]){
//                int temp = array[i];
//                array[i] = array[i+1];
//                array[i+1] = temp;
//            }
//        }
//
//
//        for (int i = 0; i < array.length-4; i++) {
//            if(array[i] > array[i+1]){
//                int temp = array[i];
//                array[i] = array[i+1];
//                array[i+1] = temp;
//            }
//        }
//
//
//        for (int i = 0; i < array.length-5; i++) {
//            if(array[i] > array[i+1]){
//                int temp = array[i];
//                array[i] = array[i+1];
//                array[i+1] = temp;
//            }
//        }

        System.out.println(Arrays.toString(array));


        for (int j = 0; j < array.length - 1; j++) {
            for (int i = 0; i < array.length-1-j; i++) {
                if(array[i] < array[i+1]){
                    int temp = array[i];
                    array[i] = array[i+1];
                    array[i+1] = temp;
                }
            }
        }

        System.out.println(Arrays.toString(array));
    }
}
```

Arrays 工具类常用方法

```java
import java.util.Arrays;

public class Test {
    public static void main(String[] args) {//实用工具类实现排序
        int[] array1 = {73,80,62,93,96,87};
        int[] array2 = {73,80,62,93,96,87};
        int[] array3 = {66,55,44,33,22};
        System.out.println(Arrays.equals(array1, array2));//两个数组是否相等：数组长度是否一致，数组里面的数据是否也完全一致。
        Arrays.sort(array3);//数组的工具类默认升序排序，并无降序排序
        System.out.println(Arrays.toString(array3));//排序后输出
        Arrays.fill(array2, 66);//填充数组：将数组里面的数据全部填充为。。。
        System.out.println(Arrays.toString(array2));
        int[] copyOf = Arrays.copyOf(array3, 10);//复制数组的数据，新数组的长度为10
        System.out.println(Arrays.toString(copyOf));
        Arrays.sort(array1);//升序排列
        System.out.println(Arrays.binarySearch(array1, 87));//二分查找法的默认条件是数据必须进行升序排列。若不先进行升序排序的话，数据位置会乱掉。升序排序之后的位置是4。
    }
}
```

## 二维数组

创建一个数组，保存 6 个货柜中所有的商品，每个货柜有 10 件商品

二维数组就是一个一维数组，该一维数组中存储的值是另一个一维数组。

```java
import java.util.Arrays;

public class Test {
    public static void main(String[] args) {
        int[][] array = {{1,2,3},{4,5,6},{7,8,9}};
        for (int i = 0; i < array.length; i++) {
            for (int i1 = 0; i1 < array[i].length; i1++) {
                System.out.println(array[i][i1]);
            }
        }
    }
}
```

二维数组第一维必须指定长度，第二维可以不指定长度，为什么？
因为第一维数组中存储的值是另外任意一个数组的内存地址，而且这个数组的长度是不确定的，所以不需要指定第二维的长度。
e.g. int[][] array1 = new int[3][];

上中下，每层 6 个格挡，每个格挡的鸡蛋个数是层数\*格挡数，按照此规律使用二维数组来装载所有的鸡蛋并求出总数量。

```java
public class Test {
    public static void main(String[] args) {
        int[][] array = new int[3][6];
        int sum = 0;
        for (int i = 0; i < array.length; i++) {
            System.out.println("--------------第" + (i + 1) + "层货柜----------------");
            for (int j = 0; j < 6; j++) {
                int num = (j+1)*(i+1);
                System.out.println("第" + (j + 1) + "个格挡的鸡蛋个数：" + num);
                sum += num;
            }
        }
        System.out.println("鸡蛋的总数是：" + sum);
    }
}
```

# Java 面向对象

面向对象是一种编程思想
e.g.开车去北京 这件事

面向过程是另外一种编程思想，具体到每一个行为，按顺序一步一步执行，相当于亲力亲为的把每一个步骤都要仔仔细细认认真真的写出来，如：打开车门，坐进车里，打开引擎。。。，更改需求比较麻烦。
面向对象：把关键对象抽象出来，再把抽象出来的关键对象连接起来，更改需求比较容易

北京、车、驾驶员

# 类和对象

面向对象编程最基础的元素就是对象，对象从何而来？通过类来创建的

类 -》对象

类是所有对象的抽象模板即所有对象共有的一些特点抽象出来，如：姓名，学号，性别；对象是类的一个具体实例，如：每一个具体的学生对象

编写的代码都是类，都是写在类里面的，静态资源，程序真正运行时，JVM 虚拟机会加载类，运行类中的代码，从而产生对象。
因此对象的存在是一种瞬时状态，程序执行期间对象是存在的，程序一旦结束——对象就不存在了，而类是一直存在的。

类中包含两部分内容——静态特征+动态特征，用来描述对象的特征

- 静态特征 颜色、重量、编号...
- 动态特征 带有动作执行的操作 走路 跑步

静态特征在类中定义为属性，即成员变量，包含三部分内容：访问权限修饰符、数据类型、属性名
动态特征在类中定义为方法，包含五部分内容：访问权限修饰符、返回值类型、方法名、参数列表、方法体

return 是结束方法的关键字
return 10 结束方法的同时向外返回 10

```java
public class Student {
    //属性的定义包含三部分内容
    //访问权限修饰符、数据类型、属性名
    public int id;
    public String name;

    //方法的定义包含五部分内容
    //访问权限修饰符、返回值类型、方法名、参数列表、方体
    public void test(int i){//void 方法不向外返回任何结果
        if(i == 1){
            System.out.println(123);
            return;//此处有return时，当前方法结束，打印的结果是123；如果没有这return，打印的结果会是 123 456 789
        }
        System.out.println(456);
        System.out.println(789);
        //return;//void无返回值的方法里面，可以写return，return是结束方法的关键字，此时return后没有代码，一旦有返回值会报错
    }

    public int add(int num1,int num2){
        int num3 = num1+num2;
        return num3;
    }
}
```

类是创建对象的，对象是通过构造函数来创建的，因此类中必须有至少一个构造函数，每个类都有一个默认的无参构造函数，但是一旦在类中声明一个有参构造，则默认的无参构造函数会被覆盖而导致无法调用创建对象。

构造函数不需要返回值的定义，方法名必须和类名保持一致，可以有参数列表
构造函数访问权限修饰符，不能写为 private，因为一旦私有化，就没有办法调用它创建对象，这个类就没有任何意义了。因此，只能是 public

无参构造和有参构造的区别？

无参构造只能创建对象，无法给对象的属性赋值

有参构造——参数列表里面有参数，可以连同创建对象 + 属性赋值一起完成
一旦在类中声明一个有参构造，则默认的无参构造函数会被覆盖而导致无法调用创建对象。

```java
public class Student {

    public int id;
    public String name;

    public Student(int id,String name){//有参构造，参数列表里面的参数叫做形式参数，简称：形参
        this.id = id;//若无this关键字，id=id,对于程序来说，id有两个：一个是对象的属性即成员变量，另一个是构造器中的形参，因为赋值动作最近的id在有参构造器中，程序会默认采用就近原则，默认要对构造器中的id形参进行赋值,把自己的值赋给自己。——即 就近赋值，第一种解决方法：成员变量和形参的名字分别取不同的名字，指定把形参的值赋值给成员变量；第二种解决方法：用this关键字，指定把形参值赋值给当前对象的属性/成员变量。
        this.name = name;
    }

    public Student(){//无参构造

    }

    @Override//方法重写
    public String toString() {
        return "Student{" +
                "id=" + id +
                ", name='" + name + '\'' +
                '}';
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        //通过无参构造来创建：既要创建对象还要赋值
        //创建一个id=1，name=张三的对象
        Student student = new Student();
        //System.out.println(student.toString());//toString方法重写之前打印的结果是：对象的类型Student以及内存的地址
        System.out.println(student);//方法重写后打印的结果是：Student{id=0，name='null'}
        student.id = 1;
        student.name = "张三";
        System.out.println(student);


        //通过有参构造来创建：在创建对象的同时进行赋值
        Student student1 = new Student(1, "张三");
        System.out.println(student1);
    }
}
```

# this 关键字

this 用来指代当前类的实例化对象，通过 this 可以调用当前类的属性和方法，比如有参构造中，通过 this 将外部传来的值赋给当前类的实例化对象。

```java
public Student(int id,String name){
    this.id = id;
    this.name = name;
}
```

this 除了可以在类中访问属性，也可以在类中调用方法，类中的方法分为两种：构造方法和普通方法

用 this 调用这两类方法的语法也不相同

-调用构造函数：this(参数列表)调用有参，this()调用无参
在无参构造器中不可以直接写 this(),相当于在构造方法中无限的调用当前的无参构造方法，这样会形成递归场景调用（recursive constructor invocation），无限的循环的去创建对象，在栈内存中会无限的开辟内容空间，会发生内容溢出

但是，在无参构造器中写 this(id:1, name: "张三");是 OK 的，因为相当于在无参中调用有参，相当于创建了两个对象。
在有参构造器中调写 this()也是 OK 的，相当于在有参里面调用无参，由于无参里面没有任何内容，不会对结果产生任何影响，因此也不会报错。

-调用普通方法：this.方法名(参数列表)

不能在普通方法中使用 this 来调用构造函数(即构造器)

```java
public Student(){
    this();//形成递归，无限循环的去创建对象，会报错
}
```

```java
public void test(){
 this();//会报错，因为普通方法调用一定要依赖于对象，因此必须要先有对象才可以调用方法，而不是先有方法，再在方法里面通过调用构造函数this()来创建对象。
 this.test2();//在方法里面调用其他的普通方法OK
 this.test();//在方法里面，调用自己也OK，因为方法是在一个对象里面，不会创建新的对象了，因此内存不会被无线占用，不会报错
}

```

# 方法重载 注解：@override

方法重载是 Java 代码复用的一种重要方式，指的是两个方法之间的一种关系

- 两个方法在同一个类中
- 两个方法的方法名相同
- 两个方法的参数列表不同（个数或数据类型不同）
- 与返回值和访问权限修饰符无关

```四个选项，属于方法重载的是？ -> BC
A public int test(){}
  public int test(){}

B public double test(double a,double b){}
  public double test(){}

C public String test(){}
  public void test(int a){}

D public void test(){}
  public void test2(){}
```

# 成员变量和局部变量

两个变量之间除了数据类型、变量名、变量值不同之外，变量的作用域范围也是不同的。

变量的作用域是指在程序中可以通过变量名来访问该变量的范围

变量的作用域由变量被声明时所在的位置决定

根据不同的作用域可以将变量分为成员变量和局部变量

如果一个变量在方法内声明，则该变量为局部变量
如果一个变量在方法外，在类中声明，则该变量为成员变量即属性

```java
public class Student {
    //成员变量
    public int id;

    public void test(){
        //局部变量
        int num = 1;
    }

}
```

成员变量的作用域是整个类，类中的任意一个方法都可以访问该变量；
局部变量的作用域仅在该方法中，其他方法无法调用该变量

成员变量有默认值，也就是说，在没有进行赋值操作的情况下会有一个默认初始值。
局部变量没有默认值，

# 封装

为什么要有封装？————为了保证数据的安全性

将类的信息全部封装到内部，让外部无法直接访问，以确保数据的安全

1、将属性私有化（private）

2、通过间接的方式即 set 方法让外部访问内部的私有属性

```java
public class Student {
    //成员变量
    private String name; //私有属性只能在类内部进行访问
    private int age;

    public void setAge(int age){
        if(age < 0){//在方法里面加入逻辑设置，用以确保数据的正确性
            System.out.println("年龄不能小于0，已重新赋值");
            this.age = 1;
        } else {
            this.age = age;//调用方法赋值
        }
    }

    public void setName(String name){
        this.name = name;//调用方法赋值
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```

# 封装

## static 关键字

static 表示静态或者全局，可以用来修饰成员变量和成员方法以及代码块。

成员变量和成员方法，必须通过对象来访问，必须依赖于对象才能进行访问。

而使用 static 修饰的成员变量和成员方法独立于该类任何一个实例对象，访问时不依赖于任何一个对象，可以直接通过类来访问

正常情况下调用方法：类 -》对象 -》方法
被 static 修饰的方法的调用：类 -》方法

被 static 修饰的变量叫做静态变量，被 static 修饰的方法叫做静态方法

静态成员变量和静态成员方法，属于一个类，被多个对象共享，在内存中只有一份
非静态的成员变量和成员方法，属于对象，不同对象的成员变量和成员方法是不一样的。

-静态成员变量&静态成员方法
例 1

```java
public class User {
    public static String name;
    public static void show(){
        System.out.println("这是一个User对象");
    }
}
```

```java
public class Test {//此时，因为user类里面的成员变量和成员方法都是静态的，因此可以不创建对象直接进行调用。创建对象后也依然可以调用。
    public static void main(String[] args) {
        User.name = "张三";//直接调用静态成员变量
        System.out.println(User.name);//直接输出静态成员变量
        User.show();//直接调用静态成员方法
    }
}
```

例 2

```java
public class User { //此时，因为user类里面的成员变量和成员方法都是静态的，因此可以不创建对象直接进行调用。创建对象后也依然可以调用。
    public static String name;
    public static void show(){
        System.out.println("这是一个User对象");
    }
}
```

```java
public class Test {//此时，因为user类里面的成员变量和成员方法都是静态的，因此可以不创建对象直接进行调用。创建对象后也依然可以调用。
    public static void main(String[] args) {
        User user = new User();
        User.name = "张三";//直接调用静态成员变量
        System.out.println(User.name);//直接输出静态成员变量
        User.show();//直接调用静态成员方法，输出结果为 name:张三

        User user1 = new User();
        User1.name = "李四";//直接调用静态成员变量
        System.out.println(User1.name);//直接输出静态成员变量
        User.show();//直接调用静态成员方法，输出结果为 name:李四，因为静态的成员变量和成员方法是所有对象共享的内容。相当于对于同一个变量进行多次赋值覆盖掉了第一次的赋值结果，最后得出的是最后一次赋值的结果。
    }
}
```

-非静态成员变量&非静态成员方法

```java
public class User {
    public String name;
    public void show(){
        System.out.println("这是一个User对象");
    }
}
```

```java
public class Test {//此时，因为user类里面的成员变量和成员方法都是非静态的，因此必须先创建对象，通过新建的对象再进行调用。
    public static void main(String[] args) {
        User user = new User();//第一步必须先创建对象
        User.name = "张三";//调用非静态成员变量
        System.out.println(User.name);//输出非静态成员变量
        User.show();//调用非静态成员方法
    }
}
```

-非静态成员变量 对比用例 1

`````java
public class Test {
    private int id;//int型数据默认值是0
    public static void main(String[] args) {
        Test test = null;
        for(int i = 0; i < 10; i++>){//循环10次，创建10个Test对象，id自动从0加1
            test = new Test();
            test.id++;//此时id使用的是对象里面的id,每个新创建的Test对象中id都是初始值0
        }
        System.out.println(test.id);//此时输出结果是1

    }
}
```
-静态成员变量 对比用例2
````java
public class Test {
    private static int id;//int型数据默认值是0
    public static void main(String[] args) {
        Test test = null;
        for(int i = 0; i < 10; i++>){//循环10次，创建10个Test对象，id自动从0加1
            test = new Test();
            test.id++;//此时的id使用的是类里面的id，每创建一次新对象，都会持续对类里面的id加1，循环10次，相当于为id加了10次1
        }
        System.out.println(test.id);//此时输出结果是10

    }
}
```

使用 static 修饰的静态方法中不能使用 this 关键字，因为this关键字指代的是当前对象，而静态方法和静态成员变量都属于类，不属于对象，因此静态方法中不能直接访问类的实例变量和实例方法，但是可以直接访问类的静态变量和静态方法，如果一定要访问实例变量和实例方法，必须先实例化该类的对象，通过对象去访问。

另外，static 还可以修饰代码块，被 static 修饰的代码块叫做静态代码块。
静态代码块的特点是：
只执行一次，当类被加载到内存中的时候，会自动执行静态代码块，不需要手动调用。

```java
public class User {
    public static int num;
    static {
        num++;//静态代码块也就是类里面的成员变量是共享的。
        System.out.println("执行了静态代码块");
    }
}
```

````java
public class Test {
    public static void main(String[] args) {
        User user = new User();
        User user2 = new User();
        User user3 = new User();
        System.out.println(user.num);//输出结果：执行了静态代码块  只执行了一次  1
        System.out.println(user2.num);//输出结果：1
        System.out.println(user3.num);//输出结果：1

    }
}
```

程序执行的时候，首先会将程序中用到的类加载到内存中，并且只加载一次，加载的时候就会自动执行静态代码块，因为只加载一次，所以静态代码块只执行一次。

静态代码块只执行一次，当程序加载类的时候执行
而普通的代码块执行多次，取决于创建了多少个对象，当程序创建对象的时候执行普通代码块，每创建一个对象就执行一次代码块

要创建对象时，首先需要先加载类，再创建对象，然后执行代码块也就是类，再调用构造器
具体来说，先加载父类 -> 加载/调用/执行父类静态代码块 -> 加载/调用/执行子类的静态代码块 -> 调用父类的代码块-> 调用父类构造函数 -> 执行子类的代码块 -> 调用子类构造函数

总结————代码块、静态代码块、父子类的构造器执行顺序：

第一步和第二部属于加载类的过程
1、调用父类的静态代码块即加载类

2、调用子类的静态代码块即加载类

第三步以后属于创建对象的过程
3、调用父类的代码块

4、调用父类的构造器

5、调用子类的代码块

6、调用子类的构造器

# 继承

继承是 Java 代码复用的重要特征，子类可以直接继承父类全部非私有信息（包括属性、方法）
*1 父类的私有信息不可以进行共有，也就是不可以被子类继承的。
*2 创建子类对象的时候，会默认优先创建父类对象

## 子类访问父类

创建子类对象的时候，无论使用无参还是有参，都会默认使用无参创建父类对象

使用 this 或者 super 调用构造函数，必须写到第一行，并且 this 和 super 调用构造器不能同时出现

## 类访问权限

访问权限修饰符（作用域的范围）

4 种：public、private、默认default (不写)、protected

| 修饰符    | 同一个类 | 同包不同类 | 不同包     | 同包父子类     | 不同包父子类
| --------- | -------- | ---------- | ---------- | ---------- | ---------- |
| public    | 可以访问 | 可以访问   | 可以访问   | 可以访问   | 可以访问   | //到处都可以用
| protected | 可以访问 | 可以访问   | 不可以访问 | 可以访问   | 不可以访问   |
| 默认      | 可以访问 | 可以访问   | 不可以访问 | 可以访问 | 不可以访问   |
| private   | 可以访问 | 不可以访问 | 不可以访问 | 不可以访问 | 可以访问   | //除了自己的类以外，都不可以用

## 方法重写

子类继承父类方法的基础上，对父类方法重新定义并覆盖的操作叫做方法重写

方法重写的规则

- 父子类方法名相同
- 父子类的参数列表相同
- 只对方法代码块里面的内容进行修改
- 子类方法的返回值和父类方法的返回值相同或是其子类
  - 子类方法的返回值和父类方法的返回值相同
  - 或者子类方法的返回值是父类方法的返回值的子类
- 子类方法的访问权限不能小于父类，也就是说，子类方法的访问权限>=父类方法的访问权限
- 父类方法的访问权限是private的时候，不可以在子类中重写，因为 private 修饰的父类方法子类是无法继承的，就不可能进行重写。（子类只能继承非私有的父类方法）

***！！！重写是建立在继承的基础上的，方法重写的前提一定子类先继承了父类的方法，才能进行重写，而 private 修饰的父类方法子类是无法继承的，所以更不可能进行重写。
举例：从长辈那里先继承了房子的所有权后，才能进行装修。

！！！## 方法重写和重载的区别

| 类型 | 所在位置 | 方法名 | 参数列表 | 返回值         | 访问权限     |
| ---- | -------- | ------ | -------- | -------------- | ------------ |
| 重写 | 父子类   | 相同   | 相同     | 相同或是其子类 | 不能小于父类 |
| 重载 | 同一个类 | 相同   | 不同     | 没有要求       | 没有要求     |
`````

# 1 多态

面向对象三大基本特征：封装、继承、多态

多态是指一个事物有多种表现形态

Java：定义一个类，该类的实例化对象在不同的业务场景中，根据不同的需求，呈现出不同的业务逻辑

场景举例：会员买书
普通会员买书 9 折优惠
超级会员买书 6 折优惠
VIP 会员买书 5 折优惠

面向对象的思想————对象有两个
对象 1：会员 -> 对象 2：收银员
而会员又可以有很多种：普通会员，超级会员，VIP 会员

从效果来看提高了代码的扩展性/复用性

使用的是多态编程思想，具体来说可以通过继承的方式来实现
会员是父类，三种会员是子类

对象：会员
一个会员对象父类，三种子类会员对象类

```java
public class Member{//父类：会员
    public void buyBook() {
        System.out.println("父类会员的方法");
    }
}
```

```java
public class Member{//父类：会员
    public void buyBook() {
        System.out.println("父类会员的方法");
    }
}
```

```java
public class OrdinaryMember extends Member{//子类：普通会员  直接继承Member类
    @override
    public void buyBook() {//对父类方法进行重写
        System.out.println("普通会员买书打9折");
    }
}
```

```java
public class SuperMember extends Member{//子类：超级会员
    @override
    public void buyBook() {//对父类方法进行重写
        System.out.println("超级会员买书打6折");
    }
}
```

```java
public class VIPMember extends Member{//子类：VIP会员
    @override
    public void buyBook() {//对父类方法进行重写
        System.out.println("VIP会员买书打5折");
    }
}
```

对象：收银员
收银员类

```java
public class Cashier{//对象：收银员
    private Member member;//有多种形态，因此有多态的特征

    public Member getMember(){
        return Member;
    }

    public void setMember(Member member){
        this.member = member;//this.member是父类，= member的member是子类，只有两者有继承关系，数据类型才会没有冲突，才能把子类对象的值赋给父类。
    }

    public void settlement(){
        System.out.println("开始结算");
        this.Member.buyBook();
    }
}
```

业务逻辑/核心业务类

```java
public class Test{//业务类
    public static void main(String[] args){
        //第一步：先创建对象
        OrdinaryMember ordinaryMember = new OrdinaryMember();
        SuperMember superMember = new SuperMember();
        VIPMember vipMember = new VIPMember();
        Cashier cashier = new Cashier();

        //第二步：
        cashier.setMember(ordinaryMember);//通过set方法，在不同的场景下，传不同的值ordinaryMember/superMember/vipMember进来，是什么会员类型就会调用什么子类对象的值，因此可以提高代码的复用性即扩展性。
        cashier.settlement();//执行方法
    }
}
```

## 多态的使用

1、定义 set 方法时形参为父类，调用方法时传入的参数为子类对象

```java
public void setMember(Member member) {
    this.member = member;
}
```

```java
Cashier cashier = new Cashier();
cashier.setMember(new VIPMember());
```

2、定义方法时，返回值的数据类型为父类，
而调用方法时，返回子类对象

```java
public Member getMember(String name){
    if(name.equals("ordinaryMember")){
        return new OrdinaryMember();
    }
    if(name.equals("superMember")){
        return new SuperMember();
    }
    if(name.equals("VIPMember")){
        return new VIPMember();
    }
    return null;
}
```

```java
public class Test{//业务类
    public static void main(String[] args){
        OrdinaryMember ordinaryMember = new OrdinaryMember();
        SuperMember superMember = new SuperMember();
        VIPMember vipMember = new VIPMember();
        Cashier cashier = new Cashier();


        cashier.setMember(ordinaryMember);
        //cashier.settlement();
        System.out.println(cashier.getMember(name: "ordinaryMember"));//输出的结果是：OrdinaryMember@存储地址（即hash值）

        //Member member = new OrdinaryMember();子类赋值给父类，不会报错 eg. 猫是动物（从右向左读）
        //OrdinaryMember ordinaryMember1 = new Member();父类赋值给子类，相当于把一个比较大的范围赋值给小的范围，会报错 eg. 动物是猫（从右向左读）
        //OrdinaryMember ordinaryMember1 = (OrdinaryMember) new Member();父类赋值给子类时，必须进行强制类型转换
    }
}
```

上述两种多态的形式，都是基于子类对象可以直接赋值给父类对象，即自动类型转换

# 抽象

父类的方法必须存在，但是父类方法的具体实现没有意义

只定义父类方法，但是不做具体的实现 => 即 抽象方法，加上 abstract（举例：父亲的房子一天也不住，孩子继承房子的时候一定要重新装修的，那作为父亲，就没必要装修了，等孩子继承房子后，由孩子去装修房子即方法重写即可。）

```java
public abstract void buyBook();
```

！！！抽象方法所在的类，必须定义为抽象类，不然会报错

对多态的父类进行优化后：

```java
public abstract class Member {
    public abstract void buyBook();
}
```

抽象类不能被实例化，不可以被 new，只能实例化其子类

一旦某个类继承了一个抽象类，要么该类也需要定义为抽象类（没有什么意义）；
要么去重写从抽象父类那里继承过来的抽象方法，让它有具体的实现，不再是抽象方法，（快捷键：ctrl + i 直接去实现）。

一旦某个类中，出现了一个抽象方法，则该类必须被声明为抽象类；
但是抽象类中可以包含非抽象方法。

# 接口

接口是实际开发中使用频繁非常重要的一种编程方式，面向接口编程（就是我们在创建对象的时候，创建的是接口类），提高程序的扩展性，降低程序的耦合度，进行解耦合（让组件之间的关系比较松散，没有直接相关的固定关系，可以随时调整/改变，比较灵活）
耦合度不好（结合的紧密程度）举例：鼠标通过线直接连接到主机里面，每次想换鼠标就必须拆开主机才能进行调整；
耦合度好：举例 USB 接口 与 笔电， 一台笔电可以和很多不同的鼠标/键盘/音箱 进行连接

接口
接口：是对抽象类的一种升级，实现解耦合
接口：本质上就是抽象类，只不过使用更加简便而已 举例：抽象类 -20 年前的台式机电脑 vs 接口 - 现在的笔电/平板电脑
接口：是一个极度抽象的抽象类，接口中 100%的方法是抽象方法，也就是说，当一个抽象类中的所有方法都是抽象方法时就可以换一种写法，简化为：接口

接口的具体实现叫做实现类，不叫子类
接口对标抽象类
实现类对标抽象类的非抽象子类，关键字不是 extends 继承，而是 implements 实现

关联：继承->抽象->接口

从 100%抽象方法的抽象类 abstract class -> interface
(而且写为下面的方式也不会报错，只是没有意义)
//`java
//public abstract interface Equipment {
//    public abstract void work();
//}
//`

```java
public abstract class Equipment {
    public abstract void work();
}
```

优化为接口

```java
public interface Equipment {
    public void work();
}
```

练习接口

```java
public interface Equipment {//设备接口
    public void work();
}
```

```java
public class EquipmentA implements Equipment {//设备A 实现设备接口
    public void work(){
        System.out.println("设备A运行，生成产品A");
    }
}
```

```java
public class EquipmentB implements Equipment {//设备B 实现设备接口
    public void work(){
        System.out.println("设备B运行，生产产品B");
    }
}
```

```java
public class EquipmentC implements Equipment {//设备C 实现设备接口
    @Override
    public void work() {
        System.out.println("设备C运行，生产产品C");
    }
}
```

```java
public class Factory {//工厂类
    private Equipment equipment;

    //构造器
    public Equipment getEquipment() {
        return equipment;
    }

    public void setEquipment(Equipment equipment) {
        this.equipment = equipment;
    }

    //业务逻辑
    public void work(){
        System.out.println("开始生产...");
        this.equipment.work();
    }
}
```

```java
public class Test {//业务实现类
    public static void main(String[] args) {//执行业务
        Factory factory = new Factory(); //创建工厂对象
        factory.setEquipment(new EquipmentC());
        factory.work();
    }
}
```

# Object 类

Object 是 Java 中全部类的共同父类 -> 为了实现代码复用

Object 中定义了一些所有类都需要使用到的方法，所有类直接继承使用

在具体的业务场景中，子类也可以对从父类继承来的方法进行重写，以匹配当前的业务需求
经常重写的三个方法：（在不同的业务场景中，通常表现不同）
toString() 以字符串的形式返回该类的实例化对象信息
equals(Object obj) 判断两个对象是否相等
hashCode() 返回对象的散列码

```java
public class Test {
    public void test() throws Throwable{
        hashcode();
        getClass();//获取类的类型
        equals(null);
        clone();
        toString();
        notify();//唤醒线程
        notifyAll();//唤醒线程
        wait();//线程休眠
        wait(timeout: 100L);//休眠方法重载
    }
}
```

| 方法                              | 描述                                   |
| --------------------------------- | -------------------------------------- |
| public String toString()          | 以字符串的形式返回该类的实例化对象信息 |
| public boolean equals(Object obj) | 判断两个对象是否相等                   |
| public native int hashCode()      | 返回对象的散列码                       |
| public native int hashCode()      | 返回对象的散列码                       |
| public native int hashCode()      | 返回对象的散列码                       |

# Object 方法重写

## toString

以字符串的形式返回该类的实例化对象信息

Object 类中的 toString 方法

```java
public String toString() {
    return getClass().getName() + "@" + Integer.toHexString(hashCode());
}
```

## equals

equals 方法是用来判断两个对象是否相等

```java
public boolean equals(Object obj) {
    return (this == obj);//此时==判断的是对象的内存地址
}
```

== 判断的是对象的内存地址

```java
@Override
public boolean equals(Object o) {
    if (this == o) return true;//比较的对象是同一个时，返回true
    if (o == null || getClass() != o.getClass()) return false;//传过来的数据为null->会空指针；当前对象的类型 和被比较对象的类型
    User user = (User) o;//类型强转
    return Objects.equals(id, user.id) &&
        Objects.equals(name, user.name);//id和id，name和name分别比较
}
```

name 必须用 equals 来判断，id 也必须用 equals 来判断，如果用==来判断时，如果是用 new 对象（在堆内存的内容）时，就会出现问题；==可以判断栈内存里面的值

String 类对于 equals 方法的重写

```java
public boolean equals(Object anObject) {
    if (this == anObject) {//首先判断类型是否相同
        return true;
    }
    if (anObject instanceof String) {
        String anotherString = (String)anObject;
        int n = value.length;
        if (n == anotherString.value.length) {//再来判断数据的长度是否相同
            char v1[] = value;
            char v2[] = anotherString.value;
            int i = 0;
            while (n-- != 0) {//判断每一个相同位置上的数据是否相等
                if (v1[i] != v2[i])
                    return false;
                i++;
            }
            return true;
        }
    }
    return false;
}
```

Integer 类对于 equals 方法的重写

```java
public boolean equals(Object obj) {
    if (obj instanceof Integer) {
        return value == ((Integer)obj).intValue();
    }
    return false;
}
```

== 判断两个对象的内存地址是否相等

equals 默认是 Object 类提供的方法，默认实现和 == 是一致的

如果是默认的 equals(Object 中原生的方法)，则和 == 是一样的，没有区别，因为 Object 中方法的实现就是 ==

如果是重写的 equals，则和 == 是不一样的，重写之后判断的就是对象的值是否一致，具体实现需要看具体的类型，可能会需要循环遍历等等

## hashCode

```java
public native int hashCode();//默认实现方法是本地native的方法
```

native 修饰的本地方法
本地方法指的是 Java 无法实现的功能，由其他语言（C++）来实现，Java 只需要负责调用

hashCode 包含内存地址、对象的属性值、类的信息，混合在一起，映射出来的一个整形数值
重写 hashcode 方法的意义是什么？->重写后可以配合 equals 联合起来使用

hashCode 和 equals 需要配合起来使用，都是用来判断两个对象是否相等的方法

1. hashCode 效率更高，如果两个对象的 hashCode 不相等，则这两个对象肯定不相等；
2. 但是如果两个对象的 hashCode 相等（内存地址、对象的属性值、类的信息混合），不能说明两个对象肯定相等，此时就需要使用 equals 进一步验证类似于接口和实现类的关系。

先用效率高的方法 hashcode()来判断，如果能得到结果，则直接返回，如果无法得到结果，再用效率低的方法 equals()进行验证->即 hashcode()+equals() 配合的方法

应用场景：在集合框架中使用
元素唯一

# 包装类

## 什么是包装类

Java 中的数据类型从本质上分为两类：8 种基本数据类型和引用类型
引用数据类型 = 必须通过 new 的方式生成对象的数据类型

如何把基本数据类型转成对象？

包装类是 Java 提供的一组类，专门用来创建 8 种基本数据类型对应的对象，每种基本数据类型对应一种包装类

| 基本数据类型 | 包装类    |
| ------------ | --------- |
| byte         | Byte      |
| short        | Short     |
| int          | Integer   |
| long         | Long      |
| float        | Float     |
| double       | Double    |
| char         | Character |
| boolean      | Boolean   |

包装类全部存放于 java.lang 包中

一级父类：Object
二级父类：Character、Number、Boolean
同时，Number 的子类：Byte、Short、Integer、Long、Float、Double

实际开发中，对于包装类的使用，就是将基本数据类型转为包装类=装箱，或者将包装类转为基本数据类型=拆箱

## 装箱和拆箱

装箱：直接调用构造器，将基本数据类型转为包装类

```java
public class Test {
    public static void main(String[] args) {
        byte b = 1;
        Byte byt = new Byte(b);//将byte基本数据类型转为Byte包装类

        short s = 2;
        Short shor = new Short(s);//将short基本数据类型转为Short包装类

        int i = 3;
        Integer integer = new Integer(i);//将int基本数据类型转为Integer包装类

        long l = 4;
        Long lon = new Long(l);//将long基本数据类型转为Long包装类

        float f = 5.5f;
        Float flo = new Float(f);//将float基本数据类型转为Float包装类

        double d = 6.6;
        Double dou = new Double(d);//将double基本数据类型转为Double包装类

        char cha = 'J';
        Character charac = new Character(cha);//将char基本数据类型转为Character包装类

        boolean bo = true;
        Boolean bool = new Boolean(bo);//将boolean基本数据类型转为Boolean包装类
    }
}
```

拆箱：调用对应的方法，将包装类对象转为基本数据类型

```java
public class Test {
    public static void main(String[] args) {
        byte b = 1;
        Byte byt = new Byte(b);
        byte b1 = byt.byteValue();//调用对应的方法将包装类转为基本数据类型的数据

        short s = 2;
        Short shor = new Short(s);
        short i1 = shor.shortValue();//调用对应的方法将包装类转为基本数据类型的数据

        int i = 3;
        Integer integer = new Integer(i);
        int i2 = integer.intValue();//调用对应的方法将包装类转为基本数据类型的数据

        long l = 4;
        Long lon = new Long(l);
        long l1 = lon.longValue();//调用对应的方法将包装类转为基本数据类型的数据

        float f = 5.5f;
        Float flo = new Float(f);
        float v = flo.floatValue();//调用对应的方法将包装类转为基本数据类型的数据

        double d = 6.6;
        Double dou = new Double(d);
        double v1 = dou.doubleValue();//调用对应的方法将包装类转为基本数据类型的数据

        char cha = 'J';
        Character charac = new Character(cha);
        char c = charac.charValue();//调用对应的方法将包装类转为基本数据类型的数据

        boolean bo = true;
        Boolean bool = new Boolean(bo);
        boolean b2 = bool.booleanValue();//调用对应的方法将包装类转为基本数据类型的数据
    }
}
```

# 异常

## 什么是异常——用来描述 Java 中的错误

Java 中的错误可以分为两类：

- 1. 编译时错误，一般指语法错误，标红，无法通过编译；
- 2. 运行时错误，语法没有问题，可以正常通过编译，但是运行时报错。e.g. 10/0

Java 专门提供了一组类，来表示各种各样的运行时错误，错误也是对象呐（万物皆对象~）

- ArithmeticException：表示数学异常
- ClassNotFoundException：类未定义异常，即类找不到
- IllegalArgumentException：参数格式异常
- ArrayIndexOutOfBoundsException：数组下标越界异常
- NullPointerException：空指针异常
- NoSuchMethodException：方法未定义异常
- NumberFormatException：将其他数据类型转为数值类型的不匹配异常

各种异常举例

- ArithmeticException：表示数学异常

```java
System.out.println(10 / 0);//编译错误，数学逻辑错了
```

- ClassNotFoundException：类未定义异常，即类找不到

```java
public static void main(String[] args) throws Exception {
    System.out.println(Class.forName("Test2"));
}
```

- IllegalArgumentException：参数格式异常

```java
import java.lang.reflect.Method;

public class Test {
    public static void main(String[] args) throws Exception {
        Class<?> test = Class.forName("Test");
        Method method = test.getMethod("test", Integer.class);
        method.invoke(new Test(), "1");
    }

    public void test(Integer integer){
        System.out.println(integer);
    }
}
```

- ArrayIndexOutOfBoundsException：数组下标越界异常

```java
public class Test {
    public static void main(String[] args) throws Exception {
        int[] array = {1,2,3};
        System.out.println(array[3]);//下标也就到2
    }
}
```

- NullPointerException：空指针异常

```java
public class Test {
    public static void main(String[] args) throws Exception {
        Integer num = null;
        System.out.println(num.equals(1));
    }
}
```

- NoSuchMethodException：方法未定义异常

```java
import java.lang.reflect.Method;

public class Test {
    public static void main(String[] args) throws Exception {
        Class<?> test = Class.forName("Test");
        Method method = test.getMethod("test2", Integer.class);
        System.out.println(method);
    }

    public void test(Integer integer){
        System.out.println(integer);
    }
}
```

- NumberFormatException：将其他数据类型转为数值类型的不匹配异常

```java
public class Test {
    public static void main(String[] args) throws Exception {
       Integer integer = new Integer("a");//"a"是Character类数据，不是Integer类
        System.out.println(integer);
    }
}
```

# 异常

异常是 Java 处理错误的一种机制，为程序员指出程序中存在的问题，程序员通过异常信息发现问题，分析问题，从而解决问题。

异常不是编译时错误，不是语法错误，是运行时错误（程序语法正确，能够正常通过编译，但是在运行期间报错。），会将具体的错误信息以及出错位置统一告知程序员
出现异常提醒时，需要看两个重点信息：（从下往上看）

1. 异常的类型：什么类型的错误
2. 异常的位置：在哪行代码报错

## 异常的使用

# try-catch

try：尝试运行————监听可能会抛出异常的代码，一旦出现错误，JDK 会自动创建一个错误对应的异常对象，抛出该异常对象

catch：捕获异常————用来捕获 JDK 创建的异常对象，进行后续的处理

```java
try {

} catch(Exception e){

}
```

```java
public class Test3 {
    public static void test3(String str){
        Integer integer = null;//创建对象
        try {
            integer = Integer.valueOf(str);//给对象赋值
        } catch (Exception e){
            System.out.println(e.getMessage());
        }
    }
}
```

业务代码出错的概率比较大（传参容易出错或者数据容易出错。。。）的时候，一般需要加上 try-catch 来进行异常的处理，如果是出错概率较小的代码，不需要加 try-catch，因为 JDK 会自动进行是否异常的判断，并在有错误时抛出异常。
当程序出现异常的时候，代码一般就不再继续执行了。

# finally 关键字

finally 关键字，无论程序是否抛出异常，finally 代码块中的程序一定会执行，资源一定会被释放。

```
try{

} catch(){

} finally{

}
```

```java
public class Test {
    public static void main(String[] args) throws Exception {
        System.out.println(test());
    }

    public static int test(){//最终输出结果 try finally... 20
        try {
            //第一步
            System.out.println("try");
            return 10;//结束程序
        } catch (Exception e) {
            e.printStackTrace();
        } //第二步
        finally {//把代码放在finally里面，即使try里面有return，try里面的return也不执行，程序不会在try后结束，而是在finally执行后才会继续。因此，finally的return会覆盖掉try里面的return。
            System.out.println("finally...");//第三步
            return 20;//第四步
        }
    }
}
```

## throw 和 throws

throw 和 throws 是 Java 在处理异常时使用的两个关键字，都是用来抛出异常的，但是使用方式和表示的含义完全不同。

Exception 是父类，IOException 是子类，只能把子类对象赋值给父类，但是不能将父类对象赋值给子类，是多态的一种体现。

```java
public class Test {
    public static void main(String[] args) throws Exception {
       try{
            IOException exception = new IOException();//IOException extends Exception, OK
            throw exception;
        }catch (Exception e){//传参，子类IOException -> 父类Exception
            e.printStackTrace();
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) throws Exception {
       try{
            Exception exception = new Exception();//IOException extends Exception, OK
            throw exception;
        }catch (IOException e){//传参，父类Exception ->  子类IOException，IOException会标红报错
            e.printStackTrace();
        }
    }
}
```

Java 中抛出异常的方式有 3 种：

- 1. try-catch————是一种防范机制，代码可能会出现异常。如果抛出则捕获即可；如果不抛出则程序继续执行。
- 2. throw————开发者主动创建一个错误并抛出，100%一定会抛异常。
- 3. throws————标注方法的，用来描述该方法可能会抛出的异常。

1. 手动创建异常对象并抛出 举例 1

```java
public class Test {
    public static void main(String[] args) throws Exception {
      Exception exception = new Exception();//主动创建异常对象
      throw exception;//抛出异常
    }
}
```

2. 手动创建异常对象并抛出 举例 2

```java
public class Test {
    public static void main(String[] args) throws Exception {
        try{
            Exception exception = new Exception();//主动创建异常对象
            throw exception;//抛出异常
        }catch (Exception e){
            e.printStackTrace();
        }
    }
}
```

3. 手动创建异常对象并抛出 举例 3

```java
public class Test {
    public static void main(String[] args) throws Exception {
        String str = "Java";
        if(str.equals("Java")){
            throw new NumberFormatException();
        } else {
            int num = Integer.parseInt(str);
        }
    }
}
```

- throws 标注方法的，用来描述该方法可能会抛出的异常

throw 主动抛出一个对象，throws 标注一个方法可能会抛出某些异常

```java
public class Test {
    public static void main(String[] args) throws Exception {
        try {
            test();
        } catch (NumberFormatException e) {
            e.printStackTrace();
        }
    }

    public static void test() throws NumberFormatException{//用throws标注，调用test方法时，可能会抛出以下异常（代码规范的要求，自己的代码别人也会调用）
        String str = "Java";
        int num = Integer.parseInt(str);
    }
}
```

通过 throws 可以声明方法，其他人在调用方法的时候必须强制其使用 try-catch 进行代码处理，如果对方不进行 try-catch 处理就会报错。

## 自定义异常

定义一个方法，对传入的参数进行 ++ 操作并返回结果，同时要求参数必须是整数类型，如果传入的参数不是整数类型则抛出自定义异常

自定义的类继承 Exception ，就成为了一个异常类

```java
public class NumberException extends Exception {//自定义异常类，继承Exception，即Java的扩展性
    public NumberException(String message){
        super(message);
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Test test = new Test();
        try {
            int add = test.add("a");//int add = test.add(1);不会抛异常
            System.out.println(add);
        } catch (NumberException e) {
            e.printStackTrace();
        }
    }

    public int add(Object object) throws NumberException{
        if(!(object instanceof Integer)) {
            //抛出异常
            //异常信息是传入的参数不是整数类型
            throw new NumberException("传入的参数不是整数类型");//定义的异常类
        } else {
            int num = (int) object;
            return ++num;
        }
    }
}
```

# 多线程

使用多线程可以让程序充分利用 CPU 的资源，提高 CPU 的使用效率，从而解决高并发所带来的负载均衡问题，提高性能

优点：

- 资源得到更合理的利用
- 程序设计更加简洁
- 程序响应速度更快，运行效率更高

缺点：

- 需要更多的内存空间来支持多线程
- 多线程并发访问的情况可能会影响数据的准确性
- 数据被多线程共享，可能会出现死锁的情况

应该将程序设计得更加合理有效，避免多线程得缺点，充分发挥多线程得优点，从而提高程序得性能

## 进程和线程

# 什么是进程

进程就是计算机正在运行的、一个独立的应用程序，进程是一个动态的概念。（安装完成的程序不是进程，正在跑的程序才是进程）

# 什么是线程

线程是组成进程的基本单位，一个进程中包含一个或多个线程，线程可以完成特定的功能

进程和线程都是应用程序在执行过程中的概念，动态，如果应用程序没有执行，则不存在进程和线程

应用程序是静态的概念，进程和线程都是动态的概念，有创建就有销毁，存在也是暂时的，不是永久的。

# 进程和线程的区别？

每个进程在运行时，拥有独立的内存空间，每个进程所占用的内存都是独立的，互不干扰。

多个线程是共享内存空间的，但是每个线程的执行是相对独立的，只不过共用内存空间。

线程必须依赖于进程才能执行，单独的线程是无法执行的，由进程来控制多个线程的执行。

# 多线程：一个进程中，多个线程同时执行。

# 在单核 CPU 的情况下，多线程并不是真正的同时执行，而是多个线程交替执行，交替占用 CPU ，执行自己的业务

因为程序执行速度太快，看起来是在同时执行。

# 在多核 CPU 的情况下，多线程才是真正的同时执行

```java
public class Test {
    public static void main(String[] args) {
        new Thread(()->{
            for (int i = 0; i < 10; i++) {
                System.out.println("++++++++++++"+i);
            }
        }).start();

        new Thread(()->{
            for (int i = 0; i < 10; i++) {
                System.out.println(i + "============");
            }
        }).start();
    }
}
```

# 多线程

## Java 中线程的使用

Java：面向对象的编程，万物皆对象，线程也是一种对象。
如何运用线程？————通过类的方式

1、继承 Thread 类

Thread 类是 Java 提供的线程的父类，类似于 Exception 是 Java 提供的异常的父类

为什么要有这个父类呢？————为了实现程序的扩展，基于 JDK 基础类开发者可以扩展出其他的相关类

线程一定跟任务绑定，一个线程必须要执行一个任务，一个空的线程没有意义，一个空的任务也没有意义，一定是线程 + 任务绑定在一起
举例：一个公司有成千名员工，但是每个员工也就是每个线程做的工作不同

Java 的特点：对修改封闭（不能修改 JDK 源码），对扩展开放（可以自定义类，通过继承的形式融入到 JDK 中）

Thread 类是 JDK 线程父类，Runnable 接口是 JDK 定义任务的接口，任务的具体实现写在 run() 方法中

1、创建 Thread 对象的时候，从外部传入一个 Runnable 对象（表示创建线程的时候，需要绑定一个任务）

```java
public class MyThread extends Thread {

}
```

2、当线程执行的时候，会调用线程的 run 方法

```java
public class MyThread extends Thread {
    @Override //通过方法重写的方式，调用线程
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(i + "===========");
        }
    }
}
```

3、如果创建线程对象的时候，传入了任务，则会执行任务，否则线程什么都不做

```java
@Override
public void run() {//thread父类对run()方法的实现
    if (target != null) {//private Runnable target; 一个叫做target的Runnable任务对象
        target.run();
    }
}
```

# 如何使用线程

1、创建线程对象

2、调用线程对象的 start 方法来启动线程

线程首先是需要去争夺 CPU 资源，当拿到资源之后才能执行任务

# 方式 1：把任务直接写在 threads 里面，耦合度过高

```java
public class MyThread extends Thread {//线程1
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(i + "===========");
        }
    }
}
```

```java
public class MyThread2 extends Thread {//线程2
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println("+++++++++++++++++" + i);
        }
    }
}
```

```java
/*public class Test {//线程举例，主线程执行，然后线程1，线程2交替进行；现实举例：让一个人取快递，倒水，做家务，一次只能做一件事情也就是一个线程
    public static void main(String[] args) {//main方法实际上是主线程
        //1. 创建线程对象
        MyThread thread = new MyThread();//创建线程1
        //2. 启动线程
        thread.run();

        //1. 创建线程对象
        MyThread2 thread2 = new MyThread2();//创建线程2
        //2. 启动线程
        thread2.run();
    }
}
*/
```

```java
public class Test {//多线程举例，主线程执行，然后线程1，线程2交替进行；现实举例：让两个人取快递，倒水，做家务，等等，两个人分别一次只能做一件事情，也就是两个线程交替进行
    public static void main(String[] args) {//main方法实际上是主线程
        //1. 创建线程对象
        MyThread thread = new MyThread();//创建线程1
        //2. 启动线程
        thread.start();

        //1. 创建线程对象
        MyThread2 thread2 = new MyThread2();//创建线程2
        //2. 启动线程
        thread2.start();
    }
}
```

# start() VS run()

start()方法：相当于组长 main()招聘了张三，李四两个员工，分别给他们安排了各自的任务，他们的任务同时执行
run()方法：相当于组长 main()自己去做了安排给张三和李四的两个工作任务，任务交替执行，一次只做一个任务

2、通过实现 Runnable 接口的方式

第一种形式线程和任务的耦合度过高，不利于程序的扩展，所以开发中不推荐使用

# 方式 2：

实现解耦合————实现 MyRunnable 接口，只需要定义任务，在执行的时候，通过传参就可以调用不同的任务

```java
public class MyRunnable implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println("~~~~~~~~~~~" + i + "~~~~~~~~~~~~~~");
        }
    }
}
```

```java
public class MyRuunable2 implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(i + "******************--------");
        }
    }
}
```

```java
public class Test {//多线程举例，主线程执行，然后线程1，线程2交替进行；现实举例：让两个人取快递，倒水，做家务，等等，两个人分别一次只能做一件事情，也就是两个线程交替进行
    public static void main(String[] args) {//main方法实际上是主线程
        MyRunnable myRunnable = new MyRunnable();//构造线程
        MyRuunable2 myRuunable2 = new MyRuunable2();//构造线程
        Thread thread1 = new Thread(myRunnable);//创建线程，通过传参的方式来调用不同的任务
        thread1.start();//启动线程
    }
}
```

方式 1 如何进行改造？改造之后虽然可以正常执行，但是并没有太大必要这样用

```java
public class MyThread extends Thread {//线程1
    private Runnable target;

    public MyThrread(Runnable target){
        this.target = target;
    }

    @Override
    public void run() {//通过外部传参的方式实现解耦合
        if(target = null){
            System.out.println("没有给当前线程指定任务");
        }else{
            target.run;
        }
    }
}
```

```java
public class MyRunnable implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println("~~~~~~~~~~~" + i + "~~~~~~~~~~~~~~");
        }
    }
}
```

```java
public class MyRuunable2 implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(i + "******************--------");
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) {//main方法实际上是主线程

        MyRunnable myRunnable = new MyRunnable()；
        //1. 创建线程对象
        MyThread thread = new MyThread(myRunnable);//创建线程，通过传参的方式实现解耦合
        //2. 启动线程
        thread.start();
    }
}
```

## 线程的状态

线程一共有 5 种状态，在特定的情况下，线程可以在不同的状态之间切换

- 创建状态：实例化了一个新的线程对象，还未启动
- 就绪状态：创建好的线程对象调用了 start() 方法完成启动，进入线程池等待抢占 CPU 资源
- 运行状态：线程对象获取了 CPU 资源，在规定的时间内执行任务
- 阻塞状态：正在运行的线程暂停执行任务，释放所占用的 CPU 资源
- 终止状态：线程运行完毕或因为异常导致线程终止运行

```java
public class MyRunnable implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println("~~~~~~~~~~~" + i + "~~~~~~~~~~~~~~");
        }
    }
}
```

```java
public class MyRuunable2 implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(i + "******************--------");
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        new Thread(()->{
            for(int i = 0; i < 100; i++){
                System.out.println(i + "--------------------");
            }
        }).start();

        new Thread(()->{
            for(int i = 0; i < 100; i++){
                System.out.println("===============" + i);
            }
        }).start();
    }
}
```

![image-20240410212216486](C:\Users\ningn\AppData\Roaming\Typora\typora-user-images\image-20240410212216486.png)

## lambda 表达式

lambda 表达式是函数式编程，将方法的实现作为参数进行传递（普通的编程的参数是变量）

可以简化代码的开发

1、通过实现 Runnable 接口的形式来完成线程的使用

```java
public class MyRunnable implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println("~~~~~~~~~~~" + i + "~~~~~~~~~~~~~~");
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        MyRunnable myRunnable = new MyRunnable();//创建myRunnable对象
        Thread thread = new Thread(myRunnable);
        thread.start();
    }
}
```

2、使用内部类对代码进行简化（在 Test 类里面写实现类接口，两个类写在一起，其中一个是内部类————在类里面的另一个类）

```java
public class Test {
    public static void main(String[] args) {
        MyRunnable3 myRunnable = new MyRunnable3();
        Thread thread = new Thread(myRunnable);
        thread.start();
    }

    static class MyRunnable3 implements Runnable{
        @Override
        public void run() {
            for (int i = 0; i < 100; i++) {
                System.out.println("~~~~~~~~~~~" + i + "~~~~~~~~~~~~~~");
            }
        }
    }
}
```

3、使用匿名内部类进一步进行简化

```java
public class Test {
    public static void main(String[] args) {
        Runnable myRunnable = new Runnable() {//匿名内部类，Runnable是当前类实现的接口类型
            @Override
            public void run() {
                for (int i = 0; i < 100; i++) {
                    System.out.println("~~~~~~~~~~~" + i + "~~~~~~~~~~~~~~");
                }
            }
        };
        Thread thread = new Thread(myRunnable);
        thread.start();
    }
}
```

4、使用 lambda 表达式继续进行简化

```java
public class Test {
    public static void main(String[] args) {
        //外层类不重要，内部核心最重要
        //Thread thread = new Thread(()->{})可以进一步简化
        new Thread(()->{//直接创建Thread对象，把方法传递进来
            for (int i = 0; i < 100; i++) {
                System.out.println("~~~~~~~~~~~" + i + "~~~~~~~~~~~~~~");
            }
        }).start();//调用Thread对象的start()方法
    }
}
```

### 什么情况下使用 lambda 表达式呢？

将接口作为参数传递的场景下，可以使用 lambda 进行简化，将方法作为参数进行传递，不再需要实现接口

```java
public interface MyRunnable3 {
    public void test();
    //public void test2();接口里面的方法只有一个时才可以使用lambda表达式，如果有多个方法时，在参数传递时，就不知道作为参数传递的是哪一个方法。
}
```

```java
public class MyTest {

    public void test(MyRunnable3 myRunnable3){//将接口作为参数传递
        myRunnable3.test();
    }

}
```

```java
public class Test {
    public static void main(String[] args) {
        MyTest myTest = new MyTest();
        myTest.test(()->{//使用lambda表达式，将方法作为参数，连同方法的实现一起用
            System.out.println(111);
        });
    }
}
```

## 线程调度

主动干涉线程的调度

### 线程休眠

休眠是指让当前线程暂停执行，从运行状态进入阻塞状态，从而将 CPU 资源让给其他线程的一种调度方式，通过 sleep 方法来实现。

```java
public static native void sleep(long millis) throws InterruptedException;//long millis 是一个long类型的参数，单位是毫秒，用来指定休眠的时间
```

```java
public class Test {
    public static void main(String[] args) {
        new Thread(()->{
            for (int i = 0; i < 100; i++) {
                if(i == 5){
                    try {
                        Thread.sleep(3000);//休眠3秒钟
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                System.out.println(i + "-----------------");
            }
        }).start();
    }
}
```

在 lambda 表达式里面的 sleep()方法 是定义在 Thread 类中的，所以必须通过类.方法名()的方式去调用。

# 多线程

## 线程合并

合并是指将指定的某个线程加入到当前线程中，合并为一个线程。

由两个线程交替执行变成一个线程中的两个子线程顺序执行，一个线程执行完毕之后再来执行第二个线程，通过 join 方法来实现合并。

线程甲和线程乙，线程甲在执行到某个时间点的时候调用线程乙的 join() 方法，则表示从当前时间点开始 CPU 资源被线程乙独占，执行乙的任务，线程甲进入阻塞状态，直到线程乙执行完毕，线程甲继续获取 CPU 资源执行自己的任务。

谁调用 join，将谁合并到对方的线程中

```java
public class JoinRunnable implements Runnable{//接口
    @override
    public void run(){
        for(int i = 0 ; i < 20; i++>){
            System.out.println(i + "---------------------JoinRunnable");
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) {//主线程类
        JoinRunnable joinRunnable = new JoinRunnable();//构造任务
        Thread thread = new Thread(joinRunnable);//构造线程，把任务传递到线程里面
        thread.start();//启动线程

        for (int i = 0; i < 100; i++) {//主线程在做的任务
            if(i == 10){
                try {
                    thread.join();//
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
            System.out.println(i + "+++++++++++++++++main");
        }
    }
}
```

最后的结果：先两个线程交替进行，在 i=10 开始之后，开始顺序执行，先 thread 的 JoinRunnable 的任务，执行完毕之后，回到 main 方法的主线程执行主线程的任务。

### join() 方法存在重载 join(long millis)

区别？

通过 join 进行合并，则合并进来的线程会一直占用 CPU 资源，直到自己的任务结束才会释放 CPU，另外一个线程才能执行。

通过 join(long millis) 进行合并，则合并进来的线程不会一直占用 CPU 资源，根据 millis 时间来占用，时间到了之后无论线程是否执行完毕，都会将 CPU 释放出来，回到两个线程争夺 CPU 资源的情况，继续交替进行。

```java
public class JoinRunnable implements Runnable{//接口
    @override
    public void run(){
        for(int i = 0 ; i < 20; i++>){
            try{
                Thread.sleep(millis: 1000);//每隔一秒执行一次
            }catch(InterruptedException e){
                e.printStackTrace();
            }
            System.out.println(i + "---------------------JoinRunnable");
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        JoinRunnable joinRunnable = new JoinRunnable();
        Thread thread = new Thread(joinRunnable);
        thread.start();

        for (int i = 0; i < 100; i++) {
            if(i == 10){
                try {
                    thread.join(millis:3000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
            System.out.println(i + "+++++++++++++++++main");
        }
    }
}
```

## 线程休眠

### 通过调用 sleep 方法进行休眠，多线程的场景中，调用 sleep 是让哪个线程休眠？

不是谁调用 sleep 就让谁休眠，而是看在哪调的，在哪个线程中调用 sleep 方法就让哪个线程休眠，和调用者无关。

```java
public class Test {
    public static void main(String[] args) {
        Thread thread = new Thread(()->{
            try {
                Thread.sleep(5000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            for (int i = 0; i < 100; i++) {
                System.out.println(i + "========================");
            }
        });
        thread.start();



        for (int i = 0; i < 100; i++) {
            System.out.println("++++++++++++++++++++++++++++++main" + i);
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Thread thread = new Thread(()->{
            for (int i = 0; i < 100; i++) {
                System.out.println(i + "========================");
            }
        });
        thread.start();

        try {
            Thread.sleep(5000);//在哪个线程中调用的sleep()方法，就让哪个线程休眠；此时，是在main方法的主线程里面调用的
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        for (int i = 0; i < 100; i++) {
            System.out.println("++++++++++++++++++++++++++++++main" + i);
        }
    }
}
```

## 线程同步

多线程同时访问同一个资源，可能会导致数据不准确的情况出现，所以需要通过线程同步来解决这一问题。

代码举例

```java
public class Account implements Runnable {

    private static int num;

    @Override
    public void run() {
        num++;
        try {
            Thread.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println(Thread.currentThread().getName() + "是当前的第" + num + "位访客");
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Account account = new Account();
        Thread t1 = new Thread(account, "线程1")；
        Thread t2 = new Thread(account, "线程2")；
        t1.start();
        t2.start();
    }
}
```

强行休眠的时候，无论如何，最终输出的结果都会是第二位访客。如何解决呢？通过线程同步

### 同步和异步的区别

同步是指多个线程按顺序一个接一个执行，排队执行

异步是指多个线程同时执行

通过给目标方法加锁 synchronized 的方式来解决

```java
public class Account implements Runnable {

    private static int num;//因为是静态变量相当于只有一份共享资源

    @Override
    public synchronized void run() {//synchronized关键字
        num++;
        try {
            Thread.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println(Thread.currentThread().getName() + "是当前的第" + num + "位访客");
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Account account = new Account();
        Thread t1 = new Thread(account, "线程1")；
        Thread t2 = new Thread(account, "线程2")；
        t1.start();
        t2.start();
    }
}
```

最终输出的结果：
线程 1 是当前的第 1 位访客
线程 2 是当前的第 2 位访客

synchronized 关键字 可以修饰实例方法，也可以修饰静态方法，但是两者在使用上是有区别的

上锁前

```java
public class SynchronizedTest {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            Thread thread = new Thread(()->{//创建5个线程对象
                SynchronizedTest.test();
            });
            thread.start();//5个thread同时输出
        }
    }

    public static void test(){
        System.out.println("start...");
        try {
            Thread.sleep(1000);//5个thread同时输出后，休眠1秒
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("end...");//然后5个thread同时输出end
    }
}
```

上锁后

```java
public class SynchronizedTest {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            Thread thread = new Thread(()->{//创建5个线程对象
                SynchronizedTest.test();
            });
            thread.start();//5个thread同时输出
        }
    }

    public synchronized static void test(){//最后输出的结果：start输出后，等待一秒，输出end,再等待一秒，输出start后，等待一秒，输出end。。。是一个接一个的执行
        System.out.println("start...");
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("end...");
    }
}
```

```java
/*
    public synchronized void test(){//非静态方法上锁后，也不会一个接一个的执行，因为静态方法在内存中只有一个，相当于一个类，（现实举例：多人排队等一个厕所）而非静态方法相当于一个对象，五个thread线程对象相当于五个厕所，不需要一个一个的执行，不需要排队。
        System.out.println("start...");
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("end...");
    }
}
*/
```

如何判断多个线程是否会实现同步，看锁定的资源在内存中有几份，如果只有一份，多线程肯定需要排队抢这份唯一的资源，如果有多份，则多线程不需要排队，就不会实现同步。

synchronized 还可以修饰代码块，会为代码块加上锁，从而实现同步

```java
public class SynchronizedTest {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            Thread thread = new Thread(()->{
                SynchronizedTest.test();
            });
            thread.start();
        }
    }

    public synchronized static void test(){
        synchronized(SynchronizedTest.class){//此时锁定的是类，在内存中只有一份
        System.out.println("start...");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("end...");
        }

        System.out.println("start...");
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("end...");
    }
}
```

代码举例，理解代码：synchronized 只能修饰只有一份的资源
举例 1

```java
public class SynchronizedTest {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            Thread thread = new Thread(()->{
                SynchronizedTest.test();
            });
            thread.start();
        }
    }

    public void test(){
        synchronized(this){//此时锁定的是this关键字，是当前的对象，有5个
        System.out.println("start...");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("end...");
        }

        System.out.println("start...");
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("end...");
    }
}
```

举例 2

```java
public class SynchronizedTest {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            Thread thread = new Thread(()->{
                SynchronizedTest.test(new String("abc"));//new了5次
            });
            thread.start();
        }
    }

    public void test(String string){
        synchronized(string){//此时锁定的是string，SynchronizedTest中，有5个string,因此不会同步
        System.out.println("start...");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("end...");
        }

        System.out.println("start...");
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("end...");
    }
}
```

举例 3

```java
public class SynchronizedTest {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            Thread thread = new Thread(()->{
                SynchronizedTest.test("abc");//直接进行赋值
            });
            thread.start();
        }
    }

    public void test(String string){
        synchronized(string){//此时锁定的是string"abc"，在常量池中只有一份，因此会同步
        System.out.println("start...");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("end...");
        }

        System.out.println("start...");
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("end...");
    }
}
```

举例 4

```java
public class SynchronizedTest {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            Thread thread = new Thread(()->{
                SynchronizedTest.test(new Integer(1));//new 出来的内容是多个，并不是唯一一份资源，因此不会同步
            });
            thread.start();
        }
    }

    public void test(Integer integer){
        synchronized(integer){//此时锁定的是string"abc"，在常量池中只有一份，因此会同步
        System.out.println("start...");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("end...");
        }

        System.out.println("start...");
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("end...");
    }
}
```

举例 5

```java
public class SynchronizedTest {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            Thread thread = new Thread(()->{
                SynchronizedTest.test(1);//常量池中的整型数据，唯一，因此会同步
            });
            thread.start();
        }
    }

    public void test(Integer integer){
        synchronized(integer){
        System.out.println("start...");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("end...");
        }

        System.out.println("start...");
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("end...");
    }
}
```

举例 6

```java
public class SynchronizedTest {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            Thread thread = new Thread(()->{
                SynchronizedTest.test(128);//超过了包装类常量池的可用范围，因此不会同步
            });
            thread.start();
        }
    }

    public void test(Integer integer){
        synchronized(integer){
        System.out.println("start...");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("end...");
        }

        System.out.println("start...");
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("end...");
    }
}
```

包装类常量池有一个可用范围：-128~127，在此区间内常量池可用，同一个数值可以给多个线程使用；一旦超出这个范围，则常量池失效，此时就需要单独在堆中创建对应的数据，因此不是一个对象而是多个对象

# 多线程

## 线程安全的单例模式

单例模式，是一种常见的软件设计模式，其核心思想是一个类只有一个实例对象

### 如何实现单例模式

1、禁止通过构造器来创建对象，如何实现？

如何禁止外部调用构造器，把构造器私有化（封装）

单线程模式下举例

```java
public class Account {

    private static Account account; //默认account是null

    private Account(){//第一步：构造器私有化
        System.out.println("创建了Account对象");
    }

    public synchronized static Account getInstance(){//第二步：提供一个共有的方法来提供account，在共有方法里面进行逻辑判断，确保Account只有一个
        if(account == null){
            account = new Account();
        }
        return account;
    }
}
```

```java
public class Test {
    public static void main(String[] args){
        for(int i = 0; i < 100; i++){
            Account instance = Account.getInstance();
        }
    }
}
```

多线程模式下

```java
public class Account {

    private static Account account; //默认account是null

    private Account(){//第一步：构造器私有化
        System.out.println("创建了Account对象");
    }

    public static Account getInstance(){//第二步：提供一个共有的方法来提供account，在共有方法里面进行逻辑判断，确保Account只有一个
        if(account == null){
            account = new Account();
        }
        return account;
    }
}
```

```java
public class Test {
    public static void main(String[] args){
        for(int i = 0; i < 100; i++){//同时有100个线程，由CPU随机分配资源对象去执行进程，因此就不是单例模式
            new Thread(()->{
                Account instance = Account.getInstance();
            }).start();
            Account instance = Account.getInstance();
        }
    }
}
```

2、如何确保对象只有一个

同步指线程的状态，多个线程排队执行，加锁是用来实现同步的方法

```java
public class Account {

    private static Account account; //默认account是null

    private Account(){
        System.out.println("创建了Account对象");
    }

    public synchronized static Account getInstance(){//只有静态方法才能通过类去调用，不需要创建对象了
        if(account == null){
            try {
                Thread.sleep(1);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            account = new Account();
        }
        return account;
    }
}
```

```java
public class Test {
    public static void main(String[] args){
        for(int i = 0; i < 100; i++){//同时有100个线程，由自动创建了多个对象执行，因此就不是单例模式
            new Thread(()->{
                Account instance = Account.getInstance();
            }).start();
            Account instance = Account.getInstance();
        }
    }
}


```

## 死锁

死锁：多个线程因为争夺同一个资源而形成的一种互斥状态，导致每个线程都无法继续进行，程序一直处于卡顿状态
实际开发过程中，应尽量避免死锁。

```java
public class Data {

}
```

```java
public class DeadLockRunnable implements Runnable {
    public int num;
    private static Data data1 = new Data();
    private static Data data2 = new Data();

    @Override
    public void run() {
        //两个人去吃饭，服务员给了只2根筷子，一人一根的情况
        //1号拿着data1，试图获取data2
        //2号拿着data2，试图获取data1
        //谁也不愿意给对方自己的data
        if(num == 1){
            System.out.println(Thread.currentThread().getName() + "获取到了data1，等待获取data2");
            synchronized (data1){//对data1加锁，先拿到1的情况下
                try {
                    Thread.sleep(100);//抢筷子的过程需要1秒
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                synchronized (data2){//尝试拿到data2
                    System.out.println(Thread.currentThread().getName() + "用餐完毕");
                }
            }
        }
        if(num == 2){
            System.out.println(Thread.currentThread().getName() + "获取到了data2，等待获取data1");
            synchronized (data2){//对data2加锁，先拿到1的情况下
                try {
                    Thread.sleep(100);//抢筷子的过程需要0.1秒
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                synchronized (data1){//尝试拿到data1
                    System.out.println(Thread.currentThread().getName() + "用餐完毕");
                }
            }
        }
    }
}
```

```java
public class DeadLockTest {
    public static void main(String[] args) {
        DeadLockRunnable runnable1 = new DeadLockRunnable();//创建任务1
        runnable1.num = 1;
        DeadLockRunnable runnable2 = new DeadLockRunnable();//创建任务2
        runnable2.num = 2;

        //两个互斥的任务
        new Thread(runnable1,"张三").start();
        new Thread(runnable2,"李四").start();
    }
}
```

### 如何避免出现死锁？

```java
public class DeadLockTest {
    public static void main(String[] args) {
        DeadLockRunnable runnable1 = new DeadLockRunnable();
        runnable1.num = 1;
        DeadLockRunnable runnable2 = new DeadLockRunnable();
        runnable2.num = 2;
        new Thread(runnable1,"张三").start();
        try {
            Thread.sleep(1000);//张三拿着data1花了0.1秒去取data2，执行runnable1的任务，main主进程休眠1秒，然后执行runnable1任务，李四拿着data2...
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        new Thread(runnable2,"李四").start();
    }
}
```

## 重入锁

ReentrantLock 是对 synchronized 的升级，synchronized 是通过 JVM 实现，ReentrantLock 是通过 JDK 实现（用方法调用的形式来使用）

重入锁的特点是可以重复上锁

synchronized 是自动上锁，自动解锁，ReentrantLock 是手动上锁，手动解锁，上了几次锁，就要解锁几次。

```java
import java.util.concurrent.locks.ReentrantLock;

public class Account implements Runnable {
    private static int num;
    private ReentrantLock reentrantLock = new ReentrantLock();
    @Override
    public void run() {
        reentrantLock.lock();//手动上锁
        reentrantLock.lock();//手动上锁第二重
        num++;
        try {
            Thread.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println(Thread.currentThread().getName() + "是当前的第" + num + "位访客");
        reentrantLock.unlock();//手动解锁
        reentrantLock.unlock();//手动解锁
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Account account = new Account();
        Thread thread1 = new Thread(account,"张三");
        Thread thread2 = new Thread(account, "李四");
        thread1.start();
        thread2.start();
    }
}
```

ReentrantLock 还具备限时性的特点，指可以判断某个线程在一定时间内能否获取到锁

tryLock(long timeout,TimeUnit unit)

```java
import java.util.concurrent.TimeUnit;
import java.util.concurrent.locks.ReentrantLock;

public class TimeLock implements Runnable {

    private ReentrantLock reentrantLock = new ReentrantLock();

    @Override
    public void run() {
        try {
            if (reentrantLock.tryLock(6, TimeUnit.SECONDS)) {//6秒->线程1和线程2都拿到了锁；3秒->只有线程1拿到了锁
                System.out.println(Thread.currentThread().getName() + "获取到了锁");
                Thread.sleep(5000);//拿到锁保持5秒
            }
        } catch (InterruptedException e) {
            e.printStackTrace();
        } finally {
            if(reentrantLock.isHeldByCurrentThread()){//谁拿走的锁，就解锁谁
                reentrantLock.unlock();
            }
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        TimeLock lock = new TimeLock();
        new Thread(lock,"线程1").start();
        new Thread(lock, "线程2").start();
    }
}
```

## 生产者消费者模式————实现业务分离的协同工作的模式

```java
public class Hamburger {
    private int id;

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public Hamburger(int id) {
        this.id = id;
    }

    @Override
    public String toString() {
        return "Hamburger{" +
                "id=" + id +
                '}';
    }
}
```

```java
public class Container {
    public Hamburger[] array = new Hamburger[6];
    public int index = 0;
    //向容器中添加汉堡
    public synchronized void push(Hamburger hamburger){
        while (index == array.length){
            try {
                this.wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        this.notify();//唤醒资源，执行消费汉堡的任务
        array[index] = hamburger;//第一次加汉堡的时候，用默认index0
        index++;
        System.out.println("生产了一个汉堡：" + hamburger);
    }

    //从容器中取出汉堡
    public synchronized Hamburger pop(){
        while (index == 0){
            try {
                this.wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        this.notify();//唤醒资源，执行生产汉堡的任务
        index--;
        System.out.println("消费了一个汉堡：" + array[index]);
        return array[index];
    }
}
```

```java
public class Producer implements Runnable {
    private Container container = null;

    public Producer(Container container) {
        this.container = container;
    }

    @Override
    public void run() {
        for (int i = 0; i < 30; i++) {
            Hamburger hamburger = new Hamburger(i);
            this.container.push(hamburger);
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```

```java
public class Consumer implements Runnable {
    private Container container = null;

    public Consumer(Container container) {
        this.container = container;
    }

    @Override
    public void run() {
        for (int i = 0; i < 30; i++) {
            this.container.pop();
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Container container = new Container();
        Producer producer = new Producer(container);
        Consumer consumer = new Consumer(container);
        new Thread(producer).start();
        new Thread(producer).start();
        new Thread(consumer).start();
        new Thread(consumer).start();
        new Thread(consumer).start();
    }
}
```

# 多线程

## sleep 和 wait

sleep 和 wait 的功能类似，都是让线程暂停执行任务。

sleep 是 Thread 类提供的方法，wait 是 Object 类提供的方法

sleep 是直接作用于线程对象本身，wait 作用于线程正在访问的资源，即 object 对象以及当前对象本身

调用 A 对象的 wait：让当前正在访问 A 对象的线程休眠，同时它有一个前提，当前线程必须拥有 A 对象，所以 wait 方法只能在同步方法或同步代码块中调用，否则会抛出异常。

wait 释放锁，sleep 不会释放锁。

```java
import java.util.concurrent.TimeUnit;

public class Test {
    public static void main(String[] args) {
        A a = new A();
        new Thread(()->{
            for (int i = 0; i < 10; i++) {
                a.test(i);
            }
        }).start();
    }
}

class A{
    public synchronized void test(int i){
        if(i == 5){
            try {
                this.wait(3000);//i==5时暂停3秒钟后继续执行,wait()来自于A，A继承Object，因此wait()作用的是A
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        try {
            TimeUnit.SECONDS.sleep(1);//==Thread.sleep(millis:1000)；sleep是来自于Thread，因此sleep()作用于线程
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println(i + "---------------");
    }
}
```

i == 5，调用 A 的 wait 方法，会让正在访问 A 的线程休眠，并且永久不会解除阻塞。

如何让线程解除阻塞？

1、指定 wait 的时间，wait(long millis)，millis 毫秒 之后会自动解除阻塞，类似 sleep

wait -》Object

A 继承了 Object，A 中自带 wait 方法

sleep -》Thread

```java
import java.util.concurrent.TimeUnit;

public class Test {
    public static void main(String[] args) {
        A a = new A();
        new Thread(()->{
            for (int i = 0; i < 10; i++) {
                a.test(i);
            }
        }).start();
    }
}

class A{
    public synchronized void test(int i){
        if(i == 5){
            try {
                wait(3000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        try {
            TimeUnit.SECONDS.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println(i + "---------------");
    }
}
```

2、通过调用 notify 方法唤醒线程

```java
import java.util.concurrent.TimeUnit;

public class Test {
    public static void main(String[] args) {
        A a = new A();
        new Thread(()->{
            for (int i = 0; i < 10; i++) {
                a.test(i);
            }
        }).start();

        new Thread(()->{
            try {
                TimeUnit.SECONDS.sleep(7);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            a.test2();
        }).start();
    }
}

class A{
    public synchronized void test(int i){
        if(i == 5){
            try {
                this.wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        try {
            TimeUnit.SECONDS.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println(i + "---------------");
    }

    public synchronized void test2(){
        this.notify();
    }
}
```

无论 wait() 还是 notify() 方法，都必须放到同步方法或者同步代码块中才能正常调用，否则会抛出异常。

## synchronized 锁定的是谁

> 如果 synchronized 修饰非静态方法，即没有 static 修饰的方法属于实例方法也就是属于对象的方法，则锁定的是方法的调用者

```java
import java.util.concurrent.TimeUnit;

public class Test {
    public static void main(String[] args) {
        Data data = new Data();//当前对象的调用者只有一个，也就是说资源只有一份（3个func相当于3个人排队用一个厕所），不加synchronized关键字的方法相当于选择了不文明的方法即不用厕所解决，不需要争抢一个资源
        new Thread(()->{
            data.func1();
        },"A").start();

        try {
            TimeUnit.SECONDS.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        new Thread(()->{
            data.func3();
        },"B").start();
    }
}

class Data {
    public synchronized void func1(){
        try {
            TimeUnit.SECONDS.sleep(3);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("1...");
    }

    public synchronized void func2(){
        System.out.println("2...");
    }

    public void func3(){
        System.out.println("3...");
    }
}
```

首先判断方法是否添加了 synchronized 关键字：（synchronized 锁的是当前对象的调用者）
如果没有添加，则不需要考虑线程同步的问题，输出结果应该是先 3，后 1；
如果添加了，则需要考虑线程同步的问题，怎么考虑呢？
————看当前锁定的资源在内存中有几份，如果只有一份，则多个线程会同步（两个人抢一个厕所，需要排队）；
————如果有多份，则多个线程不需要同步。（两个人，两个厕所，不需要排队）

> 如果 synchronized 修饰的是静态方法，则锁定的是类，无论有多少个对象，都会同步，也就是会同步执行

```java
import java.util.concurrent.TimeUnit;

public class Test {
    public static void main(String[] args) {
        Data data1 = new Data();
        new Thread(()->{
            data1.func1();
        },"A").start();

        try {
            TimeUnit.SECONDS.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        Data data2 = new Data();
        new Thread(()->{
            data2.func2();
        },"B").start();
    }
}

class Data {
    public synchronized static void func1(){
        try {
            TimeUnit.SECONDS.sleep(3);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("1...");
    }

    public synchronized static void func2(){
        System.out.println("2...");
    }
}
```

> 如果 synchronized 静态方法和非静态方法即实例方法同时存在，静态方法锁定的是类，非静态方法即实例方法锁定的是对象,此时不会同步，因为没有争夺同一个资源

```java
import java.util.concurrent.TimeUnit;

public class Test {
    public static void main(String[] args) {
        Data data = new Data();
        new Thread(()->{
            data.func1();
        },"A").start();

        try {
            TimeUnit.SECONDS.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        new Thread(()->{
            data.func2();
        },"B").start();
    }
}

class Data {
    public synchronized static void func1(){
        try {
            TimeUnit.SECONDS.sleep(3);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("1...");
    }

    public synchronized void func2(){
        System.out.println("2...");
    }
}
```

> 如果 synchronized 修饰的是代码块，则锁定的是传入的对象

```java
import java.util.concurrent.TimeUnit;

public class Test2 {
    public static void main(String[] args) {
        Data2 data2 = new Data2();

        for (int i = 0; i < 5; i++) {
            A a = new A();//new出来的内容，在内存里面有多份，因此不需要争抢资源，不会同步
            new Thread(()->{
                data2.func(a);
            }).start();
        }
    }
}

class Data2{
    public void func(A a){
        synchronized (a){
            System.out.println("start...");
            try {
                TimeUnit.SECONDS.sleep(2);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("end...");
        }
    }
}

class A{

}
```

## ConcurrentModificationException 并发修改异常

多个线程对同一个数据进行修改出现的问题

多线程同时进行也就是说交替并发，同时修改，一边读一边写，一定会出现异常。
ArrayList 是线程不安全的集合，当多个线程同时操作集合时，会出现数据不准确的情况

### 如何解决 ConcurrentModificationException？

1、将 ArrayList 替换成线程安全的集合 Vector————效率比较低

```java
public boolean add(E e) {
    ensureCapacityInternal(size + 1);  // Increments modCount!!
    elementData[size++] = e;
    return true;
}

public synchronized boolean add(E e) {
        modCount++;
        ensureCapacityHelper(elementCount + 1);
        elementData[elementCount++] = e;
        return true;
    }
```

2、使用 Collections.synchronizedList（效率略高于第一种 vector）
将 List<String> list = new ArrayList<>();
升级为 List<String> list = Collections.synchronizedList(new ArrayList<>());//相当于把 new arraylist 给包装起来

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Vector;
import java.util.concurrent.TimeUnit;

public class Test {
    public static void main(String[] args) {
        List<String> list = Collections.synchronizedList(new ArrayList<>());
        for (int i = 0; i < 10; i++) {
            new Thread(()->{
                try {
                    TimeUnit.MILLISECONDS.sleep(1);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                list.add("a");
                System.out.println(list);
            }).start();
        }
    }
}
```

3、使用 JUC 工具类 CopyOnWriteArrayList（写时复制）————效率高，推荐这种解决方案
java.util.concurrent
java.util.concurrent JDK 的一个包，存放都是关于多线程并发的很多个工具类

写时复制
将 List<String> list = new ArrayList<>();
升级为 List<String> list = new CopyOnWriteArrayList<>();

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.concurrent.CopyOnWriteArrayList;
import java.util.concurrent.TimeUnit;

public class Test {
    public static void main(String[] args) {
        List<String> list = new CopyOnWriteArrayList<>();
        for (int i = 0; i < 10; i++) {
            new Thread(()->{
                try {
                    TimeUnit.MILLISECONDS.sleep(1);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                list.add("a");
                System.out.println(list);
            }).start();
        }
    }
}
```

CopyOnWrite 写时复制，当我们往一个容器中添加元素的时候，不直接往当前容器中直接添加，
而是将当前容器进行复制，复制成一个新容易，向新容器中添加元素，添加完成之后，再将原容器的引用指向新的容器。

CopyOnWrite 方法的实现

```java
public boolean add(E e) {
    final ReentrantLock lock = this.lock;
    lock.lock();//上锁
    try {
        Object[] elements = getArray();//获取原数组
        int len = elements.length;//获取数组的长度
        Object[] newElements = Arrays.copyOf(elements, len + 1);//复制原数组，并且新数组的长度是原数组长度+1
        newElements[len] = e;//给新数组添加新元素
        setArray(newElements);//创建新数组完成
        return true;
    } finally {
        lock.unlock();//解锁
    }
}
```

可以对 CopyOnWrite 容器进行并发的读，而不需要加锁，因为当前容器不会添加任何元素，添加元素都是针对复制出来的新集合进行操作，所以 CopyOnWrite 容器也是一种读写分离的思想，读和写操作的是不同的容器。在对数据库进行操作的时候经常使用。

# JUC 并发编程工具包

JUC 常用工具类

## CountDownLatch

减法计数器，JUC 的一个工具类，可以用来倒计时，当两个线程同时执行时，如果我们要确保一个线程优先执行

方法原理：设置一个计数器，当计数器清零的时候，再执行另一个线程

```java
import java.util.concurrent.CountDownLatch;

public class CountDownLatchTest {
    public static void main(String[] args) {
        CountDownLatch countDownLatch = new CountDownLatch(100);
        new Thread(()->{
            for (int i = 0; i < 100; i++) {
                System.out.println("++++++++++++++++++++++Thread");
                countDownLatch.countDown();
            }
        }).start();

        try {
            countDownLatch.await();//等100倒数为0时才会执行下一个代码块
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        for (int i = 0; i < 100; i++) {
            System.out.println("main------------------------");
        }
    }
}
```

## CyclicBarrier

加法计数器

```java
import java.util.concurrent.BrokenBarrierException;
import java.util.concurrent.CyclicBarrier;

public class CyclicBarrierTest {
    public static void main(String[] args) {
        CyclicBarrier cyclicBarrier = new CyclicBarrier(10,()->{//cb调用10次后输出“放行”一次，然后清零一次，再次执行
            System.out.println("放行");
        });

        for (int i = 0; i < 30; i++) {
            final int temp = i;
            new Thread(()->{//开启了十个线程
                System.out.println("-->" + temp);//把0到9输出后，输出放行
                try {
                    cyclicBarrier.await();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                } catch (BrokenBarrierException e) {
                    e.printStackTrace();
                }
            }).start();
        }

    }
}
```

## Semaphore

计数信号量，实际开发中主要用来完成限流操作，即限制可以访问某些资源的线程数量。
应用场景：大客流量网红店一定时间内限制进店客人人数

- 初始化
- 获得许可
- 释放

```java
import java.util.concurrent.Semaphore;
import java.util.concurrent.TimeUnit;

public class SemaphoreTest {
    public static void main(String[] args) {
        Semaphore semaphore = new Semaphore(5);//初始化，限流5人
        for (int i = 0; i < 15; i++) {
            new Thread(()->{
                try {
                    semaphore.acquire();//获得许可
                    System.out.println(Thread.currentThread().getName() + "进店购物");
                    TimeUnit.SECONDS.sleep(2);//进店两秒后出店
                    System.out.println(Thread.currentThread().getName() + "出店");
                } catch (InterruptedException e) {
                    e.printStackTrace();
                } finally {
                    semaphore.release();//释放资源
                }
            },String.valueOf(i)).start();//给每个线程命名
        }
    }
}
```

## 读写锁

接口 ReadWriteLock，实现类 ReentrantReadWriteLock，可以支持多线程同时读，但是同一时间只能有一个线程进行写入操作。

读写锁功能也是为了实现线程同步，只不过粒度更细，可以分别给读和写操作设置不同的锁机制。

```java
import java.util.HashMap;
import java.util.Map;
import java.util.concurrent.locks.ReadWriteLock;
import java.util.concurrent.locks.ReentrantReadWriteLock;

public class ReadWriteLockTest {
    public static void main(String[] args) {
        Cache cache = new Cache();
        for (int i = 0; i < 5; i++) {
            final int temp = i;
            new Thread(()->{
                cache.write(temp, String.valueOf(temp));
            }).start();
        }

        for (int i = 0; i < 5; i++) {
            final int temp = i;
            new Thread(()->{
                cache.read(temp);
            }).start();
        }
    }
}

class Cache{
    private Map<Integer,String> map = new HashMap<>();
    ReadWriteLock lock = new ReentrantReadWriteLock();

    //写操作
    public void write(Integer key,String value){
        lock.writeLock().lock();
        System.out.println(key + "开始写入");
        map.put(key, value);
        System.out.println(key + "写入完毕");
        lock.writeLock().unlock();
    }

    //读操作
    public void read(Integer key){
        lock.readLock().lock();
        System.out.println(key + "开始读取");
        map.get(key);
        System.out.println(key + "读取完毕");
        lock.readLock().unlock();
    }
}
```

加注释版

```java
import java.util.HashMap;
import java.util.Map;
import java.util.concurrent.locks.ReadWriteLock;
import java.util.concurrent.locks.ReentrantReadWriteLock;

public class ReadWriteLockTest {
    public static void main(String[] args) {
        Cache cache = new Cache();

        for (int i = 0; i < 5; i++) {
            final int temp = i;
            new Thread(()-> {
                cache.write(temp, String.valueOf(temp));// 调用写入 方法把值转为String类型写进去
            }).start();
        }


        for (int i = 0; i < 5; i++) {//同时5个方法同时读
            final int temp = i;
            new Thread(()-> {
                cache.read(temp); //调用读 方法
            }).start();
        }
    }
}


class Cache{
    private Map<Integer, String> map = new HashMap<>();
    ReadWriteLock lock = new ReentrantReadWriteLock();
    //写操作
    public void write(Integer key, String value){
        lock.writeLock().lock();//拿到写 的资源并且锁起来
        System.out.println(key + "开始写入");
        map.put(key, value);
        System.out.println(key + "写入完毕");
        lock.writeLock().unlock();//释放锁
    }

    //读操作
    public void read(Integer key){
        lock.readLock().lock();//上锁
        System.out.println(key + "开始读取");
        map.get(key);
        System.out.println(key + "读取完毕");
        lock.readLock().unlock();//释放锁
    }
}
```

## 线程池

预先创建好一定数量的线程对象，存入缓冲池，需要用的时候直接从缓冲池中取出，用完之后不要销毁，还回到缓冲池中，供下一次任务使用。
举例：相当于把一个大的任务拆分成很多个小的任务，需要做几个小任务，就拿走几个小任务，任务完成后，返还资源。

优点：

- 提高线程的利用率（让一个员工做多个任务，而不是一个员工只做一个任务，做完就解雇对方）
- 提高响应速度（开掉做完任务的员工，再次招聘新员工做新的任务也很花时间）
- 便于统一管理线程对象（线程池相当于存有很多个任务单的抽屉，当有新的任务的时候，再增加新的任务单即可）
- 可控制最大并发量（一共 10 个任务单，不可能来多少任务就做多少，而是最多做 10 个任务）

工作流程：

- 初始化线程池，创建默认数量的线程对象，如：默认开放两个柜台
- 当任务过多的时候，额外补充线程数量，如：当等候区人员过多的时候，根据等候人员的数量状况，增加开放的柜台（休假人员召回来上半天忙期的班），最多创建指定的最大数量上限的柜台即线程
- 当任务趋于正常的时候，额外补充的线程会自动销毁，如：
  现实案例：
  1. 去银行办理业务，银行有 5 个柜台，但是有两个柜台开放了，另外三个没有开放；
  2. 当开放的柜台达到最大数量 5，且等候区人员超过规定的数量的时候，新来的客户就拿不到号码牌，不能进入等候区，也不能办理业务；
  3. 当下午时段不忙的时候，临时开放的柜台即临时创建/补充的线程就进行销毁。

初始化线程数量

最大线程数量

线程池的实现有 3 种方式

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class Test {
    public static void main(String[] args) {
        //单例线程池，只有一个线程对象
//        ExecutorService executorService = Executors.newSingleThreadExecutor();

        //指定长度
//        ExecutorService executorService = Executors.newFixedThreadPool(10);//10个线程，一人一个线程

        //每台电脑的最大线程数不同
        ExecutorService executorService = Executors.newCachedThreadPool();
        for (int i = 0; i < 100; i++) {//输出的数字A-数字B中，数字A的最大值就是线程的数量
            final int temp = i;
            executorService.execute(()->{
                System.out.println(Thread.currentThread().getName() + ":" + temp);
            });
        }
        executorService.shutdown();
    }
}
```

ThreadPoolExecutor 是线程池的原生类
不同的 7 个参数创建不同的线程池

### 核心参数：

最大线程负荷=参数 2 最大线程数+参数 5 阻塞队列数值
参数 1：corePoolSize--核心池的大小=初始化的线程数
参数 2：maximunPoolSize--最大线程数
参数 3：keepAliveTime--空闲线程的存活时间（如：空闲 10 秒后进行销毁的话，此处设置为 10）
参数 4：unit--时间单位（如：空闲 10 秒后进行销毁的话，此处设置为 秒）
参数 5：workQueue--阻塞队列（如：银行的等候区）
参数 6：threadFactory--线程工厂（用来创建线程）//有默认值，一般不用写
参数 7：handler--拒绝策略（如：线程已达到最大数量，等候区已满，此时就要拒绝对方）//有默认值，一般不用写

```java
public static ExecutorService newSingleThreadExecutor() {
    return new FinalizableDelegatedExecutorService
        (new ThreadPoolExecutor(1, 1,
                                0L, TimeUnit.MILLISECONDS,
                                new LinkedBlockingQueue<Runnable>()));//永远只能有一个，即单例模式
}
```

```java
public static ExecutorService newFixedThreadPool(int nThreads) {//传进来的int型 nThreads的参数是几就说明最大有几个线程，假如nThreads=5，说明初始化队列是5个，最大线程数也是5个
    return new ThreadPoolExecutor(nThreads, nThreads,
                                  0L, TimeUnit.MILLISECONDS,//不进行空闲线程销毁
                                  new LinkedBlockingQueue<Runnable>());
}
```

```java
public static ExecutorService newCachedThreadPool() {
    return new ThreadPoolExecutor(0, Integer.MAX_VALUE,//默认缓存线程是0个，理论上没有最大线程数限制，存活时间60秒
                                  60L, TimeUnit.SECONDS,
                                  new SynchronousQueue<Runnable>());
}
```

ThreadPoolExecutor 线程池的原生类

核心参数：

- corePoolSize：核心池大小
- maximumPoolSize：线程池最大线程数
- keepAliveTime：空闲线程的存活时间
- unit：时间单位
- workQueue：阻塞队列
- threadFactory：线程工厂
- handler：拒绝策略

代码优化

```java
import java.util.concurrent.*;

public class Test {
    public static void main(String[] args) {
        //最开始初始化的柜台有两个，对大开放柜台数5个，等候区3个位置。
        ExecutorService executorService = new ThreadPoolExecutor(2,5,1L,
                TimeUnit.SECONDS,new ArrayBlockingQueue<>(3), Executors.defaultThreadFactory(), new ThreadPoolExecutor.AbortPolicy());
        for (int i = 0; i < 9; i++) {
            //来了第6个人的时候，会开放第三个柜台，第7个人的时候，开放第4个柜台，第8个人开放柜台5，
            // 第9个人直接拒绝，因为所有人>最大线程数即柜台总数+等候区人数了，超出负荷就办不了业务会抛出异常concurrent.RejectedExecutionException
            executorService.execute(()->{//现在办理的业务
                try {
                    TimeUnit.MILLISECONDS.sleep(100);//办理现在的业务需要0.1秒
                } catch (InterruptedException e) {
                    throw new RuntimeException(e);
                }
                System.out.println(Thread.currentThread().getName() + "办理业务");//打印业务名
            });
        }
        executorService.shutdown();//释放资源
    }
}
```

# JUC

## ForkJoin 框架

ForkJoin 框架是 JDK1.7 之后提供的一个多线程并发处理框架，本质上是对线程池的一种补充，它的核心思想是将一个大型任务拆分成多个小任务，分别执行，最终将小任务的结果进行汇总，形成最终的结果。

拆分

多个任务 + 多个线程

- ForkJoinTask 表示任务
- ForkJoinPool 表示线程（线程池的一种扩展）

## 递归

什么是递归？

定义：编程语言中，函数直接或间接调用函数本身，则该函数称为递归，一个方法自己调自己

电影院求自己是第几排的问题，递推公式：

```java
f(n) = f(n-1)+1,f(1)=1
```

递归代码：

```java
int f(int n){
    if(n==1) return 1;
	return f(n-1)+1;
}
```

递归需要满足 3 要素：

1、一个父问题可以拆分成若干个子问题，并且若干个子问题的结果汇总起来就是父问题的结果

2、父问题和子问题，解题思路完全一致，只是数据规模不同

3、存在终止条件

假如有 n 个台阶，每次你可以跨 1 个台阶或者 2 个台阶，请求 n 个台阶一共有多少种走法？

可以根据第一步的走法将所有走法分为两类

第一类是第一步走了一个台阶，第二类是第一步走了两个台阶

n 个台阶的走法就等于先走 1 个台阶后，n-1 个台阶的走法 + 先走 2 个台阶，n-2 个台阶的走法

递推公式：

```
f(1) = 1
f(2) = 2
f(n) = f(n-1) + f(n-2)
```

终止条件

f(1) = 1

f(2) = 2

n = 1,f(1) =1

n = 2,f(2) = 2

n = 3,f(3) = f(2) + f(1) = 3

n = 4,f(4) = f(3) + f(2) = 5

递归代码：

```java
int f(int n){
	if(n == 1) return 1;
	if(n == 2) return 2;
	return f(n-1) + f(n-2);
}
```

1、创建一个 ForkJoinTask 任务，ForkJoinTask 是一个抽象类，需要创建一个类来继承 ForkJoinTask 的子类 RecursiveTask，实现抽象方法 compute，拆分的逻辑就写在 compute 方法中。

2、任务要通过 ForkJoinPool 来执行，将任务直接放入 ForkJoinPool 中，直接获取结果即可。

计算 0~20 亿数字相加之和

```java
import java.util.concurrent.RecursiveTask;

public class ForkJoinDemo extends RecursiveTask<Long> {

    private Long start;
    private Long end;
    private Long temp = 100_0000L;

    public ForkJoinDemo(Long start,Long end){
        this.start = start;
        this.end = end;
    }

    @Override
    protected Long compute() {
        if((end - start) < temp){
            Long sum = 0L;
            for (Long i = start;i<=end;i++){
                sum += i;
            }
            return sum;
        } else {
            Long avg = (start + end)/2;
            ForkJoinDemo task1 = new ForkJoinDemo(start, avg);
            task1.fork();
            ForkJoinDemo task2 = new ForkJoinDemo(avg+1, end);
            task2.fork();
            return task1.join() + task2.join();
        }
    }
}
```

```java
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ForkJoinPool;
import java.util.concurrent.ForkJoinTask;

public class Test {
    public static void main(String[] args) {
        Long startTime = System.currentTimeMillis();
        ForkJoinPool forkJoinPool = new ForkJoinPool();
        ForkJoinTask<Long> task = new ForkJoinDemo(0L, 20_0000_0000L);
        forkJoinPool.execute(task);
        Long sum = 0L;
        try {
            sum = task.get();
        } catch (InterruptedException e) {
            e.printStackTrace();
        } catch (ExecutionException e) {
            e.printStackTrace();
        }
        Long endTime = System.currentTimeMillis();
        System.out.println(sum + ",耗时" + (endTime - startTime) + "毫秒");
    }
}
```

## volatile 关键字

```java
public class SingletonDemo {
    private volatile static SingletonDemo instance;
    public SingletonDemo(){
        System.out.println("创建了一个SingletonDemo对象");
    }
    public static SingletonDemo getInstance(){
        if(instance == null){
            synchronized (SingletonDemo.class){
                if(instance == null) {
                    instance = new SingletonDemo();
                }
            }
        }
        return instance;
    }
}
```

volatile 关键字的作用是可以使内存中的数据对线程可见

Java 内存模型 JMM Java Memory Model

一个线程在访问内存数据的时候，其实不是拿到数据本身，而是将数据复制保存到工作内存中，相当于使用的是一个副本，对工作内存中的数据进行修改，修改完成之后再保存到主内存中，主内存对线程不可见。

```java
import java.util.concurrent.TimeUnit;

public class Test3 {
    private static int num = 0;
    public static void main(String[] args) {
        new Thread(()->{
            while (num == 0){

            }
        }).start();

        try {
            TimeUnit.SECONDS.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        num = 1;
        System.out.println(num);
    }
}
```

结果输出 1，但是循环没有停止，因为主内存对线程不可见，子线程从主内存中取出 num=0 放入到工作内存，主线程也从主内存中取出 num = 0 放入工作内存，执行 num = 1，然后将 num = 1 还回到主内存中，但是此时，子线程的工作内存中的 num = 0，所以循环不会结束。

```java
import java.util.concurrent.TimeUnit;

public class Test3 {
    private static volatile int num = 0;//加上volatile关键字
    public static void main(String[] args) {
        new Thread(()->{
            while (num == 0){
                System.out.println("---Thread---");
            }
        }).start();

        try {
            TimeUnit.SECONDS.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        num = 1;
        System.out.println(num);
    }
}
```

# 集合框架

什么是集合？

多个对象，个数未知，类型未知

集合可以简单理解为一个长度可以改变，可以保存任意数据类型的动态数组

在 Java 中，集合不是由一个类来完成的，而是由一组接口和类共同构成了一个框架体系，大致可分为 3 层，最上层是一组接口，继而是接口的实现类，接下来就是对集合各种操作的工具类

| 接口         | 描述                                                                                   |
| ------------ | -------------------------------------------------------------------------------------- |
| Collection   | 集合框架最基础的接口，一个 Collection 存储一组无序、不唯一的对象，一般不直接使用该接口 |
| List         | Collection 的子接口，存储一组有序、不唯一的对象，开发中常用的接口之一                  |
| Set          | Collection 的子接口，存储一组无序、唯一的对象                                          |
| Map          | 独立于 Collection 的另外一个接口，存储一组键值对象、提供键到值的映射                   |
| Iterator     | 专用用来输出集合元素的接口，一般适用于无序集合，从前向后单向输出元素                   |
| ListIterator | Iterator 的子接口，可以双向输出集合中的元素                                            |
| Enumeration  | 传统的输出接口，已经被 Iterator 所取代                                                 |
| SortedSet    | Set 的子接口，可以对集合中的元素进行排序                                               |
| SortedMap    | Map 的子接口，可以对集合中的键值元素进行排序                                           |
| Queue        | 队列接口，此接口的实现类可以实现队列操作                                               |
| Map.Entry    | Map 的内部接口，描述 Map 中的一个键值对元素                                            |

# 集合

## Collection 接口

Collection 是集合框架中最基础的父接口，可以存储一组无序、不唯一的对象

Iterable 专门用来迭代，把集合中的元素全部取出来

Collection 中的所有元素可以通过 Iterator 进行迭代（List、Set）

Collection 常用方法

| 方法                              | 描述                                   |
| --------------------------------- | -------------------------------------- |
| int size()                        | 获取集合长度                           |
| boolean isEmpty()                 | 判断集合是否为空                       |
| boolean contains(Object o)        | 判断集合中是否包含某个元素             |
| Iterator<E> iterator()            | 实例化 Iterator 接口，遍历集合         |
| Object[] toArray()                | 将集合转换为一个 Object 类型的对象数组 |
| boolean add(E e)                  | 向集合中添加元素                       |
| boolean remove(Object o)          | 从集合中移除元素                       |
| boolean containsAll(Collection c) | 判断集合中是否存在某个集合的所有元素   |
| boolean addAll(Collection c)      | 向集合中添加某个集合的所有元素         |
| boolean removeAll(Collection c)   | 从集合中移除满足条件的另一个集合       |
| void clear()                      | 清空集合                               |
| boolean equals(Object o)          | 比较两个集合是否相等                   |
| int hashCode()                    | 获取集合对象的散列值                   |

## Collection 的子接口

使用其子接口

- List：存放有序、不唯一的元素
- Set：存放无序、唯一的元素
- Queue：队列接口

## List 接口

List 接口在继承 Collection 接口的基础上进行了扩展，常用的扩展方法

| 方法                                       | 描述                               |
| ------------------------------------------ | ---------------------------------- |
| E get(int index)                           | 通过下标获取集合中指定位置的元素   |
| E set(int index,E element)                 | 替换集合中指定位置的元素           |
| void add(int index.E element)              | 向集合中的指定位置添加元素         |
| E remove(int index)                        | 通过下标删除集合中指定位置的元素   |
| int indexOf(Object o)                      | 查找某个对象在集合中的下标         |
| int lastIndexOf(Object o)                  | 从后向前查找某个对象在集合中的下标 |
| ListIterator<E> listIterator()             | 实例化 ListIterator 接口           |
| List<E> subList(int fromIndex,int toIndex) | 获取集合中的子集合                 |

## List 接口的实现类

ArrayList 实现了长度可变的数组

优点：查找快，因为元素都是连续的，可以通过公式快速求出下标从而取出元素

缺点：增删慢，因为元素都是连续的，添加一个元素，就必须先将后续的元素依次后移一位，再把新元素加入，删除同理

```java
toString()方法重写
public String toString() {
    Iterator<E> it = iterator()
    if (! it.hasNext())
        return "[]";

    StringBuilder sb = new StringBuilder();
    sb.append('[');
    for (;;) {
        E e = it.next();
        sb.append(e == this ? "(this Collection)" : e);
        if (! it.hasNext())
            return sb.append(']').toString();
        sb.append(',').append(' ');
    }
}
```

ArrayList 常用方法

```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class Test {
    public static void main(String[] args) {
        ArrayList list = new ArrayList();
        list.add("Hello");
        list.add("World");
        list.add("JavaSE");
        list.add("JavaME");
        list.add("JavaEE");
        System.out.println(list.toString());
        System.out.println(list.size());
        System.out.println(list.contains("Java"));
        Iterator iterator = list.iterator();
        while (iterator.hasNext()){
            Object next = iterator.next();
            System.out.println(next);
        }
        System.out.println("********************************");
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }
        list.remove(0);
        System.out.println("*************************************");
        System.out.println(list);
        list.remove("JavaSE");
        System.out.println(list);
        list.add("a");
        System.out.println(list);
        list.add(1, "b");
        System.out.println(list);
        list.set(1, "c");
        System.out.println(list);
        System.out.println(list.indexOf("cc"));
        List list1 = list.subList(1, 3);
        System.out.println(list1);
    }
}
```

注释

```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class Test {
    public static void main(String[] args) {
        ArrayList list = new ArrayList();
        list.add("Hello");
        list.add("World");
        list.add("JavaSE");
        list.add("JavaME");
        list.add("JavaEE");
//      方式1：通过list直接打印出所有的值
        System.out.println(list);
//        默认调用了 toString方法，如下
//        System.out.println(list.toString());
        System.out.println(list.size());
        System.out.println(list.contains("Java"));
//      方式2：通过迭代器进行迭代的方式获取list里面的值
        Iterator iterator = list.iterator();
        while (iterator.hasNext()) {
            Object next = iterator.next();
            System.out.println(next);
        }
//      方式3：通过for循环获取list中的值
        System.out.println("******************");
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }

//      通过remove位置的方式移除某一个坐标的值
        list.remove(0);
        System.out.println("******************");
        System.out.println(list);

//      通过指定remove某一个元素的方式直接移除某一个值
        list.remove("JavaSE");
        System.out.println(list);
        System.out.println("******************");

//      给集合最后的位置追加一个元素
        list.add("a");
        System.out.println(list);
        System.out.println("******************");

//      在指定的位置，追加一个元素，原位置以及其后的元素整体后移
        list.add(1,"b");
        System.out.println(list);
        System.out.println("******************");

//      替换掉指定位置的元素
        list.set(1,"c");
        System.out.println(list);
        System.out.println("******************");

        //获取存在的元素的下表
        list.indexOf("c");
        System.out.println(list);
        //获取不存在元素的下标，会返回-1
        System.out.println(list.indexOf("cc"));

        //截取下标1~3的元素设置为子集合list1,此时是左开右闭的[1, 3)，即>=1,同时<3的下标的范围
        List list1 = list.subList(1,3);
        System.out.println(list1);
    }
}

```

LinkedList 采用链表即后继指针的形式来存储数据，和 ArrayList 恰好相反

优点：增删快

缺点：查询慢

```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.LinkedList;
import java.util.List;

public class Test {
    public static void main(String[] args) {
        LinkedList list = new LinkedList();
        list.add("Hello");
        list.add("World");
        list.add("Java");
        System.out.println(list);
        list.offer("JavaSE");
        list.offer("JavaSE2");
        System.out.println(list);
        list.push("JavaME");
        System.out.println(list);
        list.addFirst("JavaME2");
        System.out.println(list);
        System.out.println(list.peekFirst());
        System.out.println(list.peekLast());
        System.out.println(list);
        System.out.println(list.pollFirst());
        System.out.println(list.pollLast());
        System.out.println(list);
    }
}
```

注解

```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.LinkedList;
import java.util.List;

public class Test {
    public static void main(String[] args) {
        //创建链表对象
        LinkedList list = new LinkedList();
        //向链表末位追加元素
        list.add("Hello");
        list.add("World");
        list.add("Java");
        System.out.println(list);

        //向链表末位追加元素
        list.offer("JavaSE");
        list.offer("JavaSE2");
        System.out.println(list);

        //向链表首位追加元素
        list.push("JavaME");
        System.out.println(list);

        //向链表首位追加元素
        list.addFirst("JavaME2");
        System.out.println(list);

        //读出链表首位元素,不更改链表的元素列表本身
        System.out.println(list.peekFirst());
        //读出末位元素，不更改链表的元素列表本身
        System.out.println(list.peekLast());

        //取出链表的首位元素，更改链表的元素列表
        System.out.println(list.pollFirst());
        //取出链表的末位元素，更改链表的元素列表
        System.out.println(list.pollLast());
        System.out.println(list);

    }
}
```

## Set 接口

Set 接口是 Collection 的子接口，Set 接口以散列的形式存储数据，所以元素是无序的，可以存储一组无序且唯一的对象。

## Set 接口的实现类

HashSet 存储一组无序且唯一的元素，这里的无序是指元素的存储顺序和遍历顺序不一致。

```java
import java.util.*;

public class Test {
    public static void main(String[] args) {
        HashSet hashSet = new HashSet();
        hashSet.add("Hello");
        hashSet.add("World");
        hashSet.add("Java");
        hashSet.add("Hello");
        System.out.println(hashSet.size());
        Iterator iterator = hashSet.iterator();
        while (iterator.hasNext()){
            System.out.println(iterator.next());
        }
        hashSet.remove("World");
        Iterator iterator1 = hashSet.iterator();
        while (iterator1.hasNext()){
            System.out.println(iterator1.next());
        }
    }
}
```

LinkedHashSet 是 Set 的另外一个子接口，可以存储一组有序且唯一的元素，这里的有序是指元素的存储顺序和遍历顺序是一致。

```java
import java.util.*;

public class Test {
    public static void main(String[] args) {
        LinkedHashSet set = new LinkedHashSet();
        set.add("Hello");
        set.add("World");
        set.add("Java");
        set.add("Hello");
        System.out.println(set.size());
        Iterator iterator = set.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
        set.remove("World");
        System.out.println(set);
    }
}
```

```java
import java.util.*;

public class Test {
    public static void main(String[] args) {
        LinkedHashSet set = new LinkedHashSet();
        set.add(new A(1));
        set.add(new A(1));
        Iterator iterator = set.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
    }
}

class A{
    private int num;

    public A(int num) {
        this.num = num;
    }

    @Override
    public String toString() {
        return "A{" +
                "num=" + num +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        A a = (A) o;
        return num == a.num;
    }

    @Override
    public int hashCode() {
        return Objects.hash(num);
    }
}
```

TreeSet 存储一组有序、唯一的元素，TreeSet 的有序和 LinkedHashSet 的有序不一样。

LinkedHashSet 的有序是指元素的存储顺序和遍历顺序一致，TreeSet 的有序是指集合内部会自动给所有的元素按照升序进行排列。

```java
import java.util.*;

public class Test {
    public static void main(String[] args) {
        TreeSet treeSet = new TreeSet();
        treeSet.add(new A(1));
        treeSet.add(new A(3));
        treeSet.add(new A(6));
        treeSet.add(new A(2));
        treeSet.add(new A(5));
        treeSet.add(new A(4));
        treeSet.add(new A(1));
        Iterator iterator = treeSet.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
    }
}

class A implements Comparable{
    private int num;

    public A(int num) {
        this.num = num;
    }

    /**
     * A.compareTo(B)
     * 1表示A大于B
     * 0表示A等于B
     * -1表示A小于B
     * @param o
     * @return
     */
    @Override
    public int compareTo(Object o) {
        A a = (A)o;
        if(this.num < a.num){
            return 1;
        }
        if(this.num > a.num){
            return -1;
        }
        return 0;
    }

    /**
     *  @Override
    //升序
//    public int compareTo(Object o) {
//        A a = (A) o;
//        if (this.num > a.num) {
//            return 1;
//        }
//
//        if (this.num < a.num) {
//            return -1;
//        }
//        return 0;
//    }

    //降序
    public int compareTo(Object o) {
        A a = (A) o;
        if (this.num < a.num) {
            return 1;
        }

        if (this.num > a.num) {
            return -1;
        }
        return 0;
    }
    */

    @Override
    public String toString() {
        return "A{" +
                "num=" + num +
                '}';
    }
}
```

## Map 接口

Map 接口是与 Collection 接口完全独立的另一个体系。

区别在于 Set、List、Collection 只能操作单个元素，Map 可以操作一对元素，Map 中的元素都是以 key-value 的形式进行存储的。

| 方法                                | 描述                              |
| ----------------------------------- | --------------------------------- |
| int size()                          | 获取集合长度                      |
| boolean isEmpty()                   | 判断集合是否为空                  |
| boolean containsKey(Object key)     | 判断集合中是否存在 key            |
| boolean containsValue(Object value) | 判断集合中是否存在 value          |
| V get(Object key)                   | 通过 key 取出对应的 value         |
| V put(Object key,Object value)      | 向集合中添加一组 key-value        |
| V remove(Object key)                | 通过 key 删除集合元素             |
| void clear()                        | 清空集合                          |
| Set keySet()                        | 取出所有的 key，返回 Set          |
| Collection values()                 | 取出所有的 value，返回 Collection |
| Set entrySet()                      | 将 Map 转换为 Set 对象            |
| int hashCode()                      | 获取集合的散列码                  |
| boolean equals(Object o)            | 比较两个集合是否相等              |

## Map 接口的实现类

- HashMap：存储一组无序、key 不可重复，value 可重复的元素
- Hashtable：存储一组无序、key 不可重复，value 可以重复的元素
- TreeMap：存储一组有序、key 不可重复、value 可以重复的元素，可以按照 key 来排序

HashMap 常用方法

```java
import java.util.Collection;
import java.util.HashMap;
import java.util.Iterator;
import java.util.Set;

public class Test {
    public static void main(String[] args) {
        HashMap hashMap = new HashMap();
        hashMap.put("h", "Hello");
        hashMap.put("w", "World");
        hashMap.put("j","Java");
        hashMap.put("s","JavaSE");
        hashMap.put("m","JavaME");
        hashMap.put("e","JavaEE");
        System.out.println(hashMap);
//        通过.remove(key)移除集合中的元素
        hashMap.remove("e");
        System.out.println(hashMap);
//        通过.put(key, value)的方式，向集合中添加一组key-value的元素，但是HashMap用来存储一组无序、key 不可重复，value 可重复的元素，
//        因此对于“m”已经有对应的value元素了，新追加的value元素会覆盖掉已有的元素。
        hashMap.put("m","Model");
        System.out.println(hashMap);
//      HashMap用来存储一组无序、key 不可重复，value 可重复的元素，集合中有两个相同的value也是OK的
        hashMap.put("m","Java");
        System.out.println(hashMap);
        System.out.println(hashMap.containsKey("a"));
        hashMap.containsKey("Java");

//      取出集合中的key元素
        Set set = hashMap.keySet();
        Iterator iterator = set.iterator();
        while (iterator.hasNext()){
            System.out.println(iterator.next());
        }
        System.out.println("======================");

//      取出集合中的value元素
        Collection values = hashMap.values();
        Iterator iterator1 = values.iterator();
        while (iterator1.hasNext()){
            System.out.println(iterator1.next());
        }
        System.out.println("======================");

//      按key=value的姓氏取出集合中的元素
        Set set1 = hashMap.entrySet();
        Iterator iterator2 = set1.iterator();
        while (iterator2.hasNext()){
            System.out.println(iterator2.next());
        }
    }
}
```

Hashtable 常用方法

```java
import java.util.*;

public class Test {
    public static void main(String[] args) {
        Hashtable hashtable = new Hashtable();
        hashtable.put("h", "Hello");
        hashtable.put("w", "World");
        hashtable.put("j", "Java");
        hashtable.put("s", "JavaSE");
        hashtable.put("m", "JavaME");
        hashtable.put("e", "JavaEE");
        System.out.println(hashtable);
        hashtable.remove("e");
        System.out.println(hashtable);
        hashtable.put("m", "Model");
        System.out.println(hashtable);
        System.out.println(hashtable.containsKey("a"));
        System.out.println(hashtable.containsValue("Java"));
        Set set = hashtable.keySet();
        Iterator iterator = set.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
        Collection values = hashtable.values();
        Iterator iterator1 = values.iterator();
        while (iterator1.hasNext()) {
            System.out.println(iterator1.next());
        }
    }
}
```

Hashtable 是线程安全的，HashMap 是线程不安全的，
也就是多个线程操作数据的时候，使用 Hashtable，数据不会出现错误的情况，因为 hashtable 的方法有 synchronized 关键字，也就是上了锁，因此是线程安全的集合类型
使用 HashMap 时，线程不安全的，因为 hashMap 的方法没有 synchronized 关键字，也就是没有拿到锁，因此是线程不安全的集合类型
