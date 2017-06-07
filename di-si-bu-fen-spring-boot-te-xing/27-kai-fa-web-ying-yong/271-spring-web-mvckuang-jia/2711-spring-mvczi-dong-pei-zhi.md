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





