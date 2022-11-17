# 字符串

​		String是一个引用类型，本身也是一个class，它可以用来表示一个字符串。字符串在String内部是通过一个char[]数组表示。Java字符串的一个重要特点就是**字符串不可变**。这种不可变性是通过内部的private final char[]字段，以及没有任何修改char[]的方法实现的。

​		一般程序需要处理大量文本数据，Java 语言的文本数据被保存为字符或字符串类型。关于字符及字符串的操作主要用到 **String** 类和 **StringBuffer** 类，如**连接**、**修改**、**替换**、**比较**和**查找**等。

## 字符串定义

​		**注意：**不论使用哪种形式创建字符串，字符串对象一旦被创建，其值是不能改变的，但可以使用其他变量重新赋值的方式进行更改。

### 直接定义

​		直接定义字符串是指使用双引号表示字符串中的内容，例如“Hello Java”、“Java 编程”等。具体方法是用字符串常量直接初始化一个 String 对象，示例如下：

```java
String str = "Hello Java";
// 或者
String str2;
str2 = "Hello Java";
```

​		**例子一：**下面的实例演示了直接创建字符串的几种用法。

```java
String str = "我是一只小小鸟"; // 结果：我是一只小小鸟
String word;
word = "I am a bird"; // 结果：I am a bird
word = "<h1>to fly</h1>"; // 结果：<h1>to fly</h1>
word = "Let\'s say that it\'s true"; // 结果：Let's say that it's true
System.out.println(word);
word = "北京\\上海\\广州"; // 结果：北京\上海\广州
```

### 使用String类定义

​		String类位于 java.lang 包中。下面演示创建字符串的几种方式：

**【1】String()**

​		初始化一个新创建的 String 对象，

**【2】String(String value)**

​		初始化一个新创建的 String 对象，使其表示一个与参数相同的字符序列。换句话说，新创建的字符串是该参数字符串的副本。例如：

```java
String str1 = new String("Hello Java");
String str2 = new String(str1);
```

**【3】String(char[] value)**

​		将一个数组转换成一个字符串。

```java
char a[] = {'H','e','l','l','0'};
String sChar = new String(a);
a[1] = 's';
System.out.println(sChar); //打印 Hello
```

**【4】String(char[] value,int offset,int count)**

​		**value**是一个字符数组，**offset**是数组第一个字符的索引，**count**指定截取数组的长度。

```java
char a[]={'H','e','l','l','o'};
String sChar=new String(a,1,4);		// 截取a数组，从索引1开始向后截取4个元素（包含索引1），ello
a[1]='s';
System.out.println(sChar); //打印 ello
```

### String转换为int

String转为int有两种方式

* Integer.parseInt(str)
* Integer.valueOf(str).intValue()
* **注意：Integer是一个类**，它是int基本数据类型的封装类

**例子一：**

```java
public static void main(String[] args) {
    String str = "123";
    int n = 0;
    
    // 第一种转换方法：Integer.parseInt(str)
    n = Integer.parseInt(str);
    System.out.println("Integer.parseInt(str) : " + n);	//123
    
    // 第二种转换方法：Integer.valueOf(str).intValue()
    n = 0;
    n = Integer.valueOf(str).intValue();
    System.out.println("Integer.parseInt(str) : " + n);	//123
}
```

​		在 String 转换 int 时，String 的值必须是整数，否则会报数字转换异常（java.lang.NumberFormatException）。



### int转换为String

整形int转换成String字符串有一下三种方式：

* String s = String.valueOf(i)     	（效率最高）
* String s = Integer.toString(i)
* String s = ""+i     （效率最低）

**例子一：**

```java
public static void main(String[] args) {
    int num = 10;
    // 第一种方法：String.valueOf(i);
    num = 10;
    String str = String.valueOf(num);
    System.out.println("str:" + str);
    // 第二种方法：Integer.toString(i);
    num = 10;
    String str2 = Integer.toString(num);
    System.out.println("str2:" + str2);
    // 第三种方法："" + i;
    String str3 = num + "";
    System.out.println("str3:" + str3);
}
```



### String与基本数据类型转换

**【1】valueOf()**

​		String类型转为Integer类型

​		**java.lang**包中的**Integer类**调用其类方法public static int parseInt(String s)可以将由“数字”字符组成的字符串，如"123"， 转化为int型数据

**语法：**

```java
static Integer valueOf(int i)
static Integer valueOf(String s)
static Integer valueOf(String s, int radix)
```

- **i** -- Integer 对象的整数。
- **s** -- Integer 对象的字符串。
- **radix** --在解析字符串 s 时使用的进制数，用于指定使用的进制数。

**例子一：**

```java
public static void main(String args[]){
       Integer x =Integer.valueOf(9);
       Double c = Double.valueOf(5);
       Float a = Float.valueOf("80");              
       Integer b = Integer.valueOf("22",16);   // 使用 16 进制 进行解析
 	   String dStr = String.valueOf(new char[]{'张','三'}); //把 char、int、double、float、booblean、char[]转换为字符串类型
       System.out.println(x);
       System.out.println(c);
       System.out.println(a);
       System.out.println(b);
}
```

​		其他类型转为String类型

