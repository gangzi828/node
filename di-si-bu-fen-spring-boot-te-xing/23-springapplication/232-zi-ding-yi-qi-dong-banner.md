### 23.2 自定义启动Banner

spring boot应用程序的启动Banner可以通过在的类路径中添加一个banner.txt文件，或者通过banner.location来设置Banner文件的位置来更改启动时打印的Banner。 如果文件中存在特殊的编码，你可以通过banner.charset来设置编码（默认为UTF-8）。 除了文本文件，您还可以将banner.gif，banner.jpg或banner.png图像文件添加到您的类路径中，或者设置一个banner.image.location属性。 图像将被转换成ASCII艺术表现，并打印在任何文字Banner上方。

您可以在banner.txt文件中使用以下任何一个占位符：

**表23.1Banner变量**

| 变量 | 描述 |
| :--- | :--- |
| `${application.version}` | 在MANIFEST.MF中声明的应用程序版本号。 例如，Implementation-Version: 1.0被打印为1.0。 |
| `${application.formatted-version}` | 在MANIFEST.MF中声明的格式化显示的应用程序版本号（用括号括起来并以v替代）。 例如（v1.0）。 |
| `${spring-boot.version}` | 您正在使用的Spring Boot版本。 例如1.5.3.RELEASE。 |
| `${spring-boot.formatted-version}` | 您正在使用的spring boot版本的格式化显示（用括号括起来并以v替代）。 例如（v1.5.3.RELEASE）。 |
| `${Ansi.NAME}`\(or`${AnsiColor.NAME}`,`${AnsiBackground.NAME}`,`${AnsiStyle.NAME}`\) | 其中NAME是ANSI转义码的名称。 有关详细信息，请参阅AnsiPropertySource。 |
| `${application.title}` | 在MANIFEST.MF中声明的应用程序标题。 例如：Implementation-Title：MyAppis打印为MyApp。 |

> 如果要以编程方式生成Banner，则可以使用SpringApplication.setBanner（...）方法。 实现org.springframework.boot.Banner接口，并实现自己的printBanner（）方法。

您还可以使用spring.main.banner-mode属性来决定是否必须在System.out（控制台）上打印横幅，使用配置的记录器（log）或根本不打印（关闭）。

打印的Banner将以名称springBootBanner注册为单例bean。

> YAML格式的配置文件用off代表禁止打印Banner，所以如果要禁用应用程序中的Banner，请确保为off添加引号。
>
> spring：
>
>      main：
>
>          banner-mode：“off”



