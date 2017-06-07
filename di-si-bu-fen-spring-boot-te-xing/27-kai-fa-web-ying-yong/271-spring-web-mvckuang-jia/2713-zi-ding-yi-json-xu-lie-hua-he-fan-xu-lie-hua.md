### 27.1.3 自定义JSON序列化和反序列化

如果您使用Jackson序列化和反序列化JSON数据，则可能需要编写自己的JsonSerializer和JsonDeserializer类。 自定义序列化程序通常通过一个模块注册到Jackson，但是Spring Boot提供了一个备用的@JsonComponent注释，可以更容易地直接注册Spring Bean。

您可以直接在JsonSerializer或JsonDeserializer实现中使用@JsonComponent。 您也可以将它用于包含序serializers/deserializers的类作为内部类。 例如：

```
import java.io.*;
import com.fasterxml.jackson.core.*;
import com.fasterxml.jackson.databind.*;
import org.springframework.boot.jackson.*;

@JsonComponent
public class Example {

    public static class Serializer extends JsonSerializer<SomeObject> {
        // ...
    }

    public static class Deserializer extends JsonDeserializer<SomeObject> {
        // ...
    }

}
```



