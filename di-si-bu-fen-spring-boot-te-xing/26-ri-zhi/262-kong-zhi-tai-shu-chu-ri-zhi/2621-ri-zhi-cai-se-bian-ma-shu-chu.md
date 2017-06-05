#### 26.2.1 日志彩色编码输出

如果您的终端支持ANSI，日志将会以彩色编码的形式输出，这将有助于可读性。 您可以将spring.output.ansi.enabled设置为支持的值来覆盖自动检测。

使用％clr转换字配置色彩编码。 在最简单的形式下，转换器将根据日志级别对输出进行着色，例如：

```
%clr(%5p)
```

日志级别映射到颜色如下：

| Level | Color |
| :--- | :--- |
| `FATAL` | Red |
| `ERROR` | Red |
| `WARN` | Yellow |
| `INFO` | Green |
| `DEBUG` | Green |
| `TRACE` | Green |

或者，您可以通过将其提供为转换选项来指定应使用的颜色或样式。 例如，要使文本变黄：

```
%clr(%d{yyyy-MM-dd HH:mm:ss.SSS}){yellow}
```

spring boot支持以下颜色和样式：

* blue
* cyan
* faint
* green
* magenta
* red
* yellow





