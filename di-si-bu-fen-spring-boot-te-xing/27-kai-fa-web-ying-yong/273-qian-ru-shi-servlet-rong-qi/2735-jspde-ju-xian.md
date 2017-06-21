### 27.3.5 JSP的局限

当运行使用嵌入式servlet容器（并打包为可执行jar）的Spring Boot应用程序时，JSP支持有一些限制。

使用Tomcat，如果您使用war包装，即可执行的war将会起作用，并且还可以部署到标准容器（不限于但包括Tomcat），那么它应该可以工作。 由于Tomcat中的硬编码文件模式，可执行的jar将无法正常工作。

对于Jetty，如果您使用war包，即可执行的war将会起作用，并且还可以部署到任何标准的集装箱，它应该可以工作。

Undertow不支持JSP。

创建自定义的error.jsp页面不会覆盖错误处理的默认视图，而应该使用自定义错误页面。

有一个[JSP示例](https://github.com/spring-projects/spring-boot/tree/v1.5.3.RELEASE/spring-boot-samples/spring-boot-sample-web-jsp)，所以你可以看到如何设置。



