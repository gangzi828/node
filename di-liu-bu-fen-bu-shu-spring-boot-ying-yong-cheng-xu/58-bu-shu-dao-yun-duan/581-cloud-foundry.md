### 58.1 Cloud Foundry

Cloud Foundry提供默认的buildpacks，如果没有指定其他buildpack，则可以使用默认buildpacks。 Cloud Foundry Java buildpack为Spring应用程序提供了极好的支持，包括Spring Boot。 您可以部署独立的可执行jar应用程序，以及传统的.war包应用程序。

一旦构建了应用程序（使用例如mvn clean package）并安装了cf命令行工具，只需使用cf push命令部署应用程序，将其替换为编译的.jar路径。 在推送应用程序之前，请务必使用您的cf命令行客户端登录。

```
$ cf push acloudyspringtime -p target/demo-0.0.1-SNAPSHOT.jar
```

有关更多选项，请参阅cf push文档。 如果在同一目录中存在Cloud Foundry manifest.yml文件，那么将会被查阅。

> 在这里我们将acloudyspringtime作为您应用程序名，你也可以使用其他任何值作为应用程序名。

此时，cf将开始上传您的应用程序：

```
Uploading acloudyspringtime... OK
Preparing to start acloudyspringtime... OK
-----> Downloaded app package (8.9M)
-----> Java Buildpack source: system
-----> Downloading Open JDK 1.7.0_51 from .../x86_64/openjdk-1.7.0_51.tar.gz (1.8s)
       Expanding Open JDK to .java-buildpack/open_jdk (1.2s)
-----> Downloading Spring Auto Reconfiguration from  0.8.7 .../auto-reconfiguration-0.8.7.jar (0.1s)
-----> Uploading droplet (44M)
Checking status of app 'acloudyspringtime'...
  0 of 1 instances running (1 starting)
  ...
  0 of 1 instances running (1 down)
  ...
  0 of 1 instances running (1 starting)
  ...
  1 of 1 instances running (1 running)

App started
```

恭喜！ 该应用程序现在已经运行了！

然后验证部署的应用程序的状态也很容易：

```
$ cf apps
Getting applications in ...
OK

name                 requested state   instances   memory   disk   urls
...
acloudyspringtime    started           1/1         512M     1G     acloudyspringtime.cfapps.io
...
```



