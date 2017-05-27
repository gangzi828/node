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



