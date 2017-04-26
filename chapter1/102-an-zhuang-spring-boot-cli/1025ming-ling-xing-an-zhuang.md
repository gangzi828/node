#### 10.2.5 命令行安装

Spring Boot CLI为BASH和zsh shell脚本提供了命令自动补全功能。你可以在任何shell中source脚本（名称也是spring），或将它放到用户或系统范围内的bash初始化脚本里。在Debian系统中，系统级的脚本位于`/shell-completion/bash`下，当新的shell启动时该目录下的所有脚本都会被执行。如果你已经安装了SDKMAN，可以使用以下命令手动运行脚本：

```
$ . ~/.sdkman/candidates/springboot/current/shell-completion/bash/spring
$ spring <HIT TAB HERE>

  grab  help  jar  run  test  version
```

**注**：如果你使用Homebrew或MacPorts安装Spring Boot CLI，命令行实现脚本会自动注册到你的shell。

