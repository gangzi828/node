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

有些事件是在ApplicationContext创建之前触发的，因此不能通过@Bean的方式注册事件监听器。您可以通过SpringApplication.addListeners（...）或SpringApplicationBuilder.listeners（...）方法来进行注册。

> 如果你想让这些监听在程序创建的时候自动注册，您可以添加一个META-INF/ spring.factories文件到您的项目中，并通过使用org.springframework.context.ApplicationListener键来注册监听器。
>
> org.springframework.context.ApplicationListener= com.example.project.MyListener

随着应用程序的启动，应用程序事件监听器将以如下顺序被触发：

* 在程序运行开始，但是在注册监听器和初始化之前的所有处理前，发送一个ApplicationStartingEvent事件。
* 在Environment被应用于已知上下文，但是在上下文创建之前，发送一个ApplicationEnvironmentPreparedEvent事件。
* 在refresh开始之前，但在Bean定义已被加载之后，发送一个ApplicationPreparedEvent事件。
* 在refresh执行之后，并且其他相关的回调接口已经准备就绪，程序可以接收请求，发送一个ApplicationReadyEvent事件。
* 在应用程序启动过程中抛出异常时，发送一个ApplicationFailedEvent事件。







