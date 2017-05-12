## 23.6 Web环境

SpringApplication会尝试根据用户的意图来创建正确类型的应用程序上下文。默认情况下，如果你正在开发的是非Web应用程序，则创建AnnotationConfigApplicationContext，Web应用程序则创建AnnotationConfigEmbeddedWebApplicationContext上下文。

用于确定应用程序是否为“Web环境”的算法是相当简单（基于几个类的存在）。如果你需要覆盖默认设置，可以使setWebEnvironment（boolean webEnvironment）。

因此，可以通过调用setApplicationContextClass（...）来完全控制应用程序的上下文。

> 当JUnit测试中使用SpringApplication时，通常需要调用setWebEnvironment（false\)



