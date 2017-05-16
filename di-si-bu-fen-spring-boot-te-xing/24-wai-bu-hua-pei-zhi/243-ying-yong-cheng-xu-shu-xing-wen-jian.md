## 24.3 应用程序属性文件

SpringApplication将从以下位置的application.properties文件中加载属性，并将它们添加到Spring环境中：

1. 当前目录的/config子目录。
2. 当前目录
3. 一个classpath/config包
4. 类路径根

上述列表是按属性文件优先级排序（在高优先级中定义的属性将覆盖在较低优先级中定义的属性）。

> 注意：可以使用YAML\(.yml\)文件替代.properties文件

如果您不喜欢application.properties作为配置文件名，可以通过指定一个spring.config.name环境属性来指定配置文件名。 您还可以使用spring.config.location环境属性（逗号分隔的目录位置的或文件路径）显式引用配置文件的位置。

```
$ java -jar myproject.jar --spring.config.name=myproject
```

或者

```
$ java -jar myproject.jar --spring.config.location=classpath:/default.properties,classpath:/override.properties
```

> spring.config.name和spring.config.location非常早已被用于确定哪些文件必须被加载，因此必须将它们定义为环境属性（通常是OS env，system属性或命令行参数）。

如果spring.config.location包含目录（而不是文件），那么它们应该以/结尾，（并追加从spring.config.name配置的文件名称）。 在spring.config.location中指定的文件按原样使用，不支持特定于配置文件的变体，并且将被任何特定于配置文件的属性覆盖。

默认的搜索路径classpath：，classpath：/ config，file：，file：config /始终使用，不管spring.config.location的值如何。 该搜索路径从最低优先级排序（文件：config / wins）。 如果您指定自己的位置，则它们优先于所有默认位置，并使用相同的从最低到最高优先级排序。 这样，您可以在application.properties（或使用spring.config.name选择的任何其他基础名称）中为应用程序设置默认值，并在运行时使用不同的文件覆盖它，并保留默认值。



