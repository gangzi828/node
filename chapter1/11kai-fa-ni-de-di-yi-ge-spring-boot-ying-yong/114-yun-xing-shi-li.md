### 11.4 运行示例

现在示例应用可以运行了。由于使用了`spring-boot-starter-parent`POM，这样我们就有了一个非常有用的run目标来启动程序。在项目根目录下输入`mvn spring-boot:run`启动应用：

    $ mvn spring-boot:run

      .   ____          _            __ _ _
     /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
    ( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
     \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
      '  |____| .__|_| |_|_| |_\__, | / / / /
     =========|_|==============|___/=/_/_/_/
     :: Spring Boot ::  (v1.5.3.RELEASE)
    ....... . . .
    ....... . . . (log output here)
    ....... . . .
    ........ Started Example in 2.222 seconds (JVM running for 6.514)

如果使用浏览器打开[localhost:8080](http://localhost:8080/)，你应该可以看到如下输出：

```
Hello World!

```

点击`ctrl-c`温雅地关闭应用程序。

