

# 从迭代到java流操作

在处理集合时，我们通常会迭代遍历它的元素，并从每个元素上执行某项操作。例如，假设我们想要对某本书中的所有长单词进行计数。首先我们要将所有单词放入一个列表中：

```java
String contents = new String(Files.readAllBytes(Paths.get("alice.txt")),StandardCharsets.UTF_8);
List<String> words = Arrays.asList(contents.split("\\PL+"));
```

现在，我们可以迭代它了：

```java
long count = 0;
for(String word : words){
    if(word.length() > 12){
        count++;
    }
}
```

在使用流时，相同的操作看起来像下面那样：

```java
long count = words.stream()
	.filter(word -> word.length() > 12)
	.count();
```

流的版本比循环版本更容易阅读，因为，我们不必要去扫描整个代码去查找过滤和计数操作，方法名称直接告诉我们意欲何为。而且循环需要非常详细地指定操作顺序，而流却能以其想要的任何方式调度这些操作。

仅将stream修改为parallelStream就可以让流库以并行方式来执行过滤和计数。

```java
long count = words.parallelStream();
			.filter(w -> w.length() > 12)
             .count();
```

流操作，遵循了“做什么而非怎么做”的原则。

流和集合之间的区别：

1. 流不存储其元素，这些元素可能存储在底层集合中，或者是按需生成。
2. 流操作不会修改其数据源。例如，filter方法，不会从新的流中移除元素，而是会生成一个新的流，其中不包含被过滤掉的元素。
3. 流操作是尽可能惰性执行的。意味着直至需要其结果时，操作才会执行。例如，我需要查找前5个长单词，而不是所有的长单词，那么filter方法就会匹配到第5个单词之后才会停止过滤。因此我们甚至可以操作无限流。

操作流进程

1. 创建一个流
2. 指定初始流转换为其他流的中间操作，可能包含多个步骤。
3. 应用终止，产生结果。这个操作会强制执行之前的惰性操作。从此之后，这个再也不能用了。

```java
public class CountLongWords {
    public static void main(Stringp[]  args) throws IOException {
     	String(Files.readAllBytes(Paths.get("alice.txt")),StandardCharsets.UTF_8);
		List<String> words = Arrays.asList(contents.split("\\PL+"));
        
        long count = 0;
        for(String w : words){
            if(w.length() > 12){
                count++;
            }
        }
        System.out.println(count);
        
        count = words.stream().filter(w -> w.length() > 12).count();
        System.out.println(count);
        
        count = words.paralleStream().filter(w -> w.length() > 12).count();
        System.out.println(count);
    }
}
```

接口介绍：

API：java.util.stream.Stream<T> 8

Steam<T> filter(Predicate<?  super  T>  p)

产生一个流，其中包含当前流中算有的元素。

long count()

产生当前流中元素的数量。这是一个终止操作。

API：java.Collenction<E>1.2

default Stream<E> stream()

default Stream<E> parallelStream()