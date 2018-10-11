# something for java two

## java可见性控制

1 ) 仅对本类可见 private。

2 ) 对所有类可见 public。

3 ) 对本包和所有子类可见 protected。

 4 ) 对本包可见— —默认， 不需要修饰符。

## equals方法

Object类中的equals方法用于检测一个对象是否等于另外一个对象。在Object类中，这个方法将判断两个对象是否具有相同的引用。如果两个对象具有相同的引用，他们一定是相等的。

Tips:

 	为了防备 比较参数都为null的情况， 需要使用 Objects.equals 方法。如 果两个参数都为 null， Objects.equals(a，b) 调用将返回 true ; 如果其中一个参数为 null, 则返回 false ;

原始：

```java
return name.equals(other.name) 
    && salary = other,salary 
    && hi reDay.equals(other,hi reDay):
```

修改后：

```java
return Objects.equals(name, other.name) 
	&& salary == other.salary 
	&& Object.equals(hireDay, other.hireDay);
```



## 数组

Employee[] staff = new Employee[10];

obj  = staff; // OK

obj = new int[10]; //OK

所有的数组类塱，不管是对象数组还是基本类型的数组都扩展了 Object 类。 

getClass方法将返回一个对象所属的类，

令人烦恼的是， 数组继承了 object 类的 toString 方法，数组类型将按照旧的格式 打印。

例如： 

int[] luckyNumbers = { 2, 3, 5, 7S llf 13 };

 String s = "" + luckyNumbers;

 生成字符串“ [I@la46e30”（前缀 [I 表明是一个整型数组） 。修正的方式是调用静态 方法 Arrays.toString。

代码：

 String s = Arrays.toString(luckyNumbers); 将生成字符串“ [2,3,5,7,11,13]”。 

## 反射

反射机制的功能极其强大，在下面可以看 到， 反射机制可以用来：

 •在运行时分析类的能力。

 •在运行时查看对象， 例如， 编写一个 toString方法供所有类使用。

 •实现通用的数组操作代码。

 •利用 Method 对象， 这个对象很像中的函数指针

### class类

在程序运行期间，java运行时系统始终为所有的对象维护一个被称为运行时的类型标识。

这个信息跟踪着每个对象所属的类。虚拟机利用运行时类型信息选择相应的方法执行。 

可以通过专门的 Java 类访问这些信息。保存这些信息的类被称为 Class, 这个名 字很容易让人混淆。

Object 类中的 getClass( ) 方法将会返回一个 Class 类型的实例。 

获取类型:

方法一：

```java
Employee e;
 Class cl = e.getClass();
```

方法二:

调用静态方法forName

```java
String dassName = "java.util.Random"; 
Class cl = Class.forName(className); 
```

这个方法必须className是类名或接口名才可以执行。同时应该提供一个异常处理器。

将 forName 与 newlnstance 配合起来使用， 可以根据存储在字符串中的类名创建一个对象 。

```java
String s = "java.util.Random"; 

Object m = Class.forName(s).newlnstance();
```

