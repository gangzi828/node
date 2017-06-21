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

由于Endpoint是一个Spring @Component，它的生命周期由Spring管理，您可以使用@Autowired进行依赖注入或者使用@Value注入外部配置。默认情况下，Jersey servlet将被注册并映射到/ \*。您可以通过将@ApplicationPath添加到ResourceConfig来更改映射。

默认情况下，Jersey将以名为jerseyServletRegistration的ServletRegistrationBean类型的@Bean中设置为Servlet。默认情况下，servlet将被初始化，但是您可以使用spring.jersey.servlet.load-on-startup进行自定义。您可以通过创建自己的同一个名称来禁用或覆盖该bean。您也可以通过设置spring.jersey.type = filter（在这种情况下，@Bean来替换或替换为jerseyFilterRegistration），使用Filter代替Servlet。 servlet有一个@Order，您可以使用spring.jersey.filter.order设置。可以使用spring.jersey.init。\*来指定Servlet和过滤器注册初始化参数，以指定属性的映射。

这里有一个[Jersey](https://github.com/spring-projects/spring-boot/tree/v1.5.3.RELEASE/spring-boot-samples/spring-boot-sample-jersey)示例，所以你可以看到如何设置。还有一个Jarsey1.x示例。请注意，在Jersey1.x示例中，spring-boot maven插件已经被配置为打开一些Jersey jar，以便可以通过JAX-RS实现扫描（因为示例要求它们在其Filter注册中进行扫描） 。如果您的任何JAX-RS资源被打包为嵌套的jar，您可能需要执行相同操作。

