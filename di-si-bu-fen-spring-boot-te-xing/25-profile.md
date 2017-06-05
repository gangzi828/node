## 25 Profile配置

spring boot Profile配置提供了隔离应用程序部分配置的方法，并使其仅在某些环境中可用。 任何@Component或@Configuration都可以使用@Profile进行标记，以限制其加载时间：

```
@Configuration
@Profile("production")
public class ProductionConfiguration {

    // ...

}
```

以普通的Spring方式，您可以使用spring.profiles.active Environment属性来指定哪些配置文件处于活动状态。 您可以以任何常规方式指定属性，例如，您可以将其包含在您的application.properties中：

```
spring.profiles.active=dev,hsqldb
```

或者使用命令行--spring.profiles.active = dev，hsqldb在命令行中指定。

