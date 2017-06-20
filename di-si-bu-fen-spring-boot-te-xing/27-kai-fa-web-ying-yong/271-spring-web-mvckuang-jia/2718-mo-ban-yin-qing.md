#### 27.1.8 模版引擎

除了REST Web服务，您还可以使用Spring MVC来提供动态HTML内容。 Spring MVC支持各种模板技术，包括Thymeleaf，FreeMarker和JSP。 许多其他模板引擎也运行自己的Spring MVC集成。

Spring Boot包括对以下模板引擎的自动配置支持：

* [FreeMarker](http://freemarker.org/docs/)
* [Groovy](http://docs.groovy-lang.org/docs/next/html/documentation/template-engines.html#_the_markuptemplateengine)
* [Thymeleaf](http://www.thymeleaf.org/)
* [Mustache](https://mustache.github.io/)

> 如果可能，当使用嵌入式servlet容器时，应避免使用JSP，JSP在jar包运行时有几个的限制。

当您使用默认配置的模板引擎之一时，您的模板将从src / main / resources / templates自动获取。

> IntelliJ IDEA根据运行应用程序的方式对类路径进行不同的排序。 通过其主要方法在IDE中运行应用程序将导致使用Maven或Gradle或其打包的jar运行应用程序时的不同顺序。 这可能会导致Spring Boot找不到类路径上的模板。 如果您受到此问题的影响，您可以重新排序IDE中的类路径，以便首先放置模块的类和资源。 或者，您可以配置模板前缀以搜索类路径上的每个模板目录：classpath \*：/ templates /。





