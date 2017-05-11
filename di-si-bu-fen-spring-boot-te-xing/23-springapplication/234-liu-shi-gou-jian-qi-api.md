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





