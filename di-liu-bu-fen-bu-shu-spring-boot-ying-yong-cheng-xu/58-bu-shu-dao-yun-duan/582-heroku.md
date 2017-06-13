## 58.2 Heroku

Heroku是另一个受欢迎的PaaS平台。 为了自定义Heroku构建，需要提供一个Procfile配置文件，它提供部署应用程序所需的指令。 Heroku为Java应用程序分配一个端口，然后确保到外部URI的路由工作。

您必须将应用程序配置为监听正确的端口。 以下是我们的初始化REST应用程序的Procfile：

```
web: java -Dserver.port=$PORT -jar target/demo-0.0.1-SNAPSHOT.jar
```



