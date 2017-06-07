### 27.1.2 HttpMessageConverters

Spring MVC使用HttpMessageConverter接口转换HTTP请求和响应。 spring boot 提供了开箱即用的默认值，例如对象可以自动转换为JSON（使用Jackson库）或XML（使用Jackson XML扩展，如果可用，否则使用JAXB）。 字符串默认使用UTF-8进行编码。

如果需要添加或自定义转换器，可以使用Spring Boot的HttpMessageConverters类：



