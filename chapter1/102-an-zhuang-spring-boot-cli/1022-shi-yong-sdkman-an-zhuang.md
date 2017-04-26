#### 10.2.2 使用SDKMAN安装

SDKMAN!（软件开发套件管理器）可用于管理各种二进制SDK的多个版本，包括Groovy和Spring Boot CLI。从sdkman.io获取SDKMAN！并通过下面指令安装Spring Boot：

`$ sdk install springboot`

`$ spring --version`

`Spring Boot v1.5.3.RELEASE`

如果您正在开发CLI的功能，并希望轻松访问刚创建的版本，请遵循以下额外说明。

```
$ sdk install springboot dev /path/to/spring-boot/spring-boot-cli/target/spring-boot-cli-1.5.3.RELEASE-bin/spring-1.5.3.RELEASE/
```

```
$ sdk default springboot dev
$ spring --version
Spring CLI v1.5.3.RELEASE
```

这将安装一个称为dev的spring的本地实例， 它指向您的目标构建位置，所以每次重建Spring Boot时，Starter将是最新的。

你可以看到它：

```
$ sdk ls springboot
```

```

================================================================================
Available Springboot Versions
================================================================================

>
 + dev
* 1.5.3.RELEASE

================================================================================
+ - local version
* - installed

>
 - currently in use
================================================================================
```



