### 11.1 创建POM文件

我们从创建Maven的`pom.xml开始。`因为`pom.xml`是构建项目的清单。打开你最喜欢的文本编辑器，并添加以下内容：

```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>myproject</artifactId>
    <version>0.0.1-SNAPSHOT</version>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.3.RELEASE</version>
    </parent>

    <!-- Additional lines to be added here... -->

</project>
```

这样一个工作目录就构建就完成了，你可以通过运行`mvn package`测试它（暂时忽略"jar将是空的-没有包含任何内容！"的警告）。

> **注**：此刻，你可以将该项目导入到IDE中（大多数现代的Java IDE都包含对Maven的内建支持）。简单起见，我们将继续使用普通的文本编辑器完成该示例。



