## 23.3 自定义SpringApplication

如果系统默认的SpringApplication不能满足你的需求，你可以自定义SpringApplication。例如：想关闭Banner，你可以通过以下自定义SpringApplication来实现：

```
public static void main(String[] args) {
    SpringApplication app = new SpringApplication(MySpringConfiguration.class);
    app.setBannerMode(Banner.Mode.OFF);
    app.run(args);
}
```



