### 25.1 添加激活的profiles

spring.profiles.active属性遵循与其他属性相同的优先级排序规则，PropertySource的优先级最高。 这意味着您可以在application.properties中指定活动配置文件，然后使用命令行开关替换它们。

有时，将特定于配置文件的属性添加到活动配置文件而不是替换它们是有用的。 spring.profiles.include属性可用于无条件添加活动配置文件。 SpringApplication入口点还有一个用于设置其他配置文件的Java API（即，在由spring.profiles.active属性激活的配置文件之上）：请参阅setAdditionalProfiles（）方法。

例如，当使用switch -spring.profiles.active = prod运行具有以下属性的应用程序时，proddb和prodmq配置文件也将被激活：

```
---
my.property: fromyamlfile
---
spring.profiles: prod
spring.profiles.include:
  - proddb
  - prodmq
```

请记住，可以在YAML文档中定义spring.profiles属性，以确定此特定文档何时包含在配置中。 有关详细信息，请参见第72.7节“根据环境更改配置”。

