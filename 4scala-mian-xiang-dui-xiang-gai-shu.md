# 4. Scala面向对象

### 1.面向对象概述

* 封装：属性方法封装到类中

* 继承：父类和子类直接的关系

* 多态：\*\*\*\*\* 父类引用指向子类对象 精髓所在，开发框架的基石

### 2.类的定义和使用

```java
package com.gwf.scala.course04

object SimpleObjectApp {

  def main(args: Array[String]): Unit = {

    val person = new People()
    person.name = "Messi"
    println(person.name+" "+person.age)
    println("invoke eat method "+person.eat)
    person.watchFootball("Barcelona")
    person.printInfo()
  }

  class People{
    var name:String = _ //_代表占位符
    val age = 10

    // 私有变量，外部不能访问，[]里的this代表访问权限，可以填当前所在包，则包内可以访问
    private [this] var gender:String = "male" 

    def printInfo(): Unit ={
      println(gender)
    }

    def eat():String={
      name + "eat ....."
    }

    def watchFootball(teamName: String)={
      println(name+"is watching match of "+teamName)
    }

  }
}

```

```
scala> var d:Double = _
d: Double = 0.0

scala> val i:Int = _
<console>:11: error: unbound placeholder parameter
       val i:Int = _
                   ^

scala> var i:Int = _
i: Int = 0

scala> var s:String = _
s: String = null

scala>
```



### 3.主构造器和附属构造器





