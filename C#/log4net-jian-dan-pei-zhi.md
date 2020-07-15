# 控制台应用程序、Windows服务项目中log4net的配置

1，在 `configSections` 节点中加入以下配置

```text
<section name="log4net" type="log4net.Config.Log4NetConfigurationSectionHandler, log4net" />
```

2，在 `configSections` 节点后加入以下配置

```text
<log4net>
    <!-- OFF, FATAL, ERROR, WARN, INFO, DEBUG, ALL -->
    <!-- Set root logger level to ERROR and its appenders -->
    <root>
        <level value="ALL" />
        <appender-ref ref="SysAppender" />
    </root>
    <!-- Print only messages of level DEBUG or above in the packages -->
    <logger name="WebLogger">
        <level value="DEBUG" />
    </logger>
    <appender name="SysAppender" type="log4net.Appender.RollingFileAppender,log4net">
        <param name="File" value="Log/" />
        <param name="AppendToFile" value="true" />
        <param name="RollingStyle" value="Date" />
        <param name="DatePattern" value="&quot;Logs_&quot;yyyyMMdd&quot;.txt&quot;" />
        <param name="StaticLogFileName" value="false" />
        <layout type="log4net.Layout.PatternLayout,log4net">
        <param name="ConversionPattern" value="%d [%t] %-5p %c - %m%n" />
        </layout>
    </appender>
</log4net>
```

3，在 `AssemblyInfo.cs` 中加入以下代码，告诉 `log4net` 从配置文件中读取配置

```text
[assembly: log4net.Config.XmlConfigurator(ConfigFileExtension = "config", Watch = true)]
```

