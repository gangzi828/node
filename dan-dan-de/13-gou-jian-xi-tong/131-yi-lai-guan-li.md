### 13.1 依赖管理

每个spring boot的发布版本都提供了一个支持的依赖关系列表。在实际应用中，你不需要在你的构建配置文件中提供任何依赖的版本信息，因为Spring Boot会自动管理依赖的版本。当你升级spring Boot版本时，相关的依赖也一起进行升级。

> 注意：必要的时候你也可以自己指定依赖的版本，而不是用Sping Boot推荐的依赖版本。

spring boot依赖关系列表包含了spring的所有组件和精细化的第三方库。该列表可作为标准的BOM依赖清单供Maven或Gradle使用。

> 注意：Spring Boot的每个版本都对应一个Spring框架的基础版本，所以我们强烈建议你不要自己指定Spring Boot所依赖的Spring基础版本。



