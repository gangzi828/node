#### 58.1.1 绑定服务

默认情况下，有关正在运行的应用程序的元数据以及服务连接信息作为环境变量（例如：$ VCAP\_SERVICES）作为环境变量显示给应用程序。 这种架构决定是由于Cloud Foundry的多沟槽（任何语言和平台都可以作为buildpack支持）性质; 过程范围的环境变量是语言无关的。

环境变量并不总是为最简单的API而设计，因此Spring Boot自动提取它们并将数据平坦化为可通过Spring环境抽象访问的属性：

```
@Component
class MyBean implements EnvironmentAware {

    private String instanceId;

    @Override
    public void setEnvironment(Environment environment) {
        this.instanceId = environment.getProperty("vcap.application.instance_id");
    }

    // ...

}
```

所有Cloud Foundry属性都以vcap为前缀。 您可以使用vcap属性来访问应用程序信息（如应用程序的公共URL）和服务信息（如数据库凭据）。 有关完整的详细信息，请参阅CloudFoundryVcapEnvironmentPostProcessor Javadoc文档。

> Spring Cloud Connectors项目更适合配置DataSource等任务。Spring Boot包括自动配置支持和Spring Boot启动器 - `spring-boot-starter-cloud-connectors`starter。



