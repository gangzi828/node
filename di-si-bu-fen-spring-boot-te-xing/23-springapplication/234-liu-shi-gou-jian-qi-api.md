### 23.4 流式构建器API

如果你需要建立一个应用程序上下文的层次结构（多个具有父/子关系的上下文结构），或者如果你只是喜欢用“流式”构建器API，你可以使用SpringApplicationBuilder。

SpringApplicationBuilder允许您链式调用父类或者子类中的方法。

例如：

```
new SpringApplicationBuilder()
        .sources(Parent.class)
        .child(Application.class)
        .bannerMode(Banner.Mode.OFF)
        .run(args);
```

> 当创建一个应用程序上下文的层次结构时有一些限制，例如：Web组件必须包含在子范围内，同样的环境将用于父上下文和子上下文。具体可以参考`SpringApplicationBuilder`Javadoc文档来了解全部细节。

除了 spring框架的事件，比如[ContextRefreshedEvent](http://docs.spring.io/spring/docs/4.3.8.RELEASE/javadoc-api/org/springframework/context/event/ContextRefreshedEvent.html)事件，SpringApplication还发出一些额外的应用程序事件。

