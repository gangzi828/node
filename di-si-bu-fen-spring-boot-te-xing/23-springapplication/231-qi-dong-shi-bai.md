### 23.1 启动失败

如果您的应用程序启动失败，则spring boot通过注册的FailureAnalyzers来输出错误信息并给出解决该问题的具体操作方法。 例如，如果您在8080端口上启动Web应用程序，并且该端口已在使用中，则应该会看到类似于以下的错误日志信息：

```
***************************
APPLICATION FAILED TO START
***************************

Description:

Embedded servlet container failed to start. Port 8080 was already in use.

Action:

Identify and stop the process that's listening on port 8080 or configure this application to listen on another port.
```

> ![](/assets/import.png)Spring Boot提供了许多FailureAnalyzer实现，并且您也可以自定义FailureAnalyzer。

如果没有失败分析器能够处理异常，您仍然可以通过显示完整的自动配置报告来更好地了解出现的问题。 为此，您需要启用debug属性或启用DEBUG级别日志：

```
org.springframework.boot.autoconfigure.logging.AutoConfigurationReportLoggingInitializer
```

例如，如果使用java -jar运行应用程序，则可以按如下方式启用调试属性：

```
$ java -jar myproject-0.0.1-SNAPSHOT.jar --debug
```



