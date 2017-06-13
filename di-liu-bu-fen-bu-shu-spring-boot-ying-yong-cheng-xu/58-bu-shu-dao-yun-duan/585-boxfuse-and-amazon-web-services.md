## 58.5 Boxfuse和Amazon Web Services

\[Boxfuse\]\([https://boxfuse.com/\)的工作机制是将你的Spring](https://boxfuse.com/%29的工作机制是将你的Spring) Boot可执行jar或war转换进一个最小化的VM镜像，该镜像不需改变就能部署到VirtualBox或AWS。Boxfuse深度集成Spring Boot并使用你的Spring Boot配置文件自动配置端口和健康检查URLs，它将该信息用于产生的镜像及它提供的所有资源（实例，安全分组，可伸缩的负载均衡等）。

一旦创建一个\[Boxfuse account\]\([https://console.boxfuse.com/\)，并将它连接到你的AWS账号，安装最新版Boxfuse客户端，你就能按照以下操作将Spring](https://console.boxfuse.com/%29，并将它连接到你的AWS账号，安装最新版Boxfuse客户端，你就能按照以下操作将Spring) Boot应用部署到AWS（首先要确保应用被Maven或Gradle构建过，比如\`mvn clean package\`）：

```
$ boxfuse run myapp-1.0.jar -env=prod
```

有关更多选项，请参阅boxfuse运行文档。 如果当前目录中存在一个boxfuse.com/docs/commandline/\#configuration \[boxfuse.conf\]文件，boxfuse将使用这个文件。

> 如果你的可执行jar或war包含\[\`application-boxfuse.properties\`\]\(https://boxfuse.com/docs/payloads/springboot.html\#configuration\)文件，Boxfuse默认在启动时会激活一个名为\`boxfuse\`的Spring profile，然后在该profile包含的属性基础上构建自己的配置。





