#### 11.3.1 @RestController注解and @RequestMapping注解

Example类上使用的第一个注解是`@RestController`，这是一个原（stereotype）注解。它为阅读代码的人提供暗示（这是一个支持REST的控制器），对于Spring，该类扮演了一个特殊角色。在本示例中，我们的类是一个web`@Controller`，所以当web请求进来时，Spring会考虑是否使用它来处理。

`@RequestMapping`注解提供路由信息，它告诉Spring任何来自"/"路径的HTTP请求都应该被映射到`home`方法。`@RestController`注解告诉Spring以字符串的形式渲染结果，并直接返回给调用者。

> **注**：`@RestController`和`@RequestMapping`是Spring MVC中的注解（它们不是Spring Boot的特定部分），具体参考Spring文档的[MVC章节](http://mvc.linesh.tw/)。



