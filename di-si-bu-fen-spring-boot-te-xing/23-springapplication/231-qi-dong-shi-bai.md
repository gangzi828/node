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



