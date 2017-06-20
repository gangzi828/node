#### 27.1.5 静态内容

默认情况下，Spring Boot从classpath下的\`/static\`（\`/public\`，\`/resources\`或\`/META-INF/resources\`）文件夹，或从\`ServletContext\`根目录提供静态内容。这是通过Spring MVC的\`ResourceHttpRequestHandler\`实现的，你可以自定义\`WebMvcConfigurerAdapter\`并覆写\`addResourceHandlers\`方法来改变该行为（加载静态文件）。

在单机web应用中，容器会启动默认的servlet，并用它加载\`ServletContext\`根目录下的内容以响应那些Spring不处理的请求。大多数情况下这都不会发生（除非你修改默认的MVC配置），因为Spring总能够通过\`DispatcherServlet\`处理这些请求。

默认情况下，资源映射到/ \*\*，但可以通过spring.mvc.static-path-pattern来设置。 例如，将所有资源重定位到/ resources / \*\*可以实现如下：

```
spring.mvc.static-path-pattern=/resources/**
```

您还可以使用spring.resources.static-locations（使用目录位置列表替换默认值）来自定义静态资源位置。 如果这样做，默认的欢迎页面检测将切换到您的自定义位置，因此，如果在启动时您的任何位置中有一个index.html，它将是应用程序的主页。

除了上述“标准”静态资源位置之外，还提供了一个特殊情况用于Webjars内容。 如果使用Webjars格式打包，则/ jarjars / \*\*中具有路径的资源将从jar文件中提供。

> 如果您的应用程序将被打包为jar，请不要使用src/main/webapp目录。 虽然这个目录是一个通用的标准，但它只适用于war包，如果生成一个jar，它将被大多数构建工具忽略。

Spring Boot也支持Spring MVC提供的高级资源处理特性，可用于清除缓存的静态资源或对WebJar使用版本无感知的URLs。

如果想使用针对WebJars版本无感知的URLs（version agnostic），只需要添加\`webjars-locator\`依赖，然后声明你的Webjar。以jQuery为例，\`"/webjars/jquery/dist/jquery.min.js"\`实际为\`"/webjars/jquery/x.y.z/dist/jquery.min.js"\`，\`x.y.z\`为Webjar的版本。

> 如果使用JBoss，你需要声明\`webjars-locator-jboss-vfs\`依赖而不是\`webjars-locator\`，否则所有的Webjars将解析为\`404\`。

要使用缓存清除功能，以下配置将为所有静态资源配置缓存清除解决方案，该方案通过在URL中添加哈希值来实现，例如：

```
<link href="/css/spring-2a2d595e6ed9a0b24f027f2b63b134d6.css"/>:
```

```
spring.resources.chain.strategy.content.enabled=true
spring.resources.chain.strategy.content.paths=/**
```

> 对于Thymeleaf和FreeMarker模版引擎来说，在模版运行时会进行资源链接重写，这通过spring boot自动配置的ResourceUrlEncodingFilter来实现。当使用JSP时，应手动声明此过滤器。 其他模板引擎现在不会自动支持，但可以使用自定义模板宏/帮助程序和使用ResourceUrlProvider。

当使用比如JavaScript模块加载器动态加载资源时，重命名文件是不行的，这也是提供其他策略并能结合使用的原因。下面是一个"fixed"策略，在URL中添加一个静态version字符串而不需要改变文件名：

```
spring.resources.chain.strategy.content.enabled=true
spring.resources.chain.strategy.content.paths=/**
spring.resources.chain.strategy.fixed.enabled=true
spring.resources.chain.strategy.fixed.paths=/js/lib/
spring.resources.chain.strategy.fixed.version=v12
```



