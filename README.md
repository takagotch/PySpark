### pyspark
---
http://spark.apache.org/docs/latest/rdd-programming-guide.html

```py
data = [1, 2, 3, 4, 5]
distData = sc.parallelize(data)

conf = SparkConf().setAppName(appName).setMaster(master)
sc = SparkContext(conf=conf)

distFile = sc.textFile("data.txt")

```

```scala
val accum = sc.longAccumulator("My Accumulator")
sc.parallelize(Array(1, 2, 3, 4)).foreach(x => accum.add(x))
accum.value

class VectorAccumulatorv2 extends AccumulatorV2[Myvector, MyVector] {
  private val myVector: MyVector = MyVector.createZeroVector
  
  def reset(): Unit = {
    myVector.reset()
  }
  
  def add(v: MyVector): Unit = {
    myVector.add(v)
  }
}

val myVectorAcc = new VectorAccumulatorv2
sc.register(myVectorAcc, "MyVectorAcc1")


val accum = sc.logAccumulator
data.map { x => accum.add(x); x }
```

```java
List<Integer> data = Arrays.asList(1, 2, 3, 4, 5):
JavaRDD<Integer> distData = sc.parallelize(data);
```


