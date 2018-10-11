# 流的创建

​	我们可以用collection接口的stream方法将任何集合转换为一个流。如果有一个数组，那么可以是用的静态的Stream.of方法。

```java
Stream<String> words = Stream.of(contents.split("\\PL+"));
```

​	of方法具有可变长参数，因此我们可以构建具有任意数量引元的流；

```java
Stream<String> song = Stream.of("gently","down","the","stream");
```

​	使用Array.stream(array, from, to)可以从数组中位于from（包括）和to（不包括）的元素中创建一个流。

​	我们可以使用静态的Stream.empty方法;

```java
Stream<String> silence = Stream.empty();
// Generic type<String> is inferred; same as Stream.<String>empty();
```

​	Steam 接口有两个用于创建无限流的静态方法。generate方法会接受一个不包含任何引元的函数（或者从技术上讲，是一个Sipplier<T>接口的对象）。无论何时，只需要一个流类型的值，该函数就会被调用以产生一个这样的值。

​	我们可以像如下那样获取：

```java
	Stream<String> echos = Stream.generate(() -> "Echo");
```

​	或者像下面这样获取一个随机数的流：

```java
	Stream<Double> randoms = Stream.generate(Math::random);
```

​	为了产生无限序列，列如 0 1 2 3 …… ，可以使用iterate方法。它会接受一个 “ 种子 ”值，以及一个函数值（从技术上讲，是一个UnaryOperation<T>），并且会反复地将该函数应用到之前的结果上。 

​	例如：

```java
Stream<BigInteger> integers = Stream.iterate(BigInteger.ZERO, n -> n.add(BigInteger.ONE));
```

​	该序列中的第一个元素是种子BigInteger.ZERO，第二个元素是f(seed)，即1（作为大整数），下一个元素为f(f(seed))即为2，后续一次类推。

------

注意:
	JavaApi中有大量的方法，都可以产生流。例如：Pattern类有一个splitAsStream方法，它会按照某个正则表达式来分割一个charsequence对象。可以使用下面的语句来讲一个字符串分割为一个个的单词：

​	Stream<String> words = Pattern.compile("\\\PL+").splitAsStream(contents);

静态的Files.lines方法会返回一个包含了文件中所有行的stream：

​	伪代码

```java

```

​	

事例代码：

```java
package com.gjt.stream;


import java.io.IOException;
import java.math.BigInteger;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.util.List;
import java.util.regex.Pattern;
import java.util.stream.Collectors;
import java.util.stream.Stream;

/*
 * 创建流
 */
public class creatStream {
	
	public static<T> void show(String title, Stream<T> stream) {
		final int SIZE = 10;
		List<T> firstElement = stream
				.limit(SIZE + 1)
				.collect(Collectors.toList());
		System.out.println(title + ": ");
		for(int i = 0 ; i < firstElement.size() ; i++) {
			if(i > 0){
				System.out.println(",");
			}
			if(i < SIZE) {
				System.out.println(firstElement.get(i));
			}else {
				System.out.println("……");
			}
		}
		System.out.println();
	}
	
	public static void main(String[] args) throws IOException {
		// 读取单词文件
		String contents = new String(Files.readAllBytes(Paths.get("alice30.txt")),StandardCharsets.UTF_8);
		// 根据正则表达式分割单词
		Stream<String> words = Stream.of(contents.split("\\PL+"));
		show("words",words);
		
		Stream<String> song = Stream.of("gently","down","the","stream");
		show("song",song);
		
		Stream<String> silence = Stream.empty();
		show("silence", silence);
		
		Stream<String> echos = Stream.generate(() -> "Echo");
		show("echos",echos);
		
		Stream<Double> randoms = Stream.generate(Math::random);
		show("randoms",randoms);
		
		Stream<BigInteger> integers = Stream.iterate(BigInteger.ONE, n -> n.add(BigInteger.ONE));
		show("integers",integers);
		
		Stream<String> wordsAnotherWay = Pattern.compile("\\PL+").splitAsStream(contents);
		show("wordsAnotherWay",wordsAnotherWay);
		
		try(Stream<String> lines = Files.lines(Paths.get("alice30.txt"),StandardCharsets.UTF_8))
		{
			show("lines", lines);
		}
		
	}
}

```

API 接口：

```java
static<T> Stream<T> of(T... values)
```

