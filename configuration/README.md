# 配置信息

Spring Boot只是简化了我们的配置，很多时候我们还是需要通过配置一些属性来辅助我们程序的运行的。

对于各种配置来说，无外乎两种操作：

- 在哪里写、怎么写
- 怎么读取

我们有这几个地方写配置：

- 配置文件

  - `application.properties`

  - `application.yml`

  以application开头是Spring Boot 的默认配置，把配置文件放在resource目录下就行了

- Shell 环境变量

  比如说我们的数据库密码不适合放在git仓库中，就可以放在shell 变量中

- 命令行参数

  JVM启动的时候传递参数进去，一般是在特殊情况下，用来覆盖之前的参数的

当有字段冲突的时候：

命令行参数  > shell变量 > `application-{profile}.properties` > `application-{profile}.yml `> `application.properties` > `application.yml`



这种优先级顺序是由理由的，越是灵活、已修改的优先级越高，保证了我们在项目打包后依旧可以灵活的修改



好接下来我们来一个个尝试一下。



## Git

这个文件是在这个commit下开始新的

```

* 5e8a533 (tag: status, origin/master, origin/HEAD, master)  status
* 3681bcf (tag: response) response
* 41c0bbf (HEAD -> config, tag: conf) conf
* 749abf5 (tag: request) request
* d230dd8 (tag: router-params) router-params
* 5000443 (tag: restart) restart
* 05ca9ea (tag: servlet) servlet
* f3ff11b (tag: init) init
```

- 前往 `41c0bbf (tag: conf) conf` 这个commit

  正如之前所说的，这个项目使用git 的分支来进行管理。每一份单独的知识点都会单独的开启一个branch。而

  config相关的知识点都放在config 这个branch，它是从master分支的这个commit开始提交的

- `git reset --hard 41c0bbf` 这个命令可以帮你到达相关的commit

- `git checkout -b config`这个命令可以帮你创建config分支。

- 你自己的项目分支没必要和我保持一致，我的分支管理主要是方便读者查看源代码用的
- 如果你想查看我每一下节的源代码，请记得切换到 config这个分支
- 切换完分支后，默认在最新的一个commit上，你还要前往原始的commit（也就是`41c0bbf (tag: conf)`），我就是从这个commit开始一步步提交代码的



## 目录

- [基本配置](./application.md)
- [shell 变量](./shell.md)