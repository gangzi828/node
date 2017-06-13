## 58.2 Heroku

Heroku是另一个受欢迎的PaaS平台。 为了自定义Heroku构建，需要提供一个Procfile配置文件，它提供部署应用程序所需的指令。 Heroku为Java应用程序分配一个端口，然后确保到外部URI的路由工作。

您必须将应用程序配置为监听正确的端口。 以下是我们的初始化REST应用程序的Procfile：

```
web: java -Dserver.port=$PORT -jar target/demo-0.0.1-SNAPSHOT.jar
```

Spring Boot通过-D参数来访问Spring Environment实例的属性。 将server.port配置属性提供给嵌入式Tomcat，Jetty或Undertow实例，然后在启动时使用它。 $ PORT环境变量由Heroku PaaS分配给我们。

Heroku默认使用Java 1.8。 只要您的Maven或Gradle构建设置为使用相同的版本（Maven用户可以使用java.version属性），这是很好的。 如果要使用JDK 1.7，请在您的pom.xml和Procfile旁边创建一个名为system.properties的新文件。 在此文件中添加以下内容：

```
java.runtime.version=1.7
```

这应该是你需要的一切。 Heroku部署最常见的工作流程是将代码推送到生产。

```
$ git push heroku master

Initializing repository, done.
Counting objects: 95, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (78/78), done.
Writing objects: 100% (95/95), 8.66 MiB | 606.00 KiB/s, done.
Total 95 (delta 31), reused 0 (delta 0)

-----> Java app detected
-----> Installing OpenJDK 1.8... done
-----> Installing Maven 3.3.1... done
-----> Installing settings.xml... done
-----> Executing: mvn -B -DskipTests=true clean install

       [INFO] Scanning for projects...
       Downloading: http://repo.spring.io/...
       Downloaded: http://repo.spring.io/... (818 B at 1.8 KB/sec)
        ....
       Downloaded: http://s3pository.heroku.com/jvm/... (152 KB at 595.3 KB/sec)
       [INFO] Installing /tmp/build_0c35a5d2-a067-4abc-a232-14b1fb7a8229/target/...
       [INFO] Installing /tmp/build_0c35a5d2-a067-4abc-a232-14b1fb7a8229/pom.xml ...
       [INFO] ------------------------------------------------------------------------
       [INFO] BUILD SUCCESS
       [INFO] ------------------------------------------------------------------------
       [INFO] Total time: 59.358s
       [INFO] Finished at: Fri Mar 07 07:28:25 UTC 2014
       [INFO] Final Memory: 20M/493M
       [INFO] ------------------------------------------------------------------------

-----> Discovering process types
       Procfile declares types -> web

-----> Compressing... done, 70.4MB
-----> Launching... done, v6
       http://agile-sierra-1405.herokuapp.com/ deployed to Heroku

To git@heroku.com:agile-sierra-1405.git
 * [new branch]      master -> master
```



