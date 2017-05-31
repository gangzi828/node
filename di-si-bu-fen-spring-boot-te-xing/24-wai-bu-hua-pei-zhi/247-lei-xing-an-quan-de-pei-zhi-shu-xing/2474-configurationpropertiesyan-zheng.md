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

为了验证嵌套属性的值，您必须将关联字段注释为@Valid以触发其验证。 例如，基于上述FooProperties示例：

```
@ConfigurationProperties(prefix="connection")
@Validated
public class FooProperties {

    @NotNull
    private InetAddress remoteAddress;

    @Valid
    private final Security security = new Security();

    // ... getters and setters

    public static class Security {

        @NotEmpty
        public String username;

        // ... getters and setters

    }

}
```

您还可以通过创建名为configurationPropertiesValidator的bean定义来添加自定义的Spring Validator。 @Bean方法应声明为静态。 配置属性验证器在应用程序的生命周期早期创建，并声明@Bean方法，因为static允许创建bean，而无需实例化@Configuration类。 这避免了早期实例化可能引起的任何问题。 有一个属性验证样本，所以你可以看到如何设置。

spring-boot-actuator模块包括一个暴露所有@ConfigurationProperties bean的端点。 只需将您的Web浏览器指向/ configprops或使用等效的JMX端点。 具体细节请参阅生产就绪功能那一章。

