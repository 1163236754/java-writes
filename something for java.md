.

# Something for java

## base:

final关键字：关键字final表示这个关键字只能被赋值一次。一旦被赋值之后就不能更改了。习惯上常量名使用全大写。（const是java保留关键字 ，目前并没有使用。）

## Math类：

```java
	Math.sqrt() //求平方根方法
	Math.pow(x,a)  // 幂运算 意思是x的a次方
    // 常用三角函数
    Math.sin
    Math.cos
    Math.tan
    Math.atan
    Math.atan2
    // 指数函数以及其反函数-自然数以及以10为底的对数
    Math.exp
    Math.log
    Math.log10
    // 常量 Π和e的表示、
   	Math.PI
   	Math.E
```

不必再数学方法名和常量名称之前加上Math，只要再顶部导入即可。

```java

```



## String：

子串提取，类似于字符串截取

```java
// 提取子串
String hello = "Hello";
String s = hello.substring(0,3); //0,3表示需要截取的位置，s输出结果为“hel”
```

## 字符串拼接

和绝大多数语言一样，java允许用  + 号连接字符串

```java
String expletive = "Expletive";
String PG13 = "deleted";
String message = expletive + PG13;
//输出结果 ： Expletive deleted
```

如果需要把多个字符串放在一起用一个定界符分隔，可以使用静态join方法：

```java
String all = String.join("/","a","b","c");
// 输出结果 ： a / b / c
```

由于不能修改 Java 字符串中的字符， 所以在 Java 文档中将 String类对象称为不可变字 符串。

而不可变字符串有一个优点：编译器可以让字符串共享。共享带来的高效率远远胜过于提取、 拼接字符串所带来的 低效率

检测字符串是否相等：

方法：equals -> s.equals(t)

```java
if(s.equals(t)){
	// true
}else{
    // else
}
```

不区分大小写地比较可以用：equalsIgnoreCase

**切记不能使用==运算符来检测两个字符串是否相等，这个运算只能确定两个字符串是否放置在同一位置上，如果在同一位置上那必然是相等的，但是不排除将内容相同的多个字符串的拷贝放置在不同的位置上**

```java
String greeting = "Hello"; //initialize greeting to a string 
if (greeting == "Hello") .
    // probably true 
if (greeting.substring(0, 3) == "HeV) . . .
      // probably false 
```

	如果虚拟机始终将相同的字符串共享， 就可以使用= 运算符检测是否相等。但实际上 只有字符串常量是共享的，而+ 或 substring 等操作产生的结果并不是共享的。

## 空串与Null串：

空串 “ ” 是长度为0的字符串。

```java
if(str.length() == 0){
    // Something to do
}

if(str.equals(".")){
    // Something to do
}
```

空串是以一个java对象。有自己的串长度（0）和内容（空）。不过，String变量还可以存一个特殊值为null。

如何检查一个字符串是否为Null，使用如下条件：

```java
if(str == null)
```

有时候要检查str不为 null，也不为空串，可以使用如下条件：

```java

```

## 码点与代码单元：

	java字符串由char值序列组成。char数据类型是一个采用UTF-16编码表示Unicode码点的代码单元。大多数的常用 Unicode 字符使用一个代 码单元就可以表示，而辅助字符需要一对代码单元表示。 


	

```java
// length 方法将返回采用 UTF-16 编码表示的给定字符串所需要的代码单元数量。
// 例如：
String greeting = "Hello"; 
int n = greeting.length； // is 5. 
// 要想得到实际的长度，即码点数量，可以调用： 
int cpCount = greeting.codePointCount(0, greeting.lengthQ)；
//调用s.charAt(n) 将返回位置 n 的代码单元，n 介于 0 ~ s.length()-l 之间。
//例如： 
char first = greeting.charAtO); // first is 'H' 
char last = greeting.charAt(4); // last is ’o’ 
//要想得到第 i 个码点，应该使用下列语句 
int index = greeting.offsetByCodePoints(0,i); int cp = greeting.codePointAt(index); 
    
```

注意：java中对字符串的代码单元和码点是从0开始计数的。

## StringApi：

java中的String类包含50多个方法。其中绝大部分都很有用，而且使用频率非常之高。

