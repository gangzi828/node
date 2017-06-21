### 27.3.1 Servlets, Filters, and listeners

使用嵌入式servlet容器时，可以通过使用Spring bean或通过扫描Servlet组件从Servlet规范（例如HttpSessionListener）注册Servlet，过滤器和所有监听器。

#### 注册Servlets, Filters, and listeners作为 Spring beans

任何Servlet，Filter或Servlet \*作为Spring bean的Listener实例将被注册到嵌入式容器中。 如果要在配置过程中引用application.properties中的值，这可能会特别方便。

默认情况下，如果上下文只包含一个Servlet，它将映射到/。 在多个Servlet bean的情况下，bean名称将被用作路径前缀。 过滤器将映射到/ \*。

如果基于约定的映射不够灵活，可以使用ServletRegistrationBean，FilterRegistrationBean和ServletListenerRegistrationBean类进行完全控制。



