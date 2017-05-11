## 23.3 自定义SpringApplication

如果系统默认的SpringApplication不能满足你的需求，你可以自定义SpringApplication。例如：想关闭Banner，你可以通过以下自定义SpringApplication来实现：

```
public static void main(String[] args) {
    SpringApplication app = new SpringApplication(MySpringConfiguration.class);
    app.setBannerMode(Banner.Mode.OFF);
    app.run(args);
}
```

在SpringApplication构造函数中传入的变量是spring的资源配置Bean。在大多数情况下，这些Bean都是来自@Configuration注解的类，但也有来自XML配置和包扫描提供的配置Bean。

