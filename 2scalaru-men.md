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
