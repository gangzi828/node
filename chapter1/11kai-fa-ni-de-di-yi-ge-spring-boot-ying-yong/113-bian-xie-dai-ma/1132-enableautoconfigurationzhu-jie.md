#### 11.3.2 @EnableAutoConfiguration注解

第二个类级别的注解是`@EnableAutoConfiguration`，这个注解告诉Spring Boot根据添加的jar依赖猜测你想如何配置Spring。由于`spring-boot-starter-web`添加了Tomcat和Spring MVC，所以auto-configuration将假定你正在开发一个web应用，并对Spring进行相应地设置。

> **Starters和Auto-Configuration**：Auto-configuration设计成可以跟"Starters"一起很好的使用，但这两个概念没有直接的联系。你可以自由地挑选starters以外的jar依赖，Spring Boot仍会尽最大努力去自动配置你的应用。



