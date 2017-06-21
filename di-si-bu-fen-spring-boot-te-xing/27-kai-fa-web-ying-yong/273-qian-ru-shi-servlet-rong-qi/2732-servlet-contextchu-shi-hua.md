### 27.3.2 Servlet Context初始化

嵌入式servlet容器不会直接执行Servlet 3.0+ javax.servlet.ServletContainerInitializer接口或Spring的org.springframework.web.WebApplicationInitializer接口。 这种设计旨在降低war包中运行的第三方库的风险，从而不破坏Spring Boot应用程序。

如果您需要在Spring Boot应用程序中执行servlet上下文初始化，则应注册一个实现org.springframework.boot.context.embedded.ServletContextInitializer接口的bean。 单个onStartup方法提供对ServletContext的访问，并且如果需要，可以轻松地用作现有WebApplicationInitializer的适配器。

#### 扫描Servlets, Filters, and listeners

使用嵌入式容器时，可以使用@ServletComponentScan启用@WebServlet，@WebFilter和@WebListener注释类的自动注册。

> @ServletComponentScan将在独立容器中不起作用，其中将使用容器的内置发现机制。