```java
public static String valueOf(byte n)
public static String valueOf(int n)
public static String valueOf(short n)
public static String valueOf(long n)
public static String valueOf(float n)
public static String valueOf(double n)
```



**【2】parse()**

​		parseXxx(String) 这种形式，是指把字符串（String）转换为Xxx数值型，其中 Xxx 对应不同的数据类型，然后转换为 Xxx 指定的类型，如 int 型和 float 型。例如：

​		parseInt("123")：代指把字符串"123"转化为int类型123

​		parseDouble("123.123")：把字符串"123.123"转化为double类型123.123



**【3】toString()**

​		toString() 方法用于返回以一个字符串表示的对象值。

```java
public static void main(String args[]){
    Integer x = 5;

    System.out.println(x.toString());  
    System.out.println(Integer.toString(12)); 
}
```



## 字符串拼接

**【1】使用“+”进行字符串拼接**

​		“+”运算符是最简单、最快捷，也是使用最多的字符串连接方式。在使用“+”运算符连接字符串和 int 型（或 double 型）数据时，“+”将 int（或 double）型数据自动转换成 String 类型。

```java
public static void main(String[] args) {
    int[] no = new int[] { 501, 101, 204, 102, 334 }; // 定义学号数组
    String[] names = new String[] { "张城", "刘丽丽", "李国旺", "孟红霞", "贺宁" }; // 定义姓名数组
    String[] classes = new String[] { "数学", "语文", "数学", "英语", "英语" }; // 定义课程数组
    System.out.println("本次考试学生信息如下：");
    // 循环遍历数组，连接字符串
    for (int i = 0; i < no.length; i++) {
        System.out.println("学号：" + no[i] + "|姓名：" + names[i] + "|课程：" + classes[i] + "|班级：" + "初二（三）班");
    }
}
```



**【2】字符串拼接其他数据类型**

​		如果将字符串同其他数据类型数据进行连接，最终会将这些数据直接转换成字符串。

**例子一：******将字符串与整型****、浮点型变量相连并输出结果。

```java
public static void main(String[] args) {
    String book = "三国演义"; // 字符串
    int price = 59; // 整型变量
    float readtime = 2.5f; // 浮点型变量
    System.out.println("我买了一本图书，名字是：" + book + "\n价格是：" + price + "\n我每天阅读" + readtime + "小时");
}
```

​		price 和 readtime 都不是字符串，当它们与字符串相连时会自动调用自身的 toString() 方法将其转换成字符串形式，然后再参与连接运算。

​		**注意：**在拼接时要注意运算的优先级，例如下面的例子

```
String s1 = ""+1+2; // "12"
String s2 = 1+2+""; // "3"
String s3 = ""+1+22+""+; // "122"
```

​		在有其他运算的情况下，最好加上括号，圆括号的优先级最高。



## String内置方法

**【1】lenth()：**获取字符串的长度

```java
String s = "Hello Java";
System.out.println(s.length()); // 10 空格也算
```



**【2】toLowerCase()：**所有字符转为小写，非字母不受影响

**【3】toUpperCase()**： 所有字符转为大写，非字母不受影响

a-z  A-Z

```
String s = "Hello Java 你好！";
System.out.println(s.toLowerCase()); 
System.out.println(s.toUpperCase()); 
```



**【4】trim()：**去除字符串**首尾**的空格

**注意！！！：**除去的是首位的空格

```java
String str = " hello ";
System.out.println(str.trim());    // 输出 hello
System.out.println(str.length());    // 输出 7
System.out.println(str.trim().length());    // 输出 5
String s = "Hello Java 你好！";   
System.out.println(s.trim());      //Hello Java 你好！ 结果不变
```



**【5】substring()：**截取字符串

​		在 String 中提供了两个截取字符串的方法：

* 从**指定位置截取到字符串结尾**
* 截取**指定范围**的内容。
* ![image-20221019165338830](C:\Users\16490\AppData\Roaming\Typora\typora-user-images\image-20221019165338830.png)

**1. substring(int beginIndex) 形式**

​		截取从索引位置开始至结尾处的字符串，**beginIndex**表示截取起始位置处的索引,索引从0开始。 

```java
String s = "Hello Java 你好！";    //lenth : 14
System.out.println(s.substring(4));		// o Java 你好！
```

**2. substring(int beginIndex，int endIndex) 形式**

​		beginIndex表示起始索引，endIndex表示结束索引。截取的内容包含起始索引，不包含结束索引。

```java
String day = "Today is Monday";    //原始字符串
System.out.println("substring(0)结果："+day.substring(0));
System.out.println("substring(2)结果："+day.substring(2));
System.out.println("substring(10)结果："+day.substring(10));
System.out.println("substring(2,10)结果："+day.substring(2,10));
System.out.println("substring(0,5)结果："+day.substring(0,5));
```



**【6】spilt():**按指定的分割符对目标字符串进行分割，分割后的内容存放在**字符串数组**中(spilt方法的**返回值是一个String类型数组**)。方法主要有如下两种重载形式：

* str.split(String sign)
* str.split(String sign,int limit)

其中它们的含义如下：

- str 为需要分割的目标字符串。
- sign 为指定的分割符，可以是任意字符串。
- limit 表示分割后生成的字符串的限制个数，如果不指定，则表示不限制，直到将整个目标字符串完全分割为止。

