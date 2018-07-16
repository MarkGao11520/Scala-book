

# 1.初识Scala

## 1.1 Scala概述
![image.png](https://upload-images.jianshu.io/upload_images/7220971-1296759f9467aa18.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


>Scala 是整合了面向对象和函数式边恒的高级编程语言。他的一些静态类型能够帮助我们在一些复制的应用程序里面避免到很多bug，并且他的JVM和JavaScript运行环境可以帮助你构建高性能的系统，并且能够轻松的访问已有的庞大的Java类库。


## 1.2 学习Scala的意义

1. 钱多
2. 做东西：Spark，Kafka，Flink 生态系统
        - 代码优雅
        - 开发速度快
        - 融合到生态圈


## 1.3 Scala安装

#### 1. 安装Java8
#### 2. 下载Scala-2.11.8 https://www.scala-lang.org/download/2.11.8.html
![image.png](https://upload-images.jianshu.io/upload_images/7220971-2e23e75c33c3342c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
#### 3. 解压 tar -zxcf scala-2.11.8.tar.gz
#### 4. 配置环境变量
```shell
export JAVA_HOME="/Library/Java/JavaVirtualMachines/jdk1.8.0_171.jdk/Contents/Home"
export PATH=$JAVA_HOME/bin:$PATH

export SCALA_HOME="/Users/markgao/source/scala-2.11.8"
export PATH=$SCALA_HOME/bin:$PATH
```

#### 5. 验证

```
➜  scala-2.11.8 scala
Welcome to Scala 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_171).
Type in expressions for evaluation. Or try :help.

scala>
```


## 1.3 Scala使用入门

