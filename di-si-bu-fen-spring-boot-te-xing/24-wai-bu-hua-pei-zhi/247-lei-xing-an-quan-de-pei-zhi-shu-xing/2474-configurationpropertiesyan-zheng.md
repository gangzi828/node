#### 24.7.4 @ConfigurationProperties验证

当Spring的@Validated注释注释时，Spring Boot将尝试验证@ConfigurationProperties类。 您可以直接在配置类上使用JSR-303 javax.validation约束注释。 只需确保您的类路径中符合JSR-303实现，然后在您的字段中添加约束注释：

```
@ConfigurationProperties(prefix="foo")
@Validated
public class FooProperties {

    @NotNull
    private InetAddress remoteAddress;

    // ... getters and setters

}
```





