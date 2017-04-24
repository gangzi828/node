#### 10.1.1 Maven 安装

Spring Boot兼容Apache Maven 3.2或者3.2以上的版本。 如果您还没有安装Maven，可以参照[maven.apache.org](https://maven.apache.org/)上的说明进行Maven安装。

> 注意：在许多操作系统上，Maven可以通过软件包管理器进行安装。 如果您是Mac OSX 用户，请尝试使用brew install maven来进行Maven安装，如果您是 Ubuntu用户可以通过运行sudo apt-get install maven来进行Maven安装。

Spring boot 使用org.springframework.boot groupId 依赖。 通常，一个spring boot应用的Maven POM文件将从spring-boot-starter-parent项目继承，并声明一个或多个“Starter”的依赖关系。 Spring Boot还提供了一个可选的Maven插件来创建可执行的jar。

下面一个典型的pom.xml文件结构：

```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>myproject</artifactId>
    <version>0.0.1-SNAPSHOT</version>

    <!-- Inherit defaults from Spring Boot -->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.3.RELEASE</version>
    </parent>

    <!-- Add typical dependencies for a web application -->
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>

    <!-- Package as an executable jar -->
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>

```

通常情况下将spring-boot-starter-parent作为spring boot项目的父依赖是推荐做法，但这也可能不适合所有的情况。有时您可能需要从不同的父POM继承，或者您可能不需要spring boot的默认配置，这种情况下， 请参见第13.2.2节“通过设置POM的&lt;scope&gt;import&lt;/scope&gt;来使用不带父POM的Spring Boot”作为替代解决方案。

