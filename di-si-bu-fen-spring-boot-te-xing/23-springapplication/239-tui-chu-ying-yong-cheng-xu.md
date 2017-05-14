## 23.9 退出应用程序

每个SpringApplication都在JVM注册一个关闭的钩子，以确保当应用程序退出时ApplicationContext可以优雅的关闭。所有标准的Spring生命周期回调（：如DisposableBean的界面或@PreDestroy注解）可被使用。

