## 23.7 访问应用程序变量

如果想访问传入SpringApplication.run\(…​\)中的变量，只需注入一个org.springframework.boot.ApplicationArguments类型的Bean即可。ApplicationArguments接口提供了原生String\[\]类型变量的功能以及解析选项和非选项参数的功能：

```
import org.springframework.boot.*
import org.springframework.beans.factory.annotation.*
import org.springframework.stereotype.*

@Component
public class MyBean {

    @Autowired
    public MyBean(ApplicationArguments args) {
        boolean debug = args.containsOption("debug");
        List<String> files = args.getNonOptionArgs();
        // if run with "--debug logfile.txt" debug=true, files=["logfile.txt"]
    }

}
```



