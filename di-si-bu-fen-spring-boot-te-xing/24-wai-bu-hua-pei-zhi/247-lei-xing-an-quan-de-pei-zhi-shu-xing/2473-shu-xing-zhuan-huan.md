#### 24.7.3 属性转换

当Spring绑定到@ConfigurationProperties bean时，Spring将尝试将外部应用程序属性强制转换为正确的类型。 如果需要自定义类型转换，您可以提供ConversionService bean（使用bean id conversionService）或自定义属性编辑器（通过CustomEditorConfigurer bean）或自定义转换器（使用注释为@ConfigurationPropertiesBinding的bean定义）。

> 由于在应用程序生命周期期间非常早请求此Bean，请确保限制ConversionService正在使用的依赖关系。 通常，您需要的任何依赖关系可能无法在创建时完全初始化。 如果配置密钥强制不需要，只需依赖使用@ConfigurationPropertiesBinding限定的自定义转换器，就可以重命名自定义ConversionService。





