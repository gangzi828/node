### 24.6.5 合并YAML

如上所述，任何YAML内容最终都会转换为属性。 当通过配置文件覆盖“list”属性时，该过程可能是直观的。

例如，假设默认情况下，name和description属性为空的MyPojo对象。 让我们从FooProperties中公开MyPojo列表：

```
@ConfigurationProperties("foo")
public class FooProperties {

    private final List<MyPojo> list = new ArrayList<>();

    public List<MyPojo> getList() {
        return this.list;
    }

}
```

考虑 如下配置：

```
foo:
  list:
    - name: my name
      description: my description
---
spring:
  profiles: dev
foo:
  list:
    - name: my another name
```



