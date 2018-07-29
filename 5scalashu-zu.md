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

### 2. 变长数组

```java
scala>   val d = scala.collection.mutable.ArrayBuffer[Int]()  //定义一个变上数组
d: scala.collection.mutable.ArrayBuffer[Int] = ArrayBuffer()

scala>

scala>   d+=1  // 添加元素
res15: d.type = ArrayBuffer(1)

scala>   d+=2
res16: d.type = ArrayBuffer(1, 2)

scala>   d+=(3,4,5)  // 添加多个元素
res17: d.type = ArrayBuffer(1, 2, 3, 4, 5)

scala>   d++=Array(6,7,8,9)  // 添加数组
res18: d.type = ArrayBuffer(1, 2, 3, 4, 5, 6, 7, 8, 9)

scala>   d.insert(0,0)  // 在指定位置添加元素

scala>   d.remove(1)  // 删除指定位置的元素
res20: Int = 1

scala>   d.remove(0,3)  // 从指定位置开始删除多个元素

scala>   d.trimEnd(2)  // 删除最后n个元素

scala>

scala>   for(ele<-d){  // 遍历数组-法1
     |     print(ele+" ")
     |   }
4 5 6 7
scala>

scala>   for(i <- 0 until d.length){ // 遍历数组-法2
     |     print(d(i)+" ")
     |   }
4 5 6 7
scala>

scala>   for(i <- (0 until d.length).reverse){  // 从后往前遍历
     |     print(d(i)+" ")
     |   }
7 6 5 4
scala>
```

### 3. List

```java
scala> Nil // 代表一个空的list
res26: scala.collection.immutable.Nil.type = List()

scala> val l = List(1,2,3,4,5)
l: List[Int] = List(1, 2, 3, 4, 5)

scala> l.head   // 一个list由head和tail组成，head是第一个元素，tail是剩下元素组成的list
res27: Int = 1

scala> l.tail
res28: List[Int] = List(2, 3, 4, 5)

scala> val l2 = 1 :: Nil  // 使用::拼接一个新的list 
l2: List[Int] = List(1)

scala> val l3 = 2 :: l2
l3: List[Int] = List(2, 1)

scala> val l4 = 1 :: 2 :: 3 :: Nil
l4: List[Int] = List(1, 2, 3)

scala>   val l5 = scala.collection.mutable.ListBuffer[Int]()  // 变上的List
l5: scala.collection.mutable.ListBuffer[Int] = ListBuffer()

scala> l5+=2  //操作和之前的变长数组一样
res29: l5.type = ListBuffer(2)

scala> println(l5)
ListBuffer(2)
```

### 4. Set

```
scala> val s = Set(1,2,3,3,4,5)
s: scala.collection.immutable.Set[Int] = Set(5, 1, 2, 3, 4)

scala>   val s1 = scala.collection.mutable.Set[Int]()
s1: scala.collection.mutable.Set[Int] = Set()
```



