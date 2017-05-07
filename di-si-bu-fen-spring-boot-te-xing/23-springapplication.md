## 23  SpringApplication

SpringApplication类提供了一种便捷的方式来启动一个以main\(\)方法为启动入口的Spring应用程序。 在大多数情况下，您只需将启动过程委托给SpringApplication.run这个静态方法：

```
public static void main(String[] args) {
    SpringApplication.run(MySpringConfiguration.class, args);
}
```

当您的应用程序启动时，您将看到类似于以下内容：

     .   ____          _            __ _ _
     /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
    ( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
     \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
      '  |____| .__|_| |_|_| |_\__, | / / / /
     =========|_|==============|___/=/_/_/_/
     :: Spring Boot ::   v1.5.3.RELEASE

    2013-07-31 00:08:16.117  INFO 56603 --- [           main] o.s.b.s.app.SampleApplication            : Starting SampleApplication v0.1.0 on mycomputer with PID 56603 (/apps/myapp.jar started by pwebb)
    2013-07-31 00:08:16.166  INFO 56603 --- [           main] ationConfigEmbeddedWebApplicationContext : Refreshing org.springframework.boot.context.embedded.AnnotationConfigEmbeddedWebApplicationContext@6e5a8246: startup date [Wed Jul 31 00:08:16 PDT 2013]; root of context hierarchy
    2014-03-04 13:09:54.912  INFO 41370 --- [           main] .t.TomcatEmbeddedServletContainerFactory : Server initialized with port: 8080
    2014-03-04 13:09:56.501  INFO 41370 --- [           main] o.s.b.s.app.SampleApplication            : Started SampleApplication in 2.992 seconds (JVM running for 3.658)

默认情况下，spring boot将显示INFO级别的日志，这些日志包括应用程序启动的一些细节信息，例如，启动程序的用户信息。



