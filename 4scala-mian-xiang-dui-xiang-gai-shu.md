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

```java
  // 主构造器,如果不加val/var修饰符则默认是private[this] val 类型
  class Person(val name:String,val age:Int,other:String){ 
    println("Person Constructor enter...")
    val school = "ustc"
    var gender:String = _

    def getOther(): String = other

    def this(name:String,age:Int,other:String,gender:String){
      this(name,age,other) // 附属构造器的第一行必须调用主构造器或者其他构造器
      this.gender = gender
    }
    println("Person Constructor leave...")

  }
```

### 4.继承

```java
  // 子类继承父类，父类的属性在子类构造函数中可以不加val/var声明，子类特有的属性必须要加，否则也会变成private[this] val
  class Student(name:String,age:Int,other:String,val school:String) extends Person(name,age,other){

  }
```

### 5.重写

```java
  class Student(name:String,age:Int,other:String,val school:String) extends Person(name,age,other){

    // 重写必须加override
    override val country: String = "USA"

    // $代表this
    override def toString = s"Student($country, $school)"
  }
```

### 6.抽象类

```java
/**
  * 类的一个或者多个方法没有完整的实现(只有定义，没有实现)
  */
abstract class Person2{
  def speak

  var name:String

  var age:Int
}

/**
  * 普通了继承抽象类要实现未实现的抽象方法和抽象属性
  */
class Student2 extends Person2{
  override def speak: Unit = println("speak")

  override var name: String = _
  override var age: Int = _
}
```

### 7.伴生类和伴生对象

```java
/**
  * 如果有一个class,还有一个与class同名的object
  * 那么就称称这个个object是class的伴生対象, class是object的伴生类，两者相辅相成
  */
class ApplyTest{

}

object ApplyTest{

}
```

### 8.Apply 方法

```java
package com.gwf.scala.course04

object ApplyApp {
  def main(args: Array[String]): Unit = {
    for(i <- 1 to 10){
      ApplyTest.incr
    }

    println("count:"+ApplyTest.count) // 10 说明object本身就是一个单例对象

    println("~~~~~~~~~~~~~")
    val b = ApplyTest() // ==>Object.

    println("~~~~~~~~~~~~~")
    val c = new ApplyTest()
    println(c)
    c() // ==>Class.

    // 类名() ===> Object.apply
    // 对象() ===> Class.apply
  }
}

/**
  * 如果有一个class,还有一个与class同名的object
  * 那么就称称这个个object是class的伴生対象, class是object的伴生类，两者相辅相成
  */
class ApplyTest{
  def apply()= {
    println("Class ApplyTest apply...")
  }
}

object ApplyTest{

  println("Object ApplyTest enter...")

  var count = 0

  def incr = {
    count = count + 1
  }

  // 最佳实践:在0bject的apply方法中去new Class
  def apply()= {
    println("Object ApplyTest apply...")
  }

  println("Object ApplyTest leave...")

}
```

### 9.case class

```java
package com.gwf.scala.course04

// 通常用到模式匹配里
object CaseClassApp {
  def main(args: Array[String]): Unit = {
    println(Dog("wangcai").name)
  }
}

case class Dog(name:String)

```

### 10.Trait

Trait 类似于java的接口，但是可以集成抽象类，并实现其抽象方法。

```
// Triat多集成：XXX extends ATrait with BTrait
class SparkConf(loadDefaults: Boolean) extends Cloneable with Logging with Serializable {

```



