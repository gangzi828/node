
---

### 59.1.3 自定义启动脚本

Maven或Gradle插件生成的默认内嵌启动脚本可以通过很多方法自定义，对于大多数开发者，使用默认脚本和一些自定义脚本通常就足够了。如果发现不能自定义需要的东西，你可以使用\`embeddedLaunchScript\`选项生成自己的文件。

**在脚本生成时自定义**

自定义写入jar文件的启动脚本元素是有意义的，例如，为\`init.d\`脚本提供\`description\`，既然知道这会展示到前端，你可能会在生成jar时提供它。

为了自定义写入的元素，你需要为Spring Boot Maven或Gradle插件指定\`embeddedLaunchScriptProperties\`选项。

以下是默认脚本支持的可代替属性：

| 名称 | 描述 |
| :--- | :--- |
| `mode` | 脚本模式，默认为\`auto\` |
| `initInfoProvides` | 'INIT INFO'部分的\`Provides\`，对于Gradle默认为\`spring-boot-application\`，对于Maven默认为\`${project.artifactId}\` |
| `initInfoRequiredStart` | ‘INIT INFO’部分的\`Required-Start\`，默认是`$remote_fs $syslog $network` |
| `initInfoRequiredStop` | INIT INFO 部分的Required-Stop，默认是$remote\_fs $syslog $network |
| `initInfoDefaultStart` | INIT INFO部分的Default-Start，默认是2 3 4 5 |
| `initInfoDefaultStop` | ‘INIT INFO’部分的\``Default-Stop`\`，默认值是 0 1 6 |
| `initInfoShortDescription` | ‘INIT INFO’部分的\`Short-Description\`，对于Gradle默认为\`Spring Boot Application\`，对于Maven默认为\`${project.name}\` |
| `initInfoDescription` | “INIT INFO”部分的\`Description\`，对于Gradle默认为\`Spring Boot Application\`，对于Maven默认为\`${project.description}\`（失败会回退到\`${project.name}\`） |
| `initInfoChkconfig` | INIT INFO部分的chkconfig .默认是`2345 99 01`. |
| `confFolder` | \`CONF\_FOLDER\`的默认值，默认为包含jar的文件夹 |
| `logFolder` | \`LOG\_FOLDER\`的默认值，只对\`init.d\`服务有效 |
| logfileName | LOGFILENAME`的默认名称，只对init.d服务有效` |
| `pidFolder` | \`PID\_FOLDER\`的默认值，只对\`init.d\`服务有效 |
| `pidFilename` | `PID_FOLDER文件夹中的文件默认名称，在init.d服务有效。` |
| `useStartStopDaemon` | 如果\`start-stop-daemon\`命令可用，它会控制该实例，默认为\`true\` |
| `stopWaitTime` | `STOP_WAIT_TIME的默认值。只有在init.d服务时有效`. 默认值是60秒 |

#### 在脚本运行时自定义

对于需要在jar文件生成后自定义的项目，你可以使用环境变量或配置文件。

默认脚本支持以下环境变量：

| Variable | Description |
| :--- | :--- |
| `MODE` | The “mode” of operation. The default depends on the way the jar was built, but will usually be`auto`_\(meaning it tries to guess if it is an init script by checking if it is a symlink in a directory called`init.d`\)_. You can explicitly set it to`service`so that the`stop|start|status|restart`commands work, or to`run`if you just want to run the script in the foreground. |
| `USE_START_STOP_DAEMON` | If the`start-stop-daemon`command, when it’s available, should be used to control the process. Defaults to`true`. |
| `PID_FOLDER` | The root name of the pid folder \(`/var/run`by default\). |
| `LOG_FOLDER` | The name of the folder to put log files in \(`/var/log`by default\). |
| `CONF_FOLDER` | The name of the folder to read .conf files from \(same folder as jar-file by default\). |
| `LOG_FILENAME` | The name of the log file in the`LOG_FOLDER`\(`<appname>.log`by default\). |
| `APP_NAME` | The name of the app. If the jar is run from a symlink the script guesses the app name, but if it is not a symlink, or you want to explicitly set the app name this can be useful. |
| `RUN_ARGS` | The arguments to pass to the program \(the Spring Boot app\). |
| `JAVA_HOME` | The location of the`java`executable is discovered by using the`PATH`by default, but you can set it explicitly if there is an executable file at`$JAVA_HOME/bin/java`. |
| `JAVA_OPTS` | Options that are passed to the JVM when it is launched. |
| `JARFILE` | The explicit location of the jar file, in case the script is being used to launch a jar that it is not actually embedded in. |
| `DEBUG` | if not empty will set the`-x`flag on the shell process, making it easy to see the logic in the script. |
| `STOP_WAIT_TIME` | The time in seconds to wait when stopping the application before forcing a shutdown \(`60`by default\). |

\`PID\_FOLDER\`，\`LOG\_FOLDER\`和\`LOG\_FILENAME\`变量只对\`init.d\`服务有效。对于\`systemd\`等价的自定义方式是使用‘service’脚本。

如果\`JARFILE\`和\`APP\_NAME\`出现异常，上面的设置可以使用一个\`.conf\`文件进行配置。该文件预期是放到跟jar文件临近的地方，并且名字相同，但后缀为\`.conf\`而不是\`.jar\`。例如，一个命名为\`/var/myapp/myapp.jar\`的jar将使用名为\`/var/myapp/myapp.conf\`的配置文件：

**myapp.conf. **

```
JAVA_OPTS=-Xmx1024M
LOG_FOLDER=/custom/log/folder
```



