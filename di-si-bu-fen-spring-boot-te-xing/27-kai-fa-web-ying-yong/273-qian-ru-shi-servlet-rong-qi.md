### 27.3 嵌入式Servlet容器

Spring Boot支持嵌入式Tomcat，Jetty和Undertow服务器。 大多数开发人员将简单地使用适当的“Starter”来获取完全配置的实例。 默认情况下，嵌入式服务器将侦听端口8080上的HTTP请求。

> 如果您选择在CentOS上使用Tomcat，请注意，默认情况下，临时目录用于存储编译的JSP，文件上传等。当您的应用程序运行时导致故障时，该目录可能会被tmpwatch删除。 为了避免这种情况，您可能需要自定义tmpwatch配置，以便tomcat \*目录不被删除，或配置server.tomcat.basedir，以便嵌入式Tomcat使用不同的位置。