**使用分隔符注意如下：**

(1) “.”和“|”都是转义字符，必须得加“\\”。
如果用“.”作为分隔的话，必须写成String.split("\\.")，这样才能正确的分隔开，不能用String.split(".")。
如果用“|”作为分隔的话，必须写成String.split("\\|")，这样才能正确的分隔开，不能用String.split("|")。

(2) 如果在一个字符串中有多个分隔符，可以用“|”作为连字符，比如：“acount=? and uu =? or n=?”，把三个都分隔出来，可以用String.split("and|or")。

```java
public static void main(String[] args) {
    String Colors = "Red,Black,White,Yellow,Blue";
    String[] arr1 = Colors.split(","); // 不限制元素个数
    String[] arr2 = Colors.split(",", 3); // 限制元素个数为3
    System.out.println("所有颜色为：");
    for (int i = 0; i < arr1.length; i++) {
        System.out.println(arr1[i]);
    }
    System.out.println("前三个颜色为：");
    for (int j = 0; j < arr2.length; j++) {
        System.out.println(arr2[j]);
    }
}
```



**【7】replace()、replaceFirst():**

**1.replace()**方法将目标字符串中**指定字符串**替换成**新的字符串**，

```
字符串.replace(String oldChar, String newChar)
```

​		oldChar 表示被替换的字符串；newChar 表示用于替换的字符串。replace() 方法会将字符串中所有 oldChar 替换成 newChar。

```java
String words = "hello java,hello php";
System.out.println(words.replace("l","1"));     //he11o java,he11o php  将 所有l 替换成 1 
System.out.println(words.replace("hello","你好"));     //你好 java,你好 php 将 所有hello 替换成 你好
```



**2.replaceFirst()**将目标字符串中**指定第一个字符串**替换成**新的字符串**，

```java
字符串.replaceFirst(String regex, String replacement)
```

```java
String words = "hello java,hello php";
System.out.println(words.replaceFirst("l","1"));     //he1lo java,hello php  将第一个“l” 替换成 1
System.out.println(words.replaceFirst("hello","你好"));     //你好 java,hello php 将第一个“hello” 替换成 你好
```



**【8】字符串比较：**equals()、equalsIgnoreCase() 、compareTo()

**equals()：**逐个地比较两个字符串的每个字符是否相同

**equalsIgnoreCase()：**对比eauals() 此方法忽略大小写比较两个字符串是否相等 a A

**equals()与==的比较：**equals() 方法比较字符串对象中的字符。而==运算符比较两个对象引用看它们是否引用相同的实例。

 ```java
 String s1 = "Hello";
 String s2 = new String(s1);
 System.out.println(s1.equals(s2)); // 输出true
 System.out.println(s1 == s2); // 输出false
 ```

**compareTo()：**按字典顺序比较两个字符串的大小，该比较是基于字符串各个字符的 Unicode 值。

比较格式：str.compareTo(String otherstr);

比较说明：它会按字典顺序将 str 表示的字符序列与 otherstr 参数表示的字符序列进行比较。如果按字典顺序 str 位于 otherster 参数之前，比较结果为一个负整数；如果 str 位于 otherstr 之后，比较结果为一个正整数；如果两个字符串相等，则结果为 0。

```java
String str = "A";
String str1 = "a";
System.out.println("str.compareTo(str1)的结果是：" + str.compareTo(str1));
System.out.println("str1.compareTo(str)的结果是：" + str1.compareTo(str));
System.out.println("str1.compareTo('a')的结果是：" + str1.compareTo("a"));
```



**【9】查找字符串：**indexOf(),返回int类型

​		indexOf() 方法用于返回字符（串）在指定字符串中**首次出现的索引位置**，如果能找到，则返回索引值，否则返回 -1。该方法主要有两种重载形式：

* str.indexOf(value)
* str.indexOf(value,int fromIndex)

​		其中，str 表示指定字符串；value 表示待查找的字符（串）；fromIndex 表示查找时的起始索引，如果不指定 fromIndex，则默认从指定字符串中的开始位置（即 fromIndex 默认为 0）开始查找。

```java
String s = "Hello Java";
System.out.println(s.indexOf('v'));    //  8
System.out.println(s.indexOf("ava"));  //  7
System.out.println(s.indexOf('v',5));   // 返回8 表示从索引5开始查，索引5是一个空格,这样可以提升效率   
```



**【10】charAt()：** 在字符串内根据指定的索引查找字符

**语法格式：**

​		字符串名.charAt(索引值)

**例子一：**

```java
String words = "today,monday,sunday";
System.out.println(words.charAt(0));    // 结果：t
System.out.println(words.charAt(1));    // 结果：o
System.out.println(words.charAt(8));    // 结果：n
```



**【11】contains(String s):**判断当前字符串对象是否含有参数指定的字符串s。返回值是一个booblean类型

**例子一：**

```java
String tom = "student";
tom.contains("stu")	// true
tom.contains("ok")	// false
```





## StringBuffer类

​		StringBuffer 类是**可变字符串类**，创建 StringBuffer 类的对象后可以随意修改字符串的内容。每个 StringBuffer 类的对象都能够存储指定容量的字符串，如果字符串的长度超过了 StringBuffer 类对象的容量，则该对象的容量会自动扩大。

