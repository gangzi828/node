## 24 外部化配置

Spring Boot允许您外部化您的配置，以便您可以在不同的环境中使用相同的应用程序代码。 您可以使用属性文件，YAML文件，环境变量和命令行参数来外部化配置。 可以使用@Value注解将属性值直接注入到您的bean中，该注解可通过Spring环境抽象访问，或通过@ConfigurationProperties绑定到结构化对象。

Spring Boot使用非常特殊的PropertySource命令来覆盖属性值。 属性按以下顺序考虑：

1. 在用户家目录下的[Devtools](http://docs.spring.io/spring-boot/docs/1.5.3.RELEASE/reference/htmlsingle/#using-boot-devtools-globalsettings)全局配置文件，（当devtools处于活跃状态时，`~/.spring-boot-devtools.properties`） 
2. 在测试类中的[`@TestPropertySource`](http://docs.spring.io/spring/docs/4.3.8.RELEASE/javadoc-api/org/springframework/test/context/TestPropertySource.html)
3. @SpringBootTest\#properties注解属性
4. 命令行参数
5. SPRING\_APPLICATION\_JSON的属性（）
6. ServletConfig初始化参数
7. ServletContext初始化参数
8. java:comp/env中的JNDI属性
9. Java系统属性（System.getPropertis\(\)）
10. 系统环境变量
11. random.\*形式定义的RandomValuePropertySource属性
12. 应用程序的jar包之外通过[Profile](http://docs.spring.io/spring-boot/docs/1.5.3.RELEASE/reference/htmlsingle/#boot-features-external-config-profile-specific-properties)来指定的application.properties文件（application-{profile}.properties或者 YAML 形式）
13. 应用程序的jar包之内通过[Profile](http://docs.spring.io/spring-boot/docs/1.5.3.RELEASE/reference/htmlsingle/#boot-features-external-config-profile-specific-properties)来指定的application.properties文件（application-{profile}.properties或者 YAML 形式）
14. 应用程序的jar包之外的application.properties文件（application-{profile}.properties或者 YAML 形式）
15. 应用程序的jar包之内的application.properties文件（application-{profile}.properties或者 YAML 形式）
16. @Configutation注解的配置类中@PropertySource注解的属性
17. 通过 SpringApplication.setDefaultProperties指定的默认配置属性

为了展示一个完整的示例，这里我们假设已经定义了一个@Component注解的Bean，该Bean拥有name属性：

```
import org.springframework.stereotype.*
import org.springframework.beans.factory.annotation.*

@Component
public class MyBean {

    @Value("${name}")
    private String name;

    // ...

}
```

在你的应用程序类路径中（例如jar包中），可以通过application.properties给name属性提供一个默认的值。 在新环境中运行时，可以在您的jar外部提供一个application.properties来覆盖该名称; 对于一次性测试，您可以使用特定的命令行开关启动（例如，java -jar app.jar --name =“Spring”）。

