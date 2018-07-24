## 1.函数的定义和使用

函数/方法的定义:

```
def 方法名(参数名:参数类型):返回类型 ={
    // 括号内的叫做方法体
    // 方法体内的最后一行为返回值,不需要return
}
```

![image.png](https://upload-images.jianshu.io/upload_images/7220971-a0b0ba43b1eb94b7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```scala
package com.gwf.course03

object FunctionApp {

  def main(args: Array[String]): Unit = {
      println(add(1,1))
      println(three())
      println(three) // 没有入参的函数，调用时是可以省略的
      sayHello()
      sayHello
  }

  def add(x:Int,y:Int):Int={
    x+y // 最后一行就是返回值，不需要返回
  }

  def three()=1+2  // 可以自动判断返回类型

  def sayHello(): Unit ={ // Unit 代表没有返回值
      println("say hello")
  }
}

```
```
2
3
3
say hello
say hello

Process finished with exit code 0
```

## 2.默认参数
默认参数:在函数定义时，允许指定参数的默认值
$SPARK_HOME/conf/spark-defaults.conf

![image.png](https://upload-images.jianshu.io/upload_images/7220971-66a0352fea770f43.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 3.命名参数
```scala
object FunctionApp {

  def main(args: Array[String]): Unit = {
      println(speed(100,10))
      println(speed(time=10,distance=100)) // 根据参数名进行传参 // 不建议
  }
  
  def speed(distance:Float,time:Float ):Float={
    distance/time
  }
  
}
```


## 4.可变参数
JDK5+ : 提供了可变参数