**【1】创建StringBuffer类：**

StringBuffer 类提供了 3 个构造方法来创建一个字符串，如下所示：

- StringBuffer() 构造一个空的字符串缓冲区，并且初始化为 16 个字符的容量。
- StringBuffer(int length) 创建一个空的字符串缓冲区，并且初始化为指定长度 length 的容量。
- StringBuffer(String str) 创建一个字符串缓冲区，并将其内容初始化为指定的字符串内容 str，字符串缓冲区的初始容量为 16 加上字符串 str 的长度。

**例子一：**

```java
// 定义一个空的字符串缓冲区，含有16个字符的容量
StringBuffer str1 = new StringBuffer();
// 定义一个含有10个字符容量的字符串缓冲区
StringBuffer str2 = new StringBuffer(10);
// 定义一个含有(16+4)的字符串缓冲区，"青春无悔"为4个字符
StringBuffer str3 = new StringBuffer("青春无悔");
/*
*输出字符串的容量大小
*capacity()方法返回字符串的容量大小（字符串内可以包含字符的个数）
*/
System.out.println(str1.capacity());    // 输出 16
System.out.println(str2.capacity());    // 输出 10
System.out.println(str3.capacity());    // 输出 20
```



**【2】append():**追加字符串 

​		StringBuffer 类的 append() 方法用于向原有 StringBuffer 对象中追加字符串,追加内容到当前 StringBuffer 对象的末尾，类似于字符串的连接。调用该方法以后，StringBuffer 对象的内容也发生了改变

​		语法格式：

```java
StringBuffer的对象.append(String str)
```

**例子一：**

```java
StringBuffer buffer = new StringBuffer("hello,");    // 创建一个 StringBuffer 对象
String str = "World!";
buffer.append(str);    // 向 StringBuffer 对象追加 str 字符串
System.out.println(buffer.substring(0));    // 输出：Hello,World!
```



**例子二：**每个新学期开始，学校都会针对本学期课程列出必修课程。编写一个 Java 程序，要求用户向控制台循环录入五门必修课程名称，并将这五个名称进行连接，最后输出连接后的字符串。

```java
public static void main(String[] args) {
    // 循环录入五门课程，将这五门课程连接输出

    System.out.println("欢迎进入《校内课程管理》系统");
    // 新建一个StringBuffer类
    StringBuffer stringBuffer = new StringBuffer();
    // 提示用户录入课程名称
    System.out.println("请录入本期的五门必修课名称：");
    Scanner scanner = new Scanner(System.in);
    System.out.println(stringBuffer);
    for (int i = 0; i < 3; i++) {
        String s = scanner.next();  // 接受用户输入的课程
        stringBuffer.append(s);
    }
    System.out.println(stringBuffer);
}
```



**【3】setCharAt():替换字符** ：在字符串的指定索引位置**替换一个字符**。

语法格式：

```java
对象.setCharAt(int index, char ch);
```

**例子一：**

```java
StringBuffer sb = new StringBuffer("hello");
sb.setCharAt(1,'E');
System.out.println(sb);    // 输出：hEllo
sb.setCharAt(0,'H');
System.out.println(sb);    // 输出：HEllo
sb.setCharAt(2,'p');
System.out.println(sb);    // 输出：HEplo
```



**【4】reverse():** 将字符串序列用其反转的形式取代。

语法格式：

```java
对象.reverse();
```

**例子一：**

```java
StringBuffer sb = new StringBuffer("java");
sb.reverse();
System.out.println(sb);    // 输出：avaj
```



**【5】删除字符串:**StringBuffer 类提供了 deleteCharAt() 和 delete() 两个删除字符串的方法

**1. deleteCharAt() 方法**:用于移除序列中指定位置的字符

语法格式：

```java
对象.deleteCharAt(int index);
```

**例子一：**

```java
StringBuffer sb = new StringBuffer("She");
sb.deleteCharAt(2);
System.out.println(sb);    // 输出：Sh
```

​		执行该段代码，将字符串 sb 中索引值为 2 的字符删除，剩余的内容组成一个新的字符串，因此对象 sb 的值为 Sh。



**2. delete() 方法**:delete() 方法用于移除序列中子字符串的字符。start 表示要删除字符的起始索引值（包括索引值所对应的字符），end 表示要删除字符串的结束索引值（不包括索引值所对应的字符）。该方法的作用是删除指定区域以内的所有字符。

语法格式：

```java
对象.delete(int start,int end);	// [start，end)
```

**例子一：**

```java
StringBuffer sb = new StringBuffer("hello jack");
sb.delete(2,5);
System.out.println(sb);    // 输出：he jack
sb.delete(2,5);
System.out.println(sb);    // 输出：heck
```

​		执行该段代码，将字符串“hello jack”索引值为 2（包括）到索引值为 5（不包括）之间的所有字符删除，因此输出的新的字符串的值为“he jack”。



## StringBuilder

​		Java 提供了两个可变字符串类 StringBuffer 和 StringBuilder， 它们两个功能基本相似，方法也差不多。不同的是，StringBuffer 是线程安全的，而 StringBuilder 则没有实现线程安全功能，所以性能略高。

**区别：**

