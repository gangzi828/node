## 23.10 Admin特性

在spring boot中可以通过设置spring.application.admin.enabled属性来开启Admin相关的特性。这通过MBeanServer平台暴露出一个

[SpringApplicationAdminMXBean](https://github.com/spring-projects/spring-boot/tree/v1.5.3.RELEASE/spring-boot/src/main/java/org/springframework/boot/admin/SpringApplicationAdminMXBean.java)来实现。

* 可以通过设置local.server.port来查看应用程序运行在哪个HTTP端口。
* 注意当启用Admin特性时，在MBean中暴露了关闭应用程序的方法。





