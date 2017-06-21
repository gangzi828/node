#### 27.1.9 错误处理

默认情况下，Spring Boot提供/error映射，以合理的方式处理所有错误，并在servlet容器中注册为“全局”错误页面。 对于机器客户端，它将产生一个JSON响应，其中包含错误，HTTP状态和异常消息的详细信息。 对于浏览器客户端，有一个“whitelabel”错误视图，以HTML格式呈现相同的数据（以自定义它，只需添加一个解析为“错误”的视图）。 要完全替换默认行为，您可以实现ErrorController并注册该类型的bean定义，或者简单地添加一个类型为ErrorAttributes的bean来使用现有机制，但是替换内容。

> BasicErrorController可以用作自定义ErrorController的基类。 如果要添加新内容类型的处理程序（默认情况下是专门处理text / html并为其他内容提供后备,这一点尤其有用）。 要实现自定义错误处理功能，只需扩展BasicErrorController并添加一个带有 @RequestMapping注解和produces属性的公共方法，并创建一个新类型的bean。

你还可以定义一个@ControllerAdvice来为特定控制器和/或异常类型返回JSON格式的文档。

```
@ControllerAdvice(basePackageClasses = FooController.class)
public class FooControllerAdvice extends ResponseEntityExceptionHandler {

    @ExceptionHandler(YourException.class)
    @ResponseBody
    ResponseEntity<?> handleControllerException(HttpServletRequest request, Throwable ex) {
        HttpStatus status = getStatus(request);
        return new ResponseEntity<>(new CustomErrorType(status.value(), ex.getMessage()), status);
    }

    private HttpStatus getStatus(HttpServletRequest request) {
        Integer statusCode = (Integer) request.getAttribute("javax.servlet.error.status_code");
        if (statusCode == null) {
            return HttpStatus.INTERNAL_SERVER_ERROR;
        }
        return HttpStatus.valueOf(statusCode);
    }

}
```

在上面的示例中，如果在与FooController相同的包中定义的控件抛出了YourException，则将使用CustomerErrorType POJO的json表示法而不是ErrorAttributes表示形式。

#### 自定义错误页面

如果要显示给定状态代码的自定义HTML错误页面，请将文件添加到/ error文件夹。 错误页面可以是静态HTML（即添加在任何静态资源文件夹下）或使用模板构建。 该文件的名称应该是确切的状态代码或一个系列掩码。

例如，要将404映射到静态HTML文件，您的文件夹结构将如下所示：

```
src/
 +- main/
     +- java/
     |   + <source code>
     +- resources/
         +- public/
             +- error/
             |   +- 404.html
             +- <other public assets>
```

要使用FreeMarker模板映射所有5xx错误，您的文件夹结构将如下所示：

```
src/
 +- main/
     +- java/
     |   + <source code>
     +- resources/
         +- templates/
             +- error/
             |   +- 5xx.ftl
             +- <other templates>
```



