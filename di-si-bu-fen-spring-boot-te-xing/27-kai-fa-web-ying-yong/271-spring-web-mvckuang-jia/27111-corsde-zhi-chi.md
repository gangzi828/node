### 27.1.11 CORS的支持

跨域资源共享（CORS）是大多数浏览器支持的W3C规范，允许您以灵活的方式指定什么样的跨域请求被授权，而不是使用如IFRAME或JSONP等一些不太安全和不太强大的方法。

从版本4.2起，Spring MVC支持CORS开箱即用。 在Spring Boot应用程序中使用@CrossOrigin注解标记控制器中的方法即可实现CORS配置，这里不需要任何额外的配置。 可以通过使用自定义的addCorsMappings（CorsRegistry）方法注册WebMvcConfigurer bean来定义全局CORS配置：

```
@Configuration
public class MyConfiguration {

    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurerAdapter() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/api/**");
            }
        };
    }
}
```



