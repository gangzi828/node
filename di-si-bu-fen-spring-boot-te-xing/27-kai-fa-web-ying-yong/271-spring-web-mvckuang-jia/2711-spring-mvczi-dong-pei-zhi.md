### 27.1.1 Spring MVC自动配置

Spring Boot提供了适用于大多数应用程序的Spring MVC的自动配置。

自动配置在Spring的默认值之上添加以下功能：

* 包含ContentNegotiatingViewResolver和BeanNameViewResolver bean。
* 支持提供静态资源，包括对WebJars的支持（见下文）。
* Converter，GenericConverter，Formatter beans的自动注册。
* 支持HttpMessageConverters（见下文）。
* 自动注册MessageCodesResolver（见下文）。
* 静态index.html支持。
* 自定义Favicon支持（见下）。
* 自动使用ConfigurableWebBindingInitializer bean（见下文）。

如果要保留Spring Boot MVC功能，并且您只需要添加其他MVC配置（拦截器，格式化程序，视图控制器等），则可以添加自己的WebConfigurerAdapter类型的@Configuration类，但不能使用@EnableWebMvc。 如果要提供RequestMappingHandlerMapping，RequestMappingHandlerAdapter或ExceptionHandlerExceptionResolver的自定义实例，您可以声明一个提供此类组件的WebMvcRegistrationsAdapter实例。

如果要完全控制Spring MVC，可以使用@EnableWebMvc添加您自己的@Configuration注释。

