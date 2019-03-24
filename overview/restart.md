# 自动重启

之前的一直手动重启是不是很累? SpringBoot中提供相关的模块帮我们自动重启。

添加这个依赖：

``` xml
<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-devtools</artifactId>
		<optional>true</optional>
</dependency>
```

然后Spring Boot就会在classpath 更新的时候快速的重启服务器(这种重启比我们手动的要快很多)。

那么什么时候classpath会更新呢？

- 在Eclipse中，保存修改过的文件
- 在IntelliJ 中，`Build -> Build Project`

![](./reload/build.png)

上面两种行为会触发SpringBoot的重启。

### 为什么这种方式重启速度很快呢？

Spring Boot 内部有两个类加载器

- base classloader: 用来加载各种依赖的jar包这种基本不会变化的类
- restart classloader：用来加载用户开发中的类

每次重启的时候，实际上只是重启了restart classloader，所以会很快



## Git 版本

```bash
git checkout restart
git diff servlet restart
```

