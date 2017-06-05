### 26.5 自定义日志配置

可以通过在类路径中包含相应的库来激活各种日志记录系统，并通过在类路径的根目录中提供合适的配置文件，或在Spring Environment属性logging.config指定的位置进一步定制。

您可以强制Spring Boot使用org.springframework.boot.logging.LoggingSystem系统属性使用特定的日志记录系统。 该值应该是LoggingSystem实现的全限定类名。 您还可以使用无值的值完全禁用Spring Boot的日志记录配置。

> 由于在创建ApplicationContext之前初始化日志记录，因此无法在Spring @Configuration文件中控制@PropertySources的日志记录。 系统属性和常规的Spring Boot外部配置文件工作正常。）

根据您的日志记录系统，将会加载以下文件：

| Logging System | Customization |
| :--- | :--- |
| Logback | `logback-spring.xml`,`logback-spring.groovy`,`logback.xml`or`logback.groovy` |
| Log4j2 | `log4j2-spring.xml`or`log4j2.xml` |
| JDK \(Java Util Logging\) | `logging.properties` |



