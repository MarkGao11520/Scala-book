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
- 

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

```

