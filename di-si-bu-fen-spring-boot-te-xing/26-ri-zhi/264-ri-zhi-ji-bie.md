### 26.4 日志级别

所有支持的日志记录系统都可以在Spring环境中设置记录级别（例如在application.properties中），使用'logging.level.\* = LEVEL'，其中'LEVEL'是TRACE，DEBUG，INFO，WARN，ERROR，FATAL, OFF之一 。 可以使用logging.level.root配置根记录器。 示例application.properties：

```
logging.level.root=WARN
logging.level.org.springframework.web=DEBUG
logging.level.org.hibernate=ERROR
```