StringBuilder 线程不安全，效率高

StringBuffer  线程安全，效率低





# 包装类型

**【1】什么是包装类：**
以前定义变量，经常使用基本数据类型，
对于基本数据类型来说，它就是一个数，加点属性，加点方法，加点构造器，
将基本数据类型对应进行了一个封装，产生了一个新的类，---》包装类。
int,byte.....--->基本数据类型
包装类--->引用数据类型

引用类型可以赋值为null，表示空，但基本类型不能赋值为null：



**【2】基本类型对应的包装类型**

| boolean | java.lang.Boolean   |
| ------- | ------------------- |
| byte    | java.lang.Byte      |
| short   | java.lang.Short     |
| int     | java.lang.Integer   |
| long    | java.lang.Long      |
| float   | java.lang.Float     |
| double  | java.lang.Double    |
| char    | java.lang.Character |

**自动装箱和拆箱**

```
int i = 10;
Integer n = Integer.valueOf(i);
int x = n.intValue;
```

（1）Integer n = Integer.valueOf(i); 

​	把**int转换成Integer**类型的成为**自动装箱（Auto Boxing）**

（2）int x = n.intValue; 

​	把**Integer转换成int**类型的称为**自动拆箱（Auto Unboxing）**

# JavaBean

## JavaBean的作用

**作用：**JavaBean主要用来传递数据，即把一组数据组合成一个JavaBean便于传输。通过IDE，可以快速生成getter和setter。

```java
public class Person {
    private String name;
    private int age;
}
```

**生成get()和set()的方法：**1、点击右键，在弹出的菜单中选择“Source”，“Generate Getters and Setters”，在弹出的对话框中选中需要生成getter和setter方法的字段。2、利用alt+insert快捷键直接弹出“Generate Getters and Setters”。

## JavaBean格式

例如：

```java
public class Person {
    private String name;
    private int age;

    public String getName() { return this.name; }
    public void setName(String name) { this.name = name; }

    public int getAge() { return this.age; }
    public void setAge(int age) { this.age = age; }
}
```

如上代码所示，如果符合一下这种命名规格：

```java
// 读方法:  --读方法有返回值
public Type getXyz()
    
// 写方法: --写方法没有返回值
public void setXyz(Type value)
```

**这种class被称为JavaBean。**

我们通常把一组对应的读方法（`getter`）和写方法（`setter`）称为属性（`property`）。例如，`name`属性：

- 对应的读方法是`String getName()`
- 对应的写方法是`setName(String)`

只有`getter`的属性称为只读属性（read-only），例如，定义一个age只读属性：

- 对应的读方法是`int getAge()`
- 无对应的写方法`setAge(int)`

**读属性常见，写属性不常见**。

**特殊命名：**

`boolean`字段比较特殊，它的读方法一般命名为`isXyz()`：

```java
// 读方法:
public boolean isChild()
// 写方法:
public void setChild(boolean value)
```

# 常用工具类

## Math

**1、求绝对值：**

```
Math.abs(-100); // 100
Math.abs(-7.8); // 7.8
```

**2、取最大或最小值：**

```
Math.max(100, 99); // 100
Math.min(1.2, 2.3); // 1.2
```

**3、计算x^y次方：**

```java
Math.pow(2, 10); // 2的10次方=1024
```

**4、计算√x：**

```
Math.sqrt(2); // 1.414...
Math.sqrt(9); // 3
```

**5、生成随机数****

```
Math.random(); // 0.53907... 生成一个[0,1)的随机数，每次生成的都不一样
```

**6、求整运算（返回最接近目标值的整数）**

```
Math.ceil(1.1) 	// 2    返回大于等于1.1的最小整数
Math.floor(1.1)	// 1	返回小于等于1.1的最大整数
```



## Random类

​		在 Java 中要生成一个指定范围之内的随机数字有两种方法：一种是调用 Math 类的 random() 方法，一种是使用 Random 类。

| 方法                    | 说明                                                         |
| ----------------------- | ------------------------------------------------------------ |
| boolean nextBoolean()   | 生成一个随机的 boolean 值，生成 true 和 false 的值概率相等   |
| double nextDouble()     | 生成一个随机的 double 值，数值介于 [0,1.0)，含 0 而不包含 1.0 |
| int nextlnt()           | 生成一个随机的 int 值，该值介于 int 的区间，也就是 -231~231-1。如果 需要生成指定区间的 int 值，则需要进行一定的数学变换 |
| int nextlnt(int n)      | 生成一个随机的 int 值，该值介于 [0,n)，包含 0 而不包含 n。如果想生成 指定区间的 int 值，也需要进行一定的数学变换 |
| void setSeed(long seed) | 重新设置 Random 对象中的种子数。设置完种子数以后的 Random 对象 和相同种子数使用 new 关键字创建出的 Random 对象相同 |
| long nextLong()         | 返回一个随机长整型数字                                       |
| boolean nextBoolean()   | 返回一个随机布尔型值                                         |
| float nextFloat()       | 返回一个随机浮点型数字                                       |
| double nextDouble()     | 返回一个随机双精度值                                         |



**例子一：**使用 Random 类提供的方法来生成随机数

