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

使用Gradle，等效配置将是：

```
springBoot {
    executable = true
}
```

然后，您可以通过键入./my-application.jar（其中my-application是您的工件的名称）来运行应用程序。

> 完全可执行的jar通过在文件的前面嵌入一个额外的脚本来工作。 并不是所有的工具目前都接受这种格式，所以你可能并不总是能够使用这种技术。

> 默认脚本支持大多数Linux发行版，并在CentOS和Ubuntu上进行测试。 其他平台，如OS X和FreeBSD，将需要使用自定义的嵌入式LunchScript。

> 当运行完全可执行的jar时，它将使用jar的目录作为工作目录。





