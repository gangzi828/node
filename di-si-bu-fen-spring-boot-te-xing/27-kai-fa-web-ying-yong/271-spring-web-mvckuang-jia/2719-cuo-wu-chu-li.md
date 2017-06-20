#### 27.1.9 错误处理

默认情况下，Spring Boot提供/error映射，以合理的方式处理所有错误，并在servlet容器中注册为“全局”错误页面。 对于机器客户端，它将产生一个JSON响应，其中包含错误，HTTP状态和异常消息的详细信息。 对于浏览器客户端，有一个“whitelabel”错误视图，以HTML格式呈现相同的数据（以自定义它，只需添加一个解析为“错误”的视图）。 要完全替换默认行为，您可以实现ErrorController并注册该类型的bean定义，或者简单地添加一个类型为ErrorAttributes的bean来使用现有机制，但是替换内容。

> BasicErrorController可以用作自定义ErrorController的基类。 如果要添加新内容类型的处理程序（默认情况下是专门处理text / html并为其他内容提供后备），这一点尤其有用。 要做到这一点，只需扩展BasicErrorController并添加一个带有@属性的@RequestMapping的公共方法，并创建一个新类型的bean。



