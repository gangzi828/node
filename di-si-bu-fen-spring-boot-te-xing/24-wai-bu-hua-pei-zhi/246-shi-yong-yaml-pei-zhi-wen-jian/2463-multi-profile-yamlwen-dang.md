### 24.6.3 Multi-profile YAML文档

您可以使用spring.profiles键指定单个文件中的多个配置文件特定的YAML文档，以指示文档何时应用。 例如：

```
server:
    address: 192.168.1.100
---
spring:
    profiles: development
server:
    address: 127.0.0.1
---
spring:
    profiles: production
server:
    address: 192.168.1.120
```

在上面的示例中，如果开发环境的配置文件处于活动状态，则server.address属性将为127.0.0.1。 如果开发和生产环境的配置文件均未启用，则该属性的值将为192.168.1.100。

如果应用程序上下文启动时没有显式激活，默认配置文件将被激活。 所以在这个YAML中，我们为security.user.password设置一个仅在“默认”配置文件中可用的值：

```
server:
  port: 8000
---
spring:
  profiles: default
security:
  user:
    password: weak
```

而在此示例中，密码始终被设置，因为它没有附加到任何配置文件，并且必须在必要时在所有其他配置文件中显式重置密码：

```
server:
  port: 8000
security:
  user:
    password: weak
```

使用“spring.profiles”元素指定的可以选择使用！ 字符。 如果为单个文档指定了否定和非否定的配置文件，则至少有一个非否定配置文件必须匹配，没有否定配置文件可能匹配。

