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



