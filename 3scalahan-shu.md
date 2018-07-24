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

spark中的应用
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

```scala
package com.gwf.course03

object FunctionApp {

  def main(args: Array[String]): Unit = {
      println(sum(1,2,3,4))
      println(sum(1,2,3))
      println(sum(Array(1,2):_*)) // 将数组传入可变参数的函数
  }



  def sum(numbers:Int*)={
    var result = 0
    for(num <- numbers){
      result += num
    }
    result
  }
}

```
spark-sql 中的应用

![image.png](https://upload-images.jianshu.io/upload_images/7220971-26618e0f415444ee.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 5.条件表达式

```
if(a>0) true else false
```

## 6.循环表达式

```scala
scala> 1 to 10 // 左闭右闭
res11: scala.collection.immutable.Range.Inclusive = Range(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

scala> Range(1,10) // 左闭右开
res12: scala.collection.immutable.Range = Range(1, 2, 3, 4, 5, 6, 7, 8, 9)

scala> 1.to(10)  // 等同于 1 to 10
res13: scala.collection.immutable.Range.Inclusive = Range(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

scala> Range(1,10,2) // 可以选择步长
res14: scala.collection.immutable.Range = Range(1, 3, 5, 7, 9)

scala> Range(1,10,0) // 步长不可以为0，死循环
java.lang.IllegalArgumentException: step cannot be 0.
  at scala.collection.immutable.Range.<init>(Range.scala:86)
  at scala.collection.immutable.Range$.apply(Range.scala:439)
  ... 32 elided

scala>  Range(10,0,-1)  // 可以从大到小来
res16: scala.collection.immutable.Range = Range(10, 9, 8, 7, 6, 5, 4, 3, 2, 1)

scala> 1 until 10 // 左闭右开 底层调用的Range
res17: scala.collection.immutable.Range = Range(1, 2, 3, 4, 5, 6, 7, 8, 9)
```

Range源码

```scala
/** Make a range from `start` until `end` (exclusive) with given step value.
   * @note step != 0
   */
  def apply(start: Int, end: Int, step: Int): Range = new Range(start, end, step)

@SerialVersionUID(7618862778670199309L)
@deprecatedInheritance("The implementation details of Range makes inheriting from it unwise.", "2.11.0")
class Range(val start: Int, val end: Int, val step: Int)
...

  @deprecated("This method will be made private, use `length` instead.", "2.11")
  final val numRangeElements: Int = {
    // 如果step==0则抛异常
    if (step == 0) throw new IllegalArgumentException("step cannot be 0.")
    else if (isEmpty) 0
    else {
      val len = longLength
      if (len > scala.Int.MaxValue) -1
      else len.toInt
    }
  }
  ...
}
```

常用循环

```scala
  for(i<-1 to 10 if i%2==0){  // if作用在前面生成的列表基础上
          println(i)
      }

      val courses = Array("spark sql","spark streaming","storm","scala")

      for(course<-courses){
        println(course)
      }

      //course其实就是courses里面的每个元素
      //==> 就是将左边的couse作用上一个函数，变成另外一个结果
      // println 就是作用到course.上的一个函数
      courses.foreach(course => println(course))

      var (num,sum) = (100, 0)
      while (num>0){
        sum+=num
        num -= 1
      }
      println(num)
```