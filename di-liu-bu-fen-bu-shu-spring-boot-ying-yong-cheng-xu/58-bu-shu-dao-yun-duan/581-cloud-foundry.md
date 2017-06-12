### 58.1 Cloud Foundry

Cloud Foundry提供默认的buildpacks，如果没有指定其他buildpack，则可以使用默认buildpacks。 Cloud Foundry Java buildpack为Spring应用程序提供了极好的支持，包括Spring Boot。 您可以部署独立的可执行jar应用程序，以及传统的.war包应用程序。

一旦构建了应用程序（使用例如mvn clean package）并安装了cf命令行工具，只需使用cf push命令部署应用程序，将其替换为编译的.jar路径。 在推送应用程序之前，请务必使用您的cf命令行客户端登录。

```
$ cf push acloudyspringtime -p target/demo-0.0.1-SNAPSHOT.jar
```



