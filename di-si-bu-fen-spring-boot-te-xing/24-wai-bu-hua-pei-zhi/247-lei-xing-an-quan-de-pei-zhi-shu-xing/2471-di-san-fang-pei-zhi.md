#### 24.7.1 第三方配置

除了使用@ConfigurationProperties来注释类，还可以在public @Bean方法中使用它。 当您希望将属性绑定到不受控制的第三方组件时，这可能特别有用。

要从“环境”属性配置一个bean，请将@ConfigurationProperties添加到其Bean注册中：

```
@ConfigurationProperties(prefix = "bar")
@Bean
public BarComponent barComponent() {
    ...
}
```

使用bar前缀定义的任何属性将以与上述FooProperties示例类似的方式映射到该BarComponent bean。

