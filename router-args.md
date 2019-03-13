# 路由参数
在Spring 中配置路由参数很简单

``` java
@GetMapping("/{tid}")
public String getBookById(@PathVariable int tid){
  return "tid: " + tid;
}
```
我们只要使用花括号将路由中的名称括起来，Spring就会把它当做是
一个变量。然后我们在方法的参数中通过`@PathVariable`给我们的
变量添加注解，SpringBoot在运行时就会把读取到的变量的值传递给
我们的方法。

创建下面的类。这是一个books的路由，用户可以通过书的tid或者
书类型+作者来访问书的信息。
``` java
package com.github.fish56.HelloSpringBoot.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("/books")
public class Books {
    @GetMapping
    public String booksList(){
        return "books router";
    }

    @GetMapping("/{tid}")
    public String getBookById(@PathVariable int tid){
        return "This is book " + tid;
    }

    @GetMapping("/{type}/{author}")
    public String getBook(@PathVariable String type, @PathVariable String author){
        return String.format("Type of this book: %s; Author: %s", type, author);
    }
}
```
同时我们也可以使用嵌套路由

![](./router/idea.png)
![](./router/tid.png)
![](./router/type.png)

## Git 版本
``` bash
$ git checkout router-params
$ git diff router-params servlet
```