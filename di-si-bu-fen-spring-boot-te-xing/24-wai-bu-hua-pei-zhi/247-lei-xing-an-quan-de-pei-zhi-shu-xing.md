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

Getters和setter通常是强制性的，因为绑定是通过标准的Java Beans属性描述符，就像在Spring MVC中一样。在某些情况下可能会省略setter：

* Maps，只要它们被初始化，需要一个getter，但不一定是一个setter，因为它们可以被binder修改。

* 集合和数组可以通过索引（通常使用YAML）或使用单个逗号分隔值（属性）来访问。在后一种情况下，setter是强制性的。我们建议您始终为此类型添加一个setter。如果您初始化集合，请确保它不是不可变的（如上例所示）
* 如果已初始化嵌套POJO属性（如上例中的Security字段），则不需要setter。如果您希望binder使用其默认构造函数即时创建实例，则需要一个setter。

有些人使用Project Lombok自动添加getter和setter。确保Lombok不会为这种类型生成任何特定的构造函数，因为它将被容器自动用于实例化对象。