```java
char charAt (int index)；
// 返回给定位置的代码单元。除非对底层的代码单元感兴趣， 否则不需要调用这个方法。（） 
int codePointAt(int Index)；
// 返回从给定位置开始的码点。 
int offsetByCodePoints(int startlndex, int cpCount)；
// 返回从 startlndex 代码点开始，位移 cpCount 后的码点索引。 
int compareTo(String other);
// 字符串比较。如果字符串位于other之后，返回一个正数；如果两个字符串相等则返回0；若位于other之前则返回一个复数
new String(int[] codePoints, int offset, int count);
// 用数组中从 offset 开始的 count 个码点构造一个字符串。构造指定长度的字符串。
boolean equals(Object other);
// 如果字符串与other相等，返回true。
boolean equalsIgnoreCase(String other);
// 字符串比较（忽略大小写），返回true。
boolean startWith(String prefix);
boolean endsWith(String suffix);
// 如果字符串以suffix开头或结尾。则返回true。
int indexOf(String str);
int indexOf(String str,int fromIndex);
int indexOf(int cp);
int indexOf(int cp, int fromIndex);
//返回与字符串 str 或代码点 cp 匹配的第一个子串的开始位置。这个位置从索引 0 或 fromlndex 开始计算。 如果在原始串中不存在 str， 返回 -1。 (俗话就是找到str，在字符串中的位置)
int lastIndexOf(String str);
int lastIndexOf(String str, int fromIndex);
int lastIndexOf(int cp);
int lastIndexOf(int cp,int fromIndex);
// 返回与字符串str或者代码点cp匹配的最后一个子串开始的位置。之歌位置从原始串尾端或者fromIndex开始计算。
int length();
// 返回字符串长度
String replace(CharSequence oldString,CharSequence newString);
//返回一个新字符串。这个字符串用 newString 代替原始字符串中所有的 oldString。可 以用 String 或 StringBuilder 对象作为 CharSequence 参数。 
String substring(int beginIndex);
String substring(int beginIndex, int endIndex);
// 返回一个新字符串，包括从beginIndex到endIndex-1的所有代码单元（字符串）
String toLowerCase();
String toUpperCase();
// 返回一个新字符串，将原始字符串中大写变小写，或者将原始字符串小写变成大写。
String trim();
// 返回一个字符串，删除串头和串尾的空格。
String join(CharSequence delimiter, CharSequence... elements)；
// 返回一个新字符串， 用给定的定界符连接所有元素
```

## 构建字符串

```java
StringBuilder builder = new StringBuilder();
// 当需要添加数据的时候，调用append方法。
builder.append(ch); // appends a single character
builder.append(str); // appends a string
String completedString = builder.toStringO;
```

	

StringBufferApi

```java
StringBuilder();
// 构建一个空字符串构建器。
int length();
// 返回一个构建器或者缓冲区中的代码单元数量（代码长度）。
StringBuilder append(Strubf str);
// 追加一个字符串并返回this。
StringBui1der append(char c)；
// 追加一个代码单元并返回 this。 
void setCharAt(int i,char c);
// 将第i个代码单元设置为c。
StringBuilder insert(int offset,String str);
// 在offset位置插入一个字符并返回this。
StringBuilder delete(int startIndex,int endIndex);
// 删除偏移量从 startindex 到-endlndex-1 的代码单元并返回 this
String toString();
// 返回一个与构建器或缓冲器内容相同的字符串。
```

## 输入输出

### 安全输入输出：

Scanner 输入是可见的。

Java SE 6 特别 引入了 Console 类实现这个目的。要想读取一个密码， 可以采用下列代码： 

```java
Console cons = System.console( ); 
String username = cons.readLine("User name: ")； 
char[ ] passwd = cons.readPassword("Password:"); 
```

为了安全起见，返回的密码存放在一维字符数组中， 而不是字符串中。

在对密码进 行处理之后，应该马上用一个填充值覆盖数组元素

### 格式化输出：

	java中沿用c语言中printf用于格式化输入输出，具体操作和c语言相通。

```java
System.out.printf("Hello, %s. Next year, you'll be SSd", name, age);
```

	 可以使用 s 转换符格式化任意的对象,， 对于任意实现了 Formattable 接口的对象都 将调用 formatTo 方法；否则将调用 toString 方法， 它可以将对象转换为字符串。
	
	可以使用静态的 String.format 方法创建一个格式化的字符串， 而不打印输出： 

```java
String.format("Hello, %s. Next year, you'll be %d", name, age); 
```

### 文件输入与输出：

要想对文件进行读取，就需要一个用 File 对象构造一个 Scanner 对象，如下所示： 

```java
Scanner in = new Scanner(Paths.get("niyflle.txt"), "UTF-8"); 
```

如果文件名中包含反斜杠符号，就要记住在每个反斜杠之前再加一个额外的反斜杠： “ c:\\mydirectory\\myfile.txt” 

```java
PrintWriter out = new PrintlulriterC'myfile.txt", "UTF-8");
```

如果文件不存在，创建该文件。可以像输出到 System.out—样使用 print、 println 以及 printf 命令。 



输入输出api：

```java
static Path get(String pathname)；
// 根据给定的路径名构造一个 Path。
```

## 作用域：

块作用域：这是我们开发之中常用的作用域之一。

