## 24.3 应用程序属性文件

SpringApplication将从以下位置的application.properties文件中加载属性，并将它们添加到Spring环境中：

1. 当前目录的/config子目录。
2. 当前目录
3. 一个classpath/config包
4. 类路径根

上述列表是按属性文件优先级排序（在高优先级中定义的属性将覆盖在较低优先级中定义的属性）。

> 注意：可以使用YAML\(.yml\)文件替代.properties文件

如果您不喜欢application.properties作为配置文件名，可以通过指定一个spring.config.name环境属性来指定配置文件名。 您还可以使用spring.config.location环境属性（目录位置的逗号分隔列表或文件路径）显式引用配置文件的位置。

```
$ java -jar myproject.jar --spring.config.name=myproject
```

或者 

```
$ java -jar myproject.jar --spring.config.location=classpath:/default.properties,classpath:/override.properties
```



