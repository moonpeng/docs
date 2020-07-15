# CentOS java运行时安装

## 查看yum库中都有哪些jdk版本

```text
# yum search java|grep jdk
```

## 选择版本，进行安装

```text
# yum install java-1.8.0-openjdk.x86_64
```

## 设置环境变量

安装完之后，默认的安装目录是在: `/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.232.b09-0.el7_7.x86_64`

```text
# vim /etc/profile
```

添加如下内容

```text
#SET JAVA environment
JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.232.b09-0.el7_7.x86_64
JRE_HOME=$JAVA_HOME/jre
CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
export JAVA_HOME JRE_HOME CLASS_PATH PATH
```

生效

```text
# source /etc/profile
```

