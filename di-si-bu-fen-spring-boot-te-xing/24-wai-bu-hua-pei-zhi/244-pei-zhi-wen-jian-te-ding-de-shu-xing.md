### 24.4 配置文件特定的属性

除了application.properties文件外，还可以使用命名约定application- {profile} .properties定义特定于配置文件的属性。 Environment具有一组默认配置文件\(默认为\[default\]\)，如果没有设置活动配置文件（即，如果没有显式激活配置文件，则加载了来自application-default.properties的属性）。

特定于配置文件的属性从与标准application.properties相同的位置加载，配置文件特定文件始终覆盖非特定文件，而不管特定于配置文件的文件是否在打包的jar内部或外部。

如果指定了几个配置文件，则应用最后一个。 例如，由spring.profiles.active属性指定的配置文件在通过SpringApplication API配置的配置之后添加，因此具有高的优先级。

> 如果您在spring.config.location中指定了任何文件，则不会考虑这些文件的特定于配置文件的变体。 如果还要使用特定于配置文件的属性，请在spring.config.location中使用目录。





