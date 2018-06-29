
[runner注册文档](https://docs.gitlab.com/runner/register/index.html)

**注意：**
注册第五步需要选择true

```
Whether to run untagged jobs [true/false]:
[false]: true
```

如果运行`gitlab-runner start`后连不上，可以运行`gitlab-runner run`

runner相关命令：<br>
https://docs.gitlab.com/runner/commands/README.html

**相同类型的工程可以考虑共用runner**

步骤如下：
1. 注册runner时，是否绑定runner在当前工程，选择false。如下：
```
Whether to lock the Runner to current project [true/false]:
[true]: false
```

2. 使用root账号，进入需要共用runner的工程，进入Settings -> CI/CD -> Runners settings展开设置项, 点击`Enable for this project`按钮，即可将此runner运用于此工程。