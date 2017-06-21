### 27.2 JAX-RS和Jersey

如果您喜欢用于REST端点的JAX-RS编程模型，则可以使用其中一个可用的实现而不是Spring MVC。 如果您只是在应用程序上下文中注册他们的Servlet或Filter 作为@Bean，那么Jersey 1.x和Apache CXF的功能非常出色。 Jersey2.x有一些本地Spring支持，所以我们也提供自动配置支持在Spring Boot与相应的starter。

要开始使用Jersey 2.x，只需将spring-boot-starter-jersey作为依赖项，然后需要一个@Bean类型的ResourceConfig，您可以在其中注册所有端点：

```
@Component
public class JerseyConfig extends ResourceConfig {

    public JerseyConfig() {
        register(Endpoint.class);
    }

}
```

> Jersey对扫描可执行文件的支持是相当有限的。 例如，当运行可执行的war文件时，它无法扫描在WEB-INF / classes中找到的包中的端点。 为了避免这种限制，不应使用软件包方法，并且应使用上述寄存器方法单独注册端点。

您还可以注册任意数量的Bean，实现ResourceConfigCustomizer以实现更高级的自定义。

所有注册的端点都应为具有HTTP资源注释（@GET等）的@Components，例如。

```
@Component
@Path("/hello")
public class Endpoint {

    @GET
    public String message() {
        return "Hello";
    }

}
```



