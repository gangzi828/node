#### 10.1.2 Gradle 安装

Spring Boot与Gradle 2（2.9或更高版本）和Gradle 3兼容。如果您尚未安装Gradle，您可以按照www.gradle.org/上的安装说明进行Gradle安装。

可以使用org.springframework.boot group声明Spring引导依赖项。 通常，您的项目将声明一个或多个“Starter”的依赖关系。 Spring Boot提供了一个有用的Gradle插件，可用于简化依赖关系声明和创建可执行jar文件。

> Gradle Wrapper
>
> Gradle Wrapper提供了一种在需要构建项目时“获得”Gradle的好方法。 它是一个小脚本和库，它与代码一起引导构建过程。 有关详细信息，请参阅docs.gradle.org/2.14.1/userguide/gradle\_wrapper.html。

下面是一个典型的build.gradle文件：

```
plugins {
    id 'org.springframework.boot' version '1.5.3.RELEASE'
    id 'java'
}


jar {
    baseName = 'myproject'
    version =  '0.0.1-SNAPSHOT'
}

repositories {
    jcenter()
}

dependencies {
    compile("org.springframework.boot:spring-boot-starter-web")
    testCompile("org.springframework.boot:spring-boot-starter-test")
}
```