```java
public static void main(String[] args) {
        Random r = new Random();
        double d1 = r.nextDouble(); // 生成[0,1.0]区间的小数
        double d2 = r.nextDouble() * 7; // 生成[0,7.0]区间的小数
        int i1 = r.nextInt(10); // 生成[0,10]区间的整数
        int i2 = r.nextInt(18) - 3; // 生成[-3,15)区间的整数
        long l1 = r.nextLong(); // 生成一个随机长整型值
        boolean b1 = r.nextBoolean(); // 生成一个随机布尔型值
        float f1 = r.nextFloat(); // 生成一个随机浮点型值
        System.out.println("生成的[0,1.0]区间的小数是：" + d1);
        System.out.println("生成的[0,7.0]区间的小数是：" + d2);
        System.out.println("生成的[0,10]区间的整数是：" + i1);
        System.out.println("生成的[-3,15]区间的整数是：" + i2);
        System.out.println("生成一个随机长整型值：" + l1);
        System.out.println("生成一个随机布尔型值：" + b1);
        System.out.println("生成一个随机浮点型值：" + f1);
        System.out.print("下期七星彩开奖号码预测：");
        for (int i = 1; i < 8; i++) {
            int num = r.nextInt(9); // 生成[0,9]区间的整数
            System.out.print(num);
        }
    }
```



**例子二：**实现生成任意范围的随机数

​		Math 类的 random() 方法没有参数，它默认会返回大于等于 0.0、小于 1.0 的 double 类型随机数，即 0<=随机数<1.0。下面演示使用 random() 方法实现随机生成一个 2~100 偶数的功能。

```java
public static void main(String[] args) {
    int min = 2; // 定义随机数的最小值
    int max = 102; // 定义随机数的最大值
    // 产生一个2~100的数
    int s = (int) min + (int) (Math.random() * (max - min));
    if (s % 2 == 0) {
        // 如果是偶数就输出
        System.out.println("随机数是：" + s);
    } else {
        // 如果是奇数就加1后输出
        System.out.println("随机数是：" + (s + 1));
    }
}
```



# 日期类

​		在 Java 中获取当前时间，可以使用 **java.util.Date** 类和 **java.util.Calendar** 类完成。其中，Date 类主要封装了系统的日期和时间的信息，Calendar 类则会根据系统的日历来解释 Date 对象。

## Date类

**【1】Date 类:**表示系统特定的时间戳，可以精确到毫秒。Date 对象表示时间的默认顺序是星期、月、日、小时、分、秒、年。

**例子一：**打印当前系统时间

```java
Date date = new Date();
System.out.println(date);	//	Thu Oct 20 10:36:32 CST 2022
```



**【2】构造方法**

* Date()：此种形式表示分配 Date 对象并初始化此对象，以表示分配它的时间（精确到毫秒），使用该构造方法创建的对象可以获取本地的当前时间，如例子一。

* Date(long date)：此种形式表示从 GMT 时间（格林尼治时间）1970 年 1 月 1 日 0 时 0 分 0 秒开始经过参数 date 指定的毫秒数。

**例子二：**

```java
Date date1 = new Date();    // 调用无参数构造函数
System.out.println(date1.toString());    // 输出：Wed May 18 21:24:40 CST 2016
Date date2 = new Date(60000);    // 调用含有一个long类型参数的构造函数
System.out.println(date2);    // 输出：Thu Jan 0108:01:00 CST 1970
```

​		Date 类的无参数构造方法获取的是系统当前的时间，显示的顺序为星期、月、日、小时、分、秒、年。



**【3】Date类常用方法：**

| 方法                      | 描述                                                         |
| ------------------------- | ------------------------------------------------------------ |
| boolean after(Date when)  | 判断此日期是否在指定日期之后                                 |
| boolean before(Date when) | 判断此日期是否在指定日期之前                                 |
| long getTime()            | 返回自 1970 年 1 月 1 日 00:00:00 GMT 以来，此 Date 对象表示的毫秒数 |
| String toString()         | 把此 Date 对象转换为以下形式的 String: dow mon dd hh:mm:ss zzz yyyy。 其中 dow 是一周中的某一天(Sun、Mon、Tue、Wed、Thu、Fri 及 Sat) |

**例子一：**下面使用一个实例来具体演示 Date 类的使用。假设，某一天特定时间要去做一件事，而且那个时间已经过去一分钟之后才想起来这件事还没有办，这时系统将会提示已经过去了多 长时间。

```java
public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.println("请输入要做的事情：");
        String title = input.next();
        Date date1 = new Date(); // 获取当前日期
        System.out.println("[" + title + "] 这件事发生时间为：" + date1);
        try {
            Thread.sleep(60000);// 暂停 1 分钟
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        Date date2 = new Date();
        System.out.println("现在时间为：" + date2);
        if (date2.before(date1)) {
            System.out.println("你还有 " + (date2.getTime() - date1.getTime()) / 1000 + " 秒需要去完成【" + title + "】这件事！");
        } else {
            System.out.println("【" + title + "】事情已经过去了 " + (date2.getTime() - date1.getTime()) / 1000 + " 秒");
        }
    }
```

