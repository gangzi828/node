## 24.3 应用程序属性文件

SpringApplication将从以下位置的application.properties文件中加载属性，并将它们添加到Spring环境中：

1. 当前目录的/config子目录。
2. 当前目录
3. 一个classpath/config包
4. 类路径根

上述列表是按属性文件优先级排序（在高优先级中定义的属性将覆盖在较低优先级中定义的属性）。



