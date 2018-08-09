# 7. Scala 函数高级操作

### 1. 字符串高级操作

```scala
  val name = "Gwf"

  println(s"hello $name")

  val str =
    """
      |这是一个多行字符串
      |看到了吗
    """.stripMargin

  println(str)
```

### 2. 匿名函数

```scala
// 直接定义
scala> (x:Int) => x+1
res19: Int => Int = <function1>

// 赋值给变量
scala> val m1 = (x:Int) => x+1
m1: Int => Int = <function1>

scala> m1(10)
res20: Int = 11

// 赋值给函数
scala> def add = (x:Int,y:Int)=>{x+y}
add: (Int, Int) => Int

scala> add(2,3)
res21: Int = 5
```


### 3. currying 函数
