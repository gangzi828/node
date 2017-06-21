### 27.3.4 自定义嵌入式servlet容器

可以使用Spring Environment属性配置常见的servlet容器设置。 通常您可以在application.properties文件中定义属性。

常用服务器设置包括：

* 网络设置：监听HTTP请求的端口（server.port），绑定到server.address的接口地址等
* 会话设置：会话是否持久（server.session.persistence），会话超时（server.session.timeout），会话数据的位置（server.session.store-dir）和会话cookie配置（server.session.cookie。\*）。
* 错误管理：错误页面的位置（server.error.path）等
* SSL
* HTTP压缩

Spring Boot尝试尽可能公开常见的设置，但并不总是可能的。 对于这些情况，专用命名空间提供服务器特定的定制（请参阅server.tomcat和server.undertow）。 例如，可以使用嵌入式servlet容器的特定功能来配置访问日志。

> 有关完整列表，请参阅ServerProperties类。

#### 程序化定制

如果您需要以编程方式配置嵌入式servlet容器，则可以注册实现EmbeddedServletContainerCustomizer接口的Spring bean。 EmbeddedServletContainerCustomizer提供对ConfigurableEmbeddedServletContainer的访问，其中包含许多自定义设置器方法。

```
import org.springframework.boot.context.embedded.*;
import org.springframework.stereotype.Component;

@Component
public class CustomizationBean implements EmbeddedServletContainerCustomizer {

    @Override
    public void customize(ConfigurableEmbeddedServletContainer container) {
        container.setPort(9000);
    }

}
```



