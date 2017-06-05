### 26.1 日志格式

Spring Boot的默认日志输出格式如下：

```
2014-03-05 10:57:51.112  INFO 45469 --- [           main] org.apache.catalina.core.StandardEngine  : Starting Servlet Engine: Apache Tomcat/7.0.52
2014-03-05 10:57:51.253  INFO 45469 --- [ost-startStop-1] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2014-03-05 10:57:51.253  INFO 45469 --- [ost-startStop-1] o.s.web.context.ContextLoader            : Root WebApplicationContext: initialization completed in 1358 ms
2014-03-05 10:57:51.698  INFO 45469 --- [ost-startStop-1] o.s.b.c.e.ServletRegistrationBean        : Mapping servlet: 'dispatcherServlet' to [/]
2014-03-05 10:57:51.702  INFO 45469 --- [ost-startStop-1] o.s.b.c.embedded.FilterRegistrationBean  : Mapping filter: 'hiddenHttpMethodFilter' to: [/*]
```

输出的日志包括如下几个部分：

* 日期和时间 - 毫秒精度和容易排序。
* 日志级别 - ERROR、WARN、INFO、DEGUB和TRACE。
* 进程ID。
* A ---分隔符来区分实际日志消息的开始。
* 线程名称 - 括在方括号中（可能会截断控制台输出）。
* 记录器名称 - 这通常是源类名（通常缩写）。
* 日志消息。

> 注意：Logback没有FATAL日志级别（映射到ERROR级别）





