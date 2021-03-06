### 59.1.2 安装为Systemd服务

Systemd是System V init系统的继任者，很多现代Linux分发版本都在使用，尽管你可以继续使用\`init.d\`脚本，但使用\`systemd\` ‘service’脚本启动Spring Boot应用是有可能的。

假设你在\`/var/myapp\`目录下安装一个Spring Boot应用，为了将它安装为一个\`systemd\`服务，你需要按照以下示例创建一个脚本，比如命名为\`myapp.service\`，然后将它放到\`/etc/systemd/system\`目录下：

```
[Unit]
Description=myapp
After=syslog.target

[Service]
User=myapp
ExecStart=/var/myapp/myapp.jar
SuccessExitStatus=143

[Install]
WantedBy=multi-user.target
```

> 记得根据你的应用改变\`Description\`，\`User\`和\`ExecStart\`字段。
>
> 请注意，ExecStart字段不声明脚本操作命令，这意味着默认情况下使用run命令。

注意跟作为\`init.d\`服务运行不同，使用\`systemd\`这种方式运行应用，PID文件和控制台日志文件表现是不同的，必须在‘service’脚本配置正确的字段，具体参考\[service unit configuration man page\]\(http://www.freedesktop.org/software/systemd/man/systemd.service.html\)。

```
$ systemctl enable myapp.service
```

有关详细信息，请参阅man systemctl。

