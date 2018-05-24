### Android静态分析

#### lint命令
运行如下命令行即可使用lint对工程进行静态分析
```gradle
gradlew lint -w //-w标识日志级别调至warn
```

运行lint命令后，会在`../app/build/reports/lint-results.html`目录下生成运行结果，如需忽略lint对某些问题的检查，可在build.gradle中添加如下代码，并根据需要对disable中的参数进行修改

```gradle
android {
    ...
    lintOptions {
        disable 'AllowBackup','UnusedResources','GoogleAppIndexingWarning'
        abortOnError false
    }
}
```