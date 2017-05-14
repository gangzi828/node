## 24 外部化配置

Spring Boot允许您外部化您的配置，以便您可以在不同的环境中使用相同的应用程序代码。 您可以使用属性文件，YAML文件，环境变量和命令行参数来外部化配置。 可以使用@Value注解将属性值直接注入到您的bean中，该注解可通过Spring环境抽象访问，或通过@ConfigurationProperties绑定到结构化对象。

