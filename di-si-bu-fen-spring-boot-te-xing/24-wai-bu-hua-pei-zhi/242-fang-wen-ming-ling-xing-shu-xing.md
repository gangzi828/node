## 24.2 访问命令行属性

默认情况下，SpringApplication将任何命令行选项参数（以' -- '开头，例如--server.port = 9000）转换为属性，并将其添加到Spring环境中。 如上所述，命令行属性始终优先于其他属性来源。

如果不希望将命令行属性添加到环境中，可以使用SpringApplication.setAddCommandLineProperties（false）禁用它们。