## 大数值：

	基本的整数和浮点数精度不能够满足需求， 那么可以使用java.math 包中的两个 很有用的类：Biglnteger 和 BigDecimaL 。
	
	Biglnteger类实现了任意精度的整数运算， BigDecimal 实现了任意精度的浮点数运算。 

```java
//使用静态的 valueOf方法可以将普通的数值转换为大数值：
Biglnteger a = Biglnteger.valueOf(100); 
```

	遗憾的是，不能使用人们熟悉的算术运算符（如：+ 和 *) 处理大数值。 而需要使用大数 值类中的 add 和 multiply 方法。

```java
Biglnteger c = a.add(b); // c = a + b Biglnteger 
d = c.nultipiy(b.add(Biglnteger.valueOf(2))); // d = c * (b + 2)

```

	与 C++ 不同， Java 没有提供运算符重载功能。
	
	在设计彩票中彩概率程序的时候，我们可以采用大数值进行运算。

Apis：

Biglnteger

```java
Biglnteger add(Biglnteger other)； 
Biglnteger subtract(Biglnteger other)；
Biglnteger multipiy(Biginteger other)；
Biglnteger divide(Biglnteger other)；
Biglnteger mod(Biglnteger other)；
//返冋这个大整数和另一个大整数 other•的和、差、 积、 商以及余数。 
int compareTo(Biglnteger other) ；
  //  如果这个大整数与另一个大整数 other 相等， 返回 0; 如果这个大整数小于另一个大整 数 other, 返回负数； 否则， 返回正数。 
  static Biglnteger valueOf(1ong x)；
  //返回值等于 x 的大整数。 
```

BigDecimal 

```java
BigDecimal add(BigDecimal other)；
BigDecimal subtract(BigDecimal other)；
BigDecimal multipiy(BigDecimal other)；
BigDecimal divide(BigDecimal other RoundingMode mode)；
//返回这个大实数与另一个大实数 other 的和、 差、 积、 商。要想计算商， 必须给出舍 入方式 （rounding mode)。RoundingMode.HALF UP 是在学校中学习的四舍五入方式 (BP, 数值 0 到 4 舍去， 数值 5 到 9 进位） 。它适用于常规的计算。有关其他的舍入方 式请参看 Apr文档。
int compareTo(BigDecimal other) ；
//如果这个大实数与另一个大实数相等， 返回 0 ; 如果这个大实数小于另一个大实数， 返回负数； 否则，返回正数。 
static BigDecimal valueOf(1ong x) ；
static BigDecimal valueOf(1ong x,int scale) ；
//返回值为 X 或 x / 10scale 的一个大实数。

```

## 数组

数组是一种数据结构， 用来存储同一类型值的集合。

如果 a 是一个整型数组， a[i] 就是数组中下标为 i 的整数。 

在声明数组变量时， 需要指出数组类型 （数据元素类型紧跟 []) 和数组变量的名字。

下 面声明了整型数组 a: 

int[] a; 

不过， 这条语句只声明了变量 a， 并没有将 a 初始化为一个真正的数组。应该使用 new 运算 符创建数组。 

int[ ] a = new int[100];

这条语句创建了一个可以存储 100 个整数的数组。数组长度不要求是常量： newint[n] 会创建 一个长度为 n 的数组。 

```java
String[] names = new String[10];
```

forEach

```java
for (variable : collection) statement

for (int element : a) 

	System.out.println(element):
```

打印数组 a 的每一个元素，一个元素占一行。

for each 循环语句显得更加简洁、更不易出错（不必为下标的起始值和终止值而操心)。 

foreach 循环语句的循环变量将会遍历数组中的每个元素， 而不需要使用下标值。

## 匿名数组

```java
new int[] { 17, 19, 23, 29, 31, 37} 
```

	将创建一个新数组并利用括号中提供的值进行初始化，数组的大小就是初始值的 个数。使用这种语法形式可以在不创建新变量的情况下重新初始化一个数组。
	
	将 一个数组的所有值拷贝到一个新的数组中去， 就要使用 Arrays 类的 copyOf方法。

```java
int[] copiedLuckyNumbers = Arrays.copyOf(luckyNumbers, luckyNumbers.length); 
```

	第 2 个参数是新数组的长度。这个方法通常用来增加数组的大小： 

```java
luckyNumbers = Arrays.copyOf(luckyNumbers, 2 * luckyNumbers.length); 
```

数组排序：

```java
int[] a = new int[10000]；
Arrays.sort(a)；
```

我们在数组中排序我们使用sort方法。

这个方法使用了优化的快速排序算法。

```java
static void fi11(type[]a, type v) ；
```

将数组的所有数据元素值设置为 V。 

参数：a 类型为 int、long、short、char、byte、boolean、float 或 double 的数组。

	    v 与 a 数据元素类型相同的一个值。 