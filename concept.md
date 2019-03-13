# Spring Boot是如何工作的

其实对于任何一个Web服务程序来说，都会按照一下的步骤来执行
- 接收到一个http请求
- 解析请求报文的头部和请求体
- 提交给对应的路由函数
- 路由函数做出相应的处理
- 然后一个HTTP响应

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
使用Spring Boot是有点类似于面向注解编程。SB通过读取相关
被注解的类，方法以及参数来调度程序。
我们给Hello这个类添加了两个注解
- `@RestController`
  这个注解告诉SB这个类将来会用作控制器，它的方法将被用来处理
  HTTP请求。
- `@RequestMapping("/")`
  这个注解表明所有向请求路劲为`/`的请求都将由这个类处理

- `@GetMapping`
  这个方法表明这个路由下，所有的GET方法的请求由这个方法来处理

- `@PostMapping` `@PatchMapping` 。。。聪明的你一定
  推测出了还有这样的注解。是的，没错。

因为我们之前设置了`@RestController`，所以SB会把sayHello的
返回值写到HTTP响应的响应体里面，然后就有之前我们打开浏览器看到
的Hello World 字符串了。

Spring Boot的注解非常灵活，达到上面的效果有非常多的写法。
但是我认为过度的灵活只会带来混乱，所以这个教程我只会使用
一种我认为比较不错的注解风格，至于其他写法读者可以执行查阅官方文档。
