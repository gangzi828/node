### 26.3 文件日志输出

默认情况下，Spring Boot只是将日志输出到控制台，不会写入到日志文件中。 如果需要除控制台输出之外的日志文件，则需要设置logging.file或logging.path属性（例如在application.properties中）。

下表显示了如何一起使用logging.\*属性：

| logging.file | `logging.path` | Example | Description |
| :--- | :--- | :--- | :--- |
| _\(none\)_ | _\(none\)_ |  | 只输出到控制台. |
| Specific file | _\(none\)_ | `my.log` | 写入指定的日志文件。 名称可以是确切的位置或相对于当前目录。 |
| _\(none\)_ | Specific directory | `/var/log` | 将spring.log写入指定的目录。 名称可以是确切的位置或相对于当前目录。 |

日志文件将在10 MB时旋转，默认情况下会记录控制台输出，ERROR，WARN和INFO级别的消息。

> 日志记录系统在应用程序生命周期早期初始化，并且在通过@PropertySource注释加载的属性文件中将不会找到记录属性。

> 日志属性独立于实际的日志底层实现。 因此，特定配置key（如Logback的logback.configurationFile）不受spring boot管理。