​		在该程序中，分别使用 Date 类的无参数构造方法创建了两个 Date 对象。在创建完第一个 Date 对象后，使用 Thread.sleep() 方法让程序休眠 60 秒，然后再创建第二个 Date 对象，这样第二个 Date 对象所表示的时间将会在第一个 Date 对象所表示时间之后，因此“date2.before(date1)”条件表达式不成立，从而执行 else 块中的代码，表示事情已经发生过。



## Calendar类

​		Calendar 类是一个抽象类。使用getInstance() 方法来获得 Calendar类的对象。

```java
Calendar c = Calendar.getInstance();
```

Calendar类中常用字段：

```java
Calendar.YEAR：年份。
Calendar.MONTH：月份。	月份下标从0开始，所以实际月份要+1
Calendar.DATE：日期。
Calendar.DAY_OF_MONTH：日期，和上面的字段意义完全相同。
Calendar.HOUR：12小时制的小时。
Calendar.HOUR_OF_DAY：24 小时制的小时。
Calendar.MINUTE：分钟。
Calendar.SECOND：秒。
Calendar.DAY_OF_WEEK：星期几。
```

Calendar类中常用方法：

| 方法                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **void add(int field, int amount)**                          | 根据日历的规则，为给定的日历字段 field 添加或减去指定的时间量 amount |
| boolean after(Object when)                                   | 判断此 Calendar 表示的时间是否在指定时间 when 之后，并返回判断结果 |
| boolean before(Object when)                                  | 判断此 Calendar 表示的时间是否在指定时间 when 之前，并返回判断结果 |
| void clear()                                                 | 清空 Calendar 中的日期时间值                                 |
| int compareTo(Calendar anotherCalendar)                      | 比较两个 Calendar 对象表示的时间值（从格林威治时间 1970 年 01 月 01 日 00 时 00 分 00 秒至现在的毫秒偏移量），大则返回 1，小则返回 -1，相等返回 0 |
| **int get(int field)**                                       | 返回指定日历字段的值                                         |
| int getActualMaximum(int field)                              | 返回指定日历字段可能拥有的最大值                             |
| int getActualMinimum(int field)                              | 返回指定日历字段可能拥有的最小值                             |
| int getFirstDayOfWeek()                                      | 获取一星期的第一天。根据不同的国家地区，返回不同的值         |
| static Calendar getInstance()                                | 使用默认时区和语言坏境获得一个日历                           |
| static Calendar getInstance(TimeZone zone)                   | 使用指定时区和默认语言环境获得一个日历                       |
| static Calendar getInstance(TimeZone zone, Locale aLocale)   | 使用指定时区和语言环境获得一个日历                           |
| **Date getTime()**                                           | 返回一个表示此 Calendar 时间值（从格林威治时间 1970 年 01 月 01 日 00 时 00 分 00 秒至现在的毫秒偏移量）的 Date 对象 |
| long getTimeInMillis()                                       | 返回此 Calendar 的时间值，以毫秒为单位                       |
| **void set(int field, int value)**                           | 为指定的日历字段设置给定值                                   |
| **void set(int year, int month, int date)**                  | 设置日历字段 YEAR、MONTH 和 DAY_OF_MONTH 的值                |
| void set(int year, int month, int date, int hourOfDay, int minute, int second) | 设置字段 YEAR、MONTH、DAY_OF_MONTH、HOUR、 MINUTE 和 SECOND 的值 |
| void setFirstDayOfWeek(int value)                            | 设置一星期的第一天是哪一天                                   |
| void setTimeInMillis(long millis)                            | 用给定的 long 值设置此 Calendar 的当前时间值                 |

​		Calendar 对象可以调用 **set() 方法将日历翻到任何一个时间**，当参数 year 取负数时表示公元前。Calendar 对象调用 get() 方法可以获取有关年、月、日等时间信息，参数 field 的有效值由 Calendar 静态常量指定。

**例子一：**

```java
Calendar calendar = Calendar.getInstance(); // 如果不设置时间，则默认为当前时间
calendar.setTime(new Date()); // 将系统当前时间赋值给 Calendar 对象
System.out.println("现在时刻：" + calendar.getTime()); // 获取当前时间
int year = calendar.get(Calendar.YEAR); // 获取当前年份
System.out.println("现在是" + year + "年");
int month = calendar.get(Calendar.MONTH) + 1; // 获取当前月份（月份从 0 开始，所以加 1）
System.out.print(month + "月");
int day = calendar.get(Calendar.DATE); // 获取日
System.out.print(day + "日");
int week = calendar.get(Calendar.DAY_OF_WEEK) - 1; // 获取今天星期几（以星期日为第一天）
System.out.print("星期" + week);
int hour = calendar.get(Calendar.HOUR_OF_DAY); // 获取当前小时数（24 小时制）
System.out.print(hour + "时");
int minute = calendar.get(Calendar.MINUTE); // 获取当前分钟
System.out.print(minute + "分");
int second = calendar.get(Calendar.SECOND); // 获取当前秒数
System.out.print(second + "秒");
int millisecond = calendar.get(Calendar.MILLISECOND); // 获取毫秒数
System.out.print(millisecond + "毫秒");
int dayOfMonth = calendar.get(Calendar.DAY_OF_MONTH); // 获取今天是本月第几天
System.out.println("今天是本月的第 " + dayOfMonth + " 天");
int dayOfWeekInMonth = calendar.get(Calendar.DAY_OF_WEEK_IN_MONTH); // 获取今天是本月第几周
System.out.println("今天是本月第 " + dayOfWeekInMonth + " 周");
int many = calendar.get(Calendar.DAY_OF_YEAR); // 获取今天是今年第几天
System.out.println("今天是今年第 " + many + " 天");
Calendar c = Calendar.getInstance();
c.set(2012, 8, 8); // 设置年月日，时分秒将默认采用当前值
System.out.println("设置日期为 2012-8-8 后的时间：" + c.getTime()); // 输出时间
```







