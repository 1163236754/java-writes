# something for java three

## 接口（interface）技术

主要描述类具有什么功能，不用给出类的具体实现。一个类可以实现一个或多个接口，并在需要接口的地方，随时用来实现相应的对象。

为了让一个类实现一个接口，通常需要两个步骤

1.将类声明为实现给定的接口。

2.对接口中的所有方法进行定义。

需要试用implements关键字。

```java
class Employee implements Comparable
```
接口中所有的方法自动属于public，不需要再另外增加一个public关键字。

接口中还有一个没有明确说明的附加要求：在调用 X.c0mpareT0(y) 的时候，这个 compareTo方法必须确实比较两个对象的内容， 并返回比较的结果。 当 x 小于 y时， 返回一 个负数；当 x 等于 y时， 返回 0; 否则返回一个正数。

接口绝不能含 有实例域。

在 JavaSE 8之前， 也不能在接口中实现方法。



## comparator接口

这个接口，在java开发过程中是经常用到的，

