

# servlet

	处理请求和发送响应的过程是由一种叫做Servlet的程序来完成的，并且Servlet是为了解决实现动态页面而衍生的东西。理解这个的前提是了解一些http协议的东西，并且知道B/S模式(浏览器/服务器)。 

	B/S:浏览器/服务器。 浏览器通过网址来访问服务器，比如访问百度，在浏览器中输入www.baidu.com，这个时候浏览器就会显示百度的首页，那么这个具体的过程，步骤是怎样的呢？这个就了解一下htttp请求了 。

	为什么要编写servlet？

	为了实现动态网页。

## 基本配置

1.新建一个servlet

我这里只继承了get和post方法，没有管其他的。

2.在wei.xml中配置（可以省略）

	在web.xml中配置MyServlet，为什么需要配置？让浏览器发出的请求知道到达哪个servlet，也就是让tomcat将封装好的request找到对应的servlet让其使用。

	后期应为webServlet注解的存在，直接是可以通过WebServlet("/Test")找到Servlet。

完成之后点开即可

## servlet原理

1.servlet的生命周期是什么？

	服务器启动的时（web.xml中配置load-on-startup = 1,默认值为0）或者第一次请求该servlet时，就会初始化一个Servlet对象，也就是会执行初始化方法init方法（ServletConfig conf ）该servlet对象去处理所有客户端的请求，在service(ServletRequest req，ServletResponse res)方法中执行最后服务器关闭时，才会销毁这个servlet对象，执行destroy()方法。

2.为什么创建的servlet是继承自httpServlet，而不是直接实现Servlet接口？

查看源码，httpServlet的继承结构。

```java
public abstract class HttpServlet extends GenericServlet
```
