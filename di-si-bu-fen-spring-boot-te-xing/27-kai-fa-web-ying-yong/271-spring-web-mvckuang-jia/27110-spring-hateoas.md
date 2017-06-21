### 27.1.10 Spring HATEOAS

如果您正在开发一种利用超媒体的RESTful API，Spring Boot可为Spring HATEOAS提供自动配置，适用于大多数应用程序。 自动配置取代了使用@EnableHypermediaSupport的需要，并注册了一些Bean来简化构建基于超媒体的应用程序，包括LinkDiscoverers（用于客户端支持）和配置为将响应正确地组织到所需表示中的ObjectMapper。 ObjectMapper将根据spring.jackson。\*属性或Jackson2ObjectMapperBuilder bean（如果存在）进行自定义。

您可以使用@EnableHypermediaSupport控制Spring HATEOAS的配置。 请注意，这将禁用上述的ObjectMapper自定义。





