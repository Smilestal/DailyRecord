Android单元测试覆盖率

1. 在`build.gradle`中打开测试覆盖率开关

```gradle
android{
    ... ...
    buildTypes {
            debug{
                testCoverageEnabled = true
            }
    }
}

```

1. 运行`gradlew connectedAndroidTest`即可