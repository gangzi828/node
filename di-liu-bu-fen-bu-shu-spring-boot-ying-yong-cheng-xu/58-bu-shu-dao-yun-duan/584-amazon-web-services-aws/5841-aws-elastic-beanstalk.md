### 58.4.1 AWS Elastic Beanstalk

正如Elastic Beanstalk Java指南中所述，部署Java应用程序有两个主要方式： 您可以使用“Tomcat平台”或“Java SE平台”。

#### 使用 Tomcat平台

此选项适用于生成war文件的Spring Boot项目。 没有任何特殊配置，只需按照官方指南即可。

#### 使用Java SE平台

此种方式适用于生成jar文件并运行嵌入式Web容器的Spring Boot项目。 Elastic Beanstalk环境在端口80上运行一个nginx实例来代理在端口5000上运行的实际应用程序。要配置它，请将以下内容添加到您的application.properties中：

```
server.port=5000
```

#### **最佳实践**

**上传二进制jar而不是源文件**

默认情况下，Elastic Beanstalk上传源码并在AWS中编译它们。 要上传二进制文件，请将以下内容添加到.elasticbeanstalk / config.yml文件中：

```
deploy:
    artifact: target/demo-0.0.1-SNAPSHOT.jar
```

**通过设置环境类型降低系统开销**

默认情况下，Elastic Beanstalk环境是负载均衡的。 负载平衡器有系统资源消耗，为避免这种情况，将环境类型设置为“单例模式”，如Amazon文档中所述。 使用CLI也可以使用以下命令创建单一实例环境：

```
eb create -s
```



