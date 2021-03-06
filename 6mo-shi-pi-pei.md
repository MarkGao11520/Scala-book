# 6.模式匹配

### 1.最基础的模式匹配

Java: 对一个值进行条件判断，返回针对不同的条件进行不同的处理

Scala:

```
变量 match {
    case value1 =>代码1,
    case value2 =>代码2,
    ...
    case _ => 代码N
}
```

```java
object MatchApp extends App {

  val names = Array("zhangsan","lisi","wangwu")
  val name = names(Random.nextInt(names.length))

  name match {
    case "zhangsan" => println("张三...")
    case "lisi" => println("李四...")
    case _ => println("真的不知道你们在说什么")
  }

}
```

### 2.加条件进行匹配

![](https://upload-images.jianshu.io/upload_images/7220971-19e9d2c8b817f6b0.png?imageMogr2/auto-orient/strip|imageView2/2/w/1240)

### 3.Array模式匹配

```java
  def greeting(array:Array[String])={
    array match{
      case Array("zhangsan") => println("Hi zhangsan")
      case Array(x,y) => println("Hi "+x+" , "+y)
      case Array("zhangsan",_*) => println("Hi zhangsan and other friends")
      case _ => println("Hi everybody")
    }
  }
```

### 4.List模式匹配

![image.png](https://upload-images.jianshu.io/upload_images/7220971-0c07a8217979977e.png?imageMogr2/auto-orient/strip|imageView2/2/w/1240)

### 5.类型匹配

```java
  def matchType(obj:Any)={
    obj match {
      case Int => println("Int")
      case String => println("String")
      case m:Map[_,_] => m.foreach(println)
      case _ => println("other type")
    }
  }
```



### 6.Scala异常处理

![image.png](https://upload-images.jianshu.io/upload_images/7220971-a25b0238e52ddc25.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 7.case class

```scala
  class Person
  case class CTO(name: String,floor:Int) extends Person
  case class Employee(name: String,floor:Int) extends Person
  case class Other(name:String) extends Person

  def caseclassMatch(person: Person)={
    person match{
      case CTO(name,floor) => println("CTO name is "+name+", floor is "+floor)
      case Employee(name,floor) => println("Employee name is "+name+", floor is "+floor)
      case _ => println("other")
    }
  }
```

### 8.Some None模式匹配

```scala
val grades = Map("zhangsan"->"A", "lise"->"B")

  def getGrade(nase:String)={
    val grade = grades.get(name)

    grade match {
      case Some(v) => println("your grade is "+v)
      case None => println("sorry ....")
    }
  }

```