# 内置包装类



## Object类

​		Object 是所有类的父类。也就是说，Java 允许把任何类型的对象赋给 Object 类型的变量。当一个类被定义后，如果没有指定继承的父类，那么默认父类就是 Object 类。如下两个类代表含义相同：

```java
public class MyClass{…}
public class MyClass extends Object {…}
```

**Object类常见方法：**

| 方法                       | 说明                                                         |
| -------------------------- | ------------------------------------------------------------ |
| Object clone()             | 创建与该对象的类相同的新对象                                 |
| boolean **equals**(Object) | 比较两对象是否相等                                           |
| void finalize()            | 当垃圾回收器确定不存在对该对象的更多引用时，对象垃圾回收器调用该方法 |
| Class getClass()           | 返回一个对象运行时的实例类                                   |
| int hashCode()             | 返回该对象的散列码值                                         |
| void notify()              | 激活等待在该对象的监视器上的一个线程                         |
| void notifyAll()           | 激活等待在该对象的监视器上的全部线程                         |
| String **toString**()      | 返回该对象的字符串表示                                       |
| void wait()                | 在其他线程调用此对象的 notify() 方法或 notifyAll() 方法前，导致当前线程等待 |

​		其中，toString()、equals() 方法和 getClass() 方法在 Java 程序中比较常用。

**【1】toString() 方法**

​		toString() 方法返回该对象的字符串，子类想要输出字段的信息，可以重写toString方法。

**【2】equals() 方法**

​		==运算符和 equals() 方法，==运算符是比较两个引用变量是否指向同一个实例，equals() 方法是比较两个对象的内容是否相等，通常字符串的比较只是关心内容是否相等。

​		**Object中的equals()方法：**

```java
public boolean equals(Object obj) {
    // 比较两对象在JVM的地址是否相同
    return (this == obj);
}
```

​		

​		**String类重写的equals()方法：**

```java
public boolean equals(Object anObject) {
    // == 比较两对象的地址是否相等，如若相等则表示两对象引用同一个字符串，返回true  
        if (this == anObject) {		
            return true;
        }
    
    // 如果地址不相等继续比较字符串的内容，instanceof表示比较两边是否引用String
        if (anObject instanceof String) {
            String anotherString = (String)anObject;
            int n = value.length;
            
    // 判断当前字符串长度是否等于传入字符串长度，如果相等继续比较字符串相同位置字符是否相等
            if (n == anotherString.value.length) {
                char v1[] = value;
                char v2[] = anotherString.value;
                int i = 0;
                while (n-- != 0) {
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



​		**Student自建类重写equals()方法：**该类有三个字段：name，id，major

```java
public boolean equals(Object o) {
    // 1.首先判断当前对象引用和传入对象o的引用是否指向相同的JVM地址，相同返回true
    if (this == o) return true;
    
    // 2.判断传入对象o是否为空 || 当前对象的实力类和传入对象实力类是否相同
    if (o == null || getClass() != o.getClass()) return false;	// 这步的作用？？
    Student student = (Student) o;
    
    // 3.
    return Objects.equals(id, student.id);
}
```











**【3】接收任意引用类型的对象**

​		既然 Object 类是所有对象的父类，则所有的对象都可以向 Object 进行转换，在这其中也包含了数组和接口类型，即一切的引用数据类型都可以使用 Object 进行接收。

**例子一：**

```java
interface A {
    public String getInfo();
}
class B implements A {
    public String getInfo() {
        return "Hello World!!!";
    }
}
public class ObjectDemo04 {
    public static void main(String[] args) {
        // 为接口实例化
        A a = new B();
        // 对象向上转型
        Object obj = a;
        // 对象向下转型
        A x = (A) obj;
        System.out.println(x.getInfo());
    }
}
```

​		虽然接口不能继承一个类，但是依然是 Object 类的子类，因为接口本身是引用数据类型，所以可以进行向上转型操作。



**例子二：**使用Object接收一个数组，数组本身也是引用数据类型，继承自Object

```java
public static void main(String[] args) {
        int temp[] = { 1, 3, 5, 7, 9 };
        // 使用object接收数组
        Object obj = temp;
        // 传递数组引用
        print(obj);
    }
    public static void print(Object o) {
        // 判断对象的类型
        if (o instanceof int[]) {
            // 向下转型
            int x[] = (int[]) o;
            // 循环输出
            for (int i = 0; i < x.length; i++) {
                System.out.print(x[i] + "\t");
            }
        }
    }
```

​		使用 Object 接收一个整型数组，因为数组本身属于引用数据类型，所以可以使用 Object 接收数组内容，在输出时通过 instanceof 判断类型是否是一个整型数组，然后进行输出操作。









