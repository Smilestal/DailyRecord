mac配置Java环境变量：

安装好jdk之后，就开始配置环境变量了。

首先，在终端输入 sudo vim /etc/profile

如需要密码，就输入密码。

按下i，显示insert，进入输入模式。

（注： 在终端输入  /usr/libexec/java_home  可以得到JAVA_HOME 的路径）

输入如下配置：

JAVA_HOME="/Library/Java/JavaVirtualMachines/jdk1.8.0_131.jdk/Contents/Home"

export JAVA_HOME

CLASS_PATH="$JAVA_HOME/lib"

PATH=".$PATH:$JAVA_HOME/bin"

按ESC，进入保存

输入  :wq!   保存






