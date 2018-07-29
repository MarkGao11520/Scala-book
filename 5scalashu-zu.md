# 5. Scala数组

### 1. 定长数组

```
scala> val a = new Array[String](5)
a: Array[String] = Array(null, null, null, null, null)

scala> val b = Array("a","b","c")
b: Array[String] = Array(a, b, c)

scala> b.length
res0: Int = 3

scala> val b = Array(1,2,3)
b: Array[Int] = Array(1, 2, 3)

scala> b.sum
res2: Int = 6

scala> b.max
res3: Int = 3

scala> b.min
res4: Int = 1

scala> b.mkString(",")
res5: String = 1,2,3

scala> b.mkString("[",",","]")
res6: String = [1,2,3]

scala>
```

Array\(\) 的源码

```java
  /** Creates an array with given elements.
   *
   *  @param xs the elements to put in the array
   *  @return an array containing all elements from xs.
   */
  // Subject to a compiler optimization in Cleanup.
  // Array(e0, ..., en) is translated to { val a = new Array(3); a(i) = ei; a }
  def apply[T: ClassTag](xs: T*): Array[T] = {
    val array = new Array[T](xs.length)
    var i = 0
    for (x <- xs.iterator) { array(i) = x; i += 1 }
    array
  }
```



