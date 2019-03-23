## 为什么使用Spring Boot？

网上有很多优秀的文章说为什么要使用它，我就不重复了，大家可以google一下。

- <http://www.ityouknow.com/springboot/2018/06/12/spring-boo-java-simple.html>
- <https://dzone.com/articles/why-springboot>(英文)



我来对`内置容器`这一点说说自己的看法吧。

- 我们知道现在的web 服务器基本都是基于HTTP协议和浏览器进行沟通的
- JRE中没有支持快速构建HTTP服务器的方案
- nodejs python等脚本语言的安装包中就内置了HTTP服务器



这使得Java web开发人员不得不使用Tomcat之类的web 容器，开发的速度明显慢于其他的脚本语言。

Spring boot 内置容器填补了JRE的缺失的部分，真的大大提高了开发速度。



## Spring Boot是如何工作的

其实对于任何一个Web服务程序来说，都会按照一下的步骤来执行
- 接收到一个http请求
- 解析请求报文的头部和请求体
- 提交给对应的路由函数
- 路由函数做出相应的处理
- 然后一个HTTP响应

这种基本的处理流程是万年不变的。

分析下下面的代码

``` java
@RestController
@RequestMapping("/")
public class Hello {
    @GetMapping
    public String sayHello(){
        return "Hello world";
    }
}
```
使用Spring Boot是有点类似于面向注解编程。它通过读取相关被注解的类，方法以及参数来调度程序。

上面的代码中，我们给Hello这个类添加了两个注解

- `@RestController`
  这个注解告诉S B这个类将来会用作控制器，它将被用来处理HTTP请求。
- `@RequestMapping("/")`
  这个注解表明所有url路径为`/`的请求都将由这个类处理

- `@GetMapping`
  这个方法表明这个路由下，所有的GET方法的请求由这个方法来处理

- `@PostMapping` `@PatchMapping` 。。。聪明的你一定
  推测出了还有这样的注解。是的，没错。

因为我们之前设置了`@RestController`，所以S B会把sayHello的
返回值写到HTTP响应的响应体里面，然后就有之前我们打开浏览器看到
的Hello World 字符串了。

Spring Boot的注解非常灵活，达到上面的效果有非常多的写法。
但是我认为过度的灵活只会带来混乱，所以这个教程我只会使用
一种我认为比较不错的注解风格，至于其他写法读者可以执行查阅官方文档。
