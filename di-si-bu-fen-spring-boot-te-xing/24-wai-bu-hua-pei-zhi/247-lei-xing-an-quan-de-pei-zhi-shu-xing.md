### 24.7 类型安全的配置属性

使用@Value\(“$ {property}”\)注释来注入配置属性有时可能很麻烦，特别是如果您正在使用多个属性或数据是层次结构的属性。 Spring Boot提供了一种处理属性的替代方法，允许强类型的bean来管理和验证应用程序的配置。

```
package com.example;

import java.net.InetAddress;
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

import org.springframework.boot.context.properties.ConfigurationProperties;

@ConfigurationProperties("foo")
public class FooProperties {

    private boolean enabled;

    private InetAddress remoteAddress;

    private final Security security = new Security();

    public boolean isEnabled() { ... }

    public void setEnabled(boolean enabled) { ... }

    public InetAddress getRemoteAddress() { ... }

    public void setRemoteAddress(InetAddress remoteAddress) { ... }

    public Security getSecurity() { ... }

    public static class Security {

        private String username;

        private String password;

        private List<String> roles = new ArrayList<>(Collections.singleton("USER"));

        public String getUsername() { ... }

        public void setUsername(String username) { ... }

        public String getPassword() { ... }

        public void setPassword(String password) { ... }

        public List<String> getRoles() { ... }

        public void setRoles(List<String> roles) { ... }

    }
}
```

上述POJO定义了以下属性：

* foo.enabled，默认为false
* foo.remote-address，具有可以从String强制类型转换的类型
* foo.security.username，具有嵌套的“安全性”，其名称由属性名称决定。 特别是返回类型并没有被使用，可能是SecurityProperties
* foo.security.password
* foo.security.roles，一个String集合

> Getters和setter通常是强制性的，因为绑定是通过标准的Java Beans属性描述符，就像在Spring MVC中一样。在某些情况下可能会省略setter：
>
> * Maps，只要它们被初始化，需要一个getter，但不一定是一个setter，因为它们可以被binder修改。
>
> * 集合和数组可以通过索引（通常使用YAML）或使用单个逗号分隔值（属性）来访问。在后一种情况下，setter是强制性的。我们建议您始终为此类型添加一个setter。如果您初始化集合，请确保它不是不可变的（如上例所示）
>
> * 如果已初始化嵌套POJO属性（如上例中的Security字段），则不需要setter。如果您希望binder使用其默认构造函数即时创建实例，则需要一个setter。
>
> 有些人使用Project Lombok自动添加getter和setter。确保Lombok不会为这种类型生成任何特定的构造函数，因为它将被容器自动用于实例化对象。
>
> 另请参阅@Value和@ConfigurationProperties之间的差异。

您还需要列出在@EnableConfigurationProperties注释中注册的属性类：

```
@Configuration
@EnableConfigurationProperties(FooProperties.class)
public class MyConfiguration {
}
```

当@ConfigurationProperties bean以这种方式注册时，该bean将具有常规名称：&lt;prefix&gt; - &lt;fqn&gt;，其中&lt;prefix&gt;是@ConfigurationProperties注释中指定的环境密钥前缀，&lt;fqn&gt;是Bean的全限定名称。 如果注解不提供任何前缀，则仅使用该bean的完全限定名称。

上面示例中的bean名称将是foo-com.example.FooProperties。

即使上述配置将为FooProperties创建一个常规bean，我们建议@ConfigurationProperties仅处理环境，特别是不从上下文中注入其他bean。 话虽如此，@EnableConfigurationProperties注释也会自动应用于您的项目，以便使用@ConfigurationProperties注释的任何现有的bean都将从环境配置。 您可以通过确保FooProperties已经是一个bean来快速上面的MyConfiguration。

```
@Component
@ConfigurationProperties(prefix="foo")
public class FooProperties {

    // ... see above

}
```

这种配置方式与SpringApplication外部的YAML配置相当：

```
# application.yml

foo:
    remote-address: 192.168.1.1
    security:
        username: foo
        roles:
          - USER
          - ADMIN

# additional configuration as required
```

要使用@ConfigurationProperties bean，您可以像其他任何bean一样注入它们。

```
@Service
public class MyService {

    private final FooProperties properties;

    @Autowired
    public MyService(FooProperties properties) {
        this.properties = properties;
    }

     //...

    @PostConstruct
    public void openConnection() {
        Server server = new Server(this.properties.getRemoteAddress());
        // ...
    }

}
```

使用@ConfigurationProperties还可以生成IDE可以为自己的密钥提供自动完成的元数据文件，有关详细信息，请参见附录B，配置元数据附录。

