#### 59.1.1 安装为init.d服务\(System V\)

如果您配置了Spring Boot的Maven或Gradle插件来生成完全可执行的jar，并且您没有使用自定义的embeddedLaunchScript，那么您的应用程序可以用作init.d服务。 简单地将jar链接到init.d以支持标准的start，stop，restart和status命令。

该脚本支持以下功能：

* 以拥有该jar文件的用户启动服务
* 使用/var/run/&lt;appname&gt;/&lt;appname&gt;.pid跟踪应用程序的PID
* 将控制台日志写入/var/log/&lt;appname&gt;.log

假设你在\`/var/myapp\`目录安装了一个Spring Boot应用，只需要建立符号连接就能将Spring Boot应用安装成\`init.d\`服务：

```
$ sudo ln -s /var/myapp/myapp.jar /etc/init.d/myapp
```

一旦安装成功，你就可以像平常那样启动和停止服务，例如，在一个基于Debian的系统：

```
$ service myapp start
```

> 如果应用启动失败，检查下\`/var/log/&lt;appname&gt;.log\`中的错误日志。

你也可以标识应用使用标准的操作系统工具自启动，例如，在Debian上：

```
$ update-rc.d myapp defaults <priority>
```



