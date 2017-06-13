## 58.3 OpenShift

OpenShift是RedHat公共（和企业）PaaS解决方案。 像Heroku一样，它通过运行由git提交触发的脚本来起作用，因此，只要Java运行时可用，您就可以按照任何您喜欢的方式来编写Spring Boot应用程序的启动（这是您可以要求的标准功能OpenShift）。 为了做到这一点，你可以使用自己的盒子和钩子在你的仓库.openshift / action\_hooks：

基本模式是：

1. 确保Java和您的构建工具远程安装，例如 使用pre\_build钩子（Java和Maven默认情况下安装，Gradle不是）
2. 使用构建钩来构建您的jar（使用Maven或Gradle），例如：

```
#!/bin/bash
cd $OPENSHIFT_REPO_DIR
mvn package -s .openshift/settings.xml -DskipTests=true
```

```
3.添加一个调用java -jar的启动钩子...
```

```
#!/bin/bash
cd $OPENSHIFT_REPO_DIR
nohup java -jar target/*.jar --server.port=${OPENSHIFT_DIY_PORT} --server.address=${OPENSHIFT_DIY_IP} &
```

4.使用停止钩（因为开始应该是干净地返回），例如:

```
#!/bin/bash
source $OPENSHIFT_CARTRIDGE_SDK_BASH
PID=$(ps -ef | grep java.*\.jar | grep -v grep | awk '{ print $2 }')
if [ -z "$PID" ]
then
    client_result "Application is already stopped"
else
    kill $PID
fi
```

从您的application.properties中的平台提供的环境变量嵌入服务绑定，例如:

```
spring.datasource.url: jdbc:mysql://${OPENSHIFT_MYSQL_DB_HOST}:${OPENSHIFT_MYSQL_DB_PORT}/${OPENSHIFT_APP_NAME}
spring.datasource.username: ${OPENSHIFT_MYSQL_DB_USERNAME}
spring.datasource.password: ${OPENSHIFT_MYSQL_DB_PASSWORD
```

在Openshift的网站上有一篇\[running Gradle in Openshift\]\(https://www.openshift.com/blogs/run-gradle-builds-on-openshift\)博客，如果想使用gradle构建运行的应用可以参考它。

