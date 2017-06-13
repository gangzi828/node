## 59 安装Spring Boot应用

除了使用java -jar运行Spring Boot应用程序外，还可以为Unix系统完成可执行的应用程序。 这使得在常见的生产环境中安装和管理Spring Boot应用程序非常容易。

要使用Maven创建“完全可执行”的jar，请使用以下插件配置：

```
<plugin>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-maven-plugin</artifactId>
    <configuration>
        <executable>true</executable>
    </configuration>
</plugin>
```



