### 24.5 属性文件占位符

application.properties中的值在使用时通过现有环境进行过滤，以便您可以引用回先前定义的值（例如，从系统属性）。

```
app.name=MyApp
app.description=${app.name} is a Spring Boot application
```

> 您也可以使用此技术创建现有Spring Boot属性的“简短”变体。 有关详细信息，请参见第72.4节“使用”短命令行参数“how-to”。





