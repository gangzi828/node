#### 10.2.6 spring boot CLI 快速入门

下面是一个相当简单的web应用，你可以用它测试Spring CLI安装是否成功。创建一个名叫`app.groovy`

的文件：

```
@RestController
class ThisWillActuallyRun {
@RequestMapping("/")
    String home() {
        return "Hello World!";
    }
}
```

然后只需在shell中运行以下命令：

```
$ spring run app.groovy
```

> **注**：首次运行该应用将会花费一些时间，因为需要下载依赖，后续运行将会快很多。

使用你最喜欢的浏览器打开[localhost:8080](localhost:8080)，然后就可以看到如下输出：

```
Hello World!
```



