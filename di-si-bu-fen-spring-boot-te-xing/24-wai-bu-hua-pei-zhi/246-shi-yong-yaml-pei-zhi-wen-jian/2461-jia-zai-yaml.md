### 24.6.1 加载YAML

Spring Framework提供了两个方便的类，可用于加载YAML文档。 YamlPropertiesFactoryBean将YAML作为属性加载，并且YamlMapFactoryBean将加载YAML作为Map集合。

例如，如下的YAML文档：

```
environments:
    dev:
        url: http://dev.bar.com
        name: Developer Setup
    prod:
        url: http://foo.bar.com
        name: My Cool App
```

转换成对应的属性配置文件为：

```
environments.dev.url=http://dev.bar.com
environments.dev.name=Developer Setup
environments.prod.url=http://foo.bar.com
environments.prod.name=My Cool App
```

YAML列表表示为具有\[index\] 引用的属性键，例如YAML：

```
my:
   servers:
       - dev.bar.com
       - foo.bar.com
```

将被转换为如下属性：

```
my.servers[0]=dev.bar.com
my.servers[1]=foo.bar.com
```

要使用Spring DataBinder实用程序（这是@ConfigurationProperties所做的）绑定到这样的属性，您需要在类型为java.util.List（或Set）的目标bean中具有一个属性，并且您需要提供一个setter，或者用可变值初始化它，例如，这将绑定到上面的属性：

```
@ConfigurationProperties(prefix="my")
public class Config {

    private List<String> servers = new ArrayList<String>();

    public List<String> getServers() {
        return this.servers;
    }
}
```

配置列表时，需要特别小心，因为覆盖方式将无法正常工作。 在上面的示例中，当我的几个地方重新定义my.servers时，单个元素的目标是覆盖，而不是列表。 要确保具有较高优先级的PropertySource可以覆盖列表，您需要将其定义为单个属性：

my：

     servers：dev.bar.com，foo.bar.com



