### 26.2 控制台输出日志

默认的日志配置将在写入控制台时回显消息。 默认情况下会记录ERROR，WARN和INFO级别的消息。 您还可以通过启动您的应用程序--debug标志来启用“调试”模式。

```
$ java -jar myapp.jar --debug
```

> 您还可以在application.properties中指定debug = true。

当启用调试模式时，配置核心记录器（嵌入式容器，Hibernate和Spring Boot）的选择可以输出更多信息。 启用调试模式不会将应用程序配置为使用DEBUG级别记录所有消息。

或者，您可以使用--trace标志启动应用程序（或在您的application.properties中为trace = true）启用“跟踪”模式。 这将为选择的核心记录器（嵌入式容器，Hibernate模式生成和整个Spring组合）启用跟踪记录。



