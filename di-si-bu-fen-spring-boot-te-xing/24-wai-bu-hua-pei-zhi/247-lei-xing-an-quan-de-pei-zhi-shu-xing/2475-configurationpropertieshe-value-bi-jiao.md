#### 24.7.5 @ConfigurationProperties和 @Value比较

| Feature | `@ConfigurationProperties` | `@Value` |
| :--- | :--- | :--- |
| [Relaxed binding](http://docs.spring.io/spring-boot/docs/1.5.3.RELEASE/reference/htmlsingle/#boot-features-external-config-relaxed-binding) | Yes | No |
| [Meta-data support](http://docs.spring.io/spring-boot/docs/1.5.3.RELEASE/reference/htmlsingle/#configuration-metadata) | Yes | No |
| `SpEL`evaluation | No | Yes |

如果您为自己的组件定义了一组配置keys，我们建议您将它们分组到使用@ConfigurationProperties注释的POJO中。 还请注意，由于@Value不支持轻松的绑定，如果您需要使用环境变量提供值，那么它不是一个很好的候选人。

最后，当您可以在@Value中编写一个SpEL表达式时，这些表达式不会从应用程序属性文件中处理。

