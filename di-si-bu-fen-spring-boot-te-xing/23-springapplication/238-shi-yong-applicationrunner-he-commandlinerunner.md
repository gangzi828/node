## 23.8 使用ApplicationRunner和CommandLineRunner

如果某些代码需要在SpringApplication启动时只执行一次，这可以通过实现ApplicationRunner和CommandLineRunner接口来实现。这两个接口的工作方式基本相同，都只包含一个run方法，并且在SpringApplication.run\(…​\)方法执行之前执行。

CommandLineRunner接口以String数组的形式来访问应用程序变量，而ApplicationRunner通过ApplicationArguments接口来访问应用程序变量。

```
import org.springframework.boot.*
import org.springframework.stereotype.*

@Component
public class MyBean implements CommandLineRunner {

    public void run(String... args) {
        // Do something...
    }

}
```

当程序中有多个CommandLineRunner和ApplicationRunner的Bean的时候，可以通过实现org.springframework.core.Ordered接口活着通过org.springframework.core.annotation.Order这个注解来确定执行的顺序。

