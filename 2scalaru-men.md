### 1.val vs var

- val: 值
    - final
    - val 值名称:类型 = xxx

- var: 变量
    - 可变
    - var 值名称:类型 = xxx
    
    
### 2.Scala 基本数据类型

- Byte/Char
- Short/Int/Long/Float/Double
- Boolean

类型转换基本操作
```scala
scala> var d = 1.1
d: Double = 1.1

scala> var e:Float = 1.1
<console>:11: error: type mismatch;
 found   : Double(1.1)
 required: Float
       var e:Float = 1.1
                     ^
scala> var e:Float = 1.1f
e: Float = 1.1

scala> val f = 10
f: Int = 10

scala> val g = 10.asInstanceOf[Double]
g: Double = 10.0

scala> val h = 10.isInstanceOf[Int]
h: Boolean = true

```

### 3.Lazy在Scala中的使用
- 定义的时候不会执行，只有在第一次使用的时候才会执行
- 耗费计算资源或者网络的时候使用比较多（如IO）

```scala
scala> val info = fromFile("/Users/markgao/Desktop/hello.txt").mkString
info: String =
"hello
"

scala> lazy val info = fromFile("/Users/markgao/Desktop/hello.txt").mkString
info: String = <lazy>

scala> info
res10: String =
"hello
"

scala>
```

### 4.Scala 常用IDE

- IDEA:
- Eclipse:
- NetBeans:

### 4.使用IDEA整合Maven构建应用程序

1. 新建项目勾选 Create from archetype 并选择scala-archetype-simple
![image.png](https://upload-images.jianshu.io/upload_images/7220971-658b8640fb489065.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
1. 起项目名一路Next，选择自己安装的Maven地址

