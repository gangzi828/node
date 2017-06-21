## 28 Security

如果Spring Security位于类路径上，则默认情况下，Web应用程序将在所有HTTP端点上使用“basic”身份验证。 要向Web应用程序添加方法级安全性，您还可以使用所需的设置添加@EnableGlobalMethodSecurity。 有关更多信息，请参见“[Spring Security Reference](http://docs.spring.io/spring-security/site/docs/4.2.2.RELEASE/reference/htmlsingle/#jc-method)”。

默认的AuthenticationManager有一个用户（'user'用户名和随机密码，该随机密码在应用程序启动时以INFO级别打印）

```
Using default security password: 78fa095d-3f4c-48b1-ad50-e24c31d5cf35
```



