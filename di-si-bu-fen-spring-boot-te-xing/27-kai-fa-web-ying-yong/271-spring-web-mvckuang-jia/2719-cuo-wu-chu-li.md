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

对于更复杂的错误映射，您还可以添加实现ErrorViewResolver接口的bean。

```
public class MyErrorViewResolver implements ErrorViewResolver {

    @Override
    public ModelAndView resolveErrorView(HttpServletRequest request,
            HttpStatus status, Map<String, Object> model) {
        // Use the request or status to optionally return a ModelAndView
        return ...
    }

}
```

您还可以使用常规Spring MVC功能，如@ExceptionHandler方法和@ControllerAdvice。 然后，ErrorController将接收任何未处理的异常。

#### 非Spring MVC程序的错误映射

对于不使用Spring MVC的应用程序，可以使用ErrorPageRegistrar接口直接注册ErrorPages。 这个抽象直接与底层的嵌入式servlet容器一起工作，即使没有Spring MVC DispatcherServlet也可以工作。

```
@Bean
public ErrorPageRegistrar errorPageRegistrar(){
    return new MyErrorPageRegistrar();
}

// ...

private static class MyErrorPageRegistrar implements ErrorPageRegistrar {

    @Override
    public void registerErrorPages(ErrorPageRegistry registry) {
        registry.addErrorPages(new ErrorPage(HttpStatus.BAD_REQUEST, "/400"));
    }

}
```

注： 如果您注册一个最终由Filter过滤的路径的ErrorPage（例如，与某些非Spring Web框架（例如Jersey和Wicket）相同），则必须将Filter显式注册为ERROR调度程序。

```
@Bean
public FilterRegistrationBean myFilter() {
    FilterRegistrationBean registration = new FilterRegistrationBean();
    registration.setFilter(new MyFilter());
    ...
    registration.setDispatcherTypes(EnumSet.allOf(DispatcherType.class));
    return registration;
}
```

（默认的FilterRegistrationBean不包括ERROR调度程序类型）。

#### WebSphere服务器的错误处理

当部署到servlet容器时，Spring Boot使用其错误页面过滤器将具有错误状态的请求转发到相应的错误页面。 如果响应尚未提交，则该请求只能转发到正确的错误页面。 默认情况下，WebSphere Application Server 8.0和更高版本在成功完成servlet的服务方法后提交响应。 您应该通过将com.ibm.ws.webcontainer.invokeFlushAfterService设置为false来禁用此行为。





