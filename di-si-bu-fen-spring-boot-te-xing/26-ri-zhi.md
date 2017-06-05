## 26 日志

Spring Boot使用Commons Logging进行所有内部日志记录，但底层日志实现确实开放的。 默认的日志实现为Java Util Logging，Log4J2和Logback提供。 在每种情况下，记录器都预配置为使用控制台输出和可选文件输出。

默认情况下，如果使用'Starters'，spring boot将使用Logback记录日志。 还包括适当的Logback路由，以确保使用Java Util Logging，Commons Logging，Log4J或SLF4J的依赖库都能正常工作。

> 有很多可用于Java的日志记录框架。 如果上面的列表看起来很混乱，别担心。 一般来说，您不需要更改日志依赖关系，并且一般情况下Spring Boot的默认日志配置将正常工作。





