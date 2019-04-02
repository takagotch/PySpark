### pyspark
---
http://spark.apache.org/docs/latest/rdd-programming-guide.html

```py
data = [1, 2, 3, 4, 5]
distData = sc.parallelize(data)

conf = SparkConf().setAppName(appName).setMaster(master)
sc = SparkContext(conf=conf)

distFile = sc.textFile("data.txt")

lines = sc.textFile("data.txt")
lineLengths = line.map(lambda s: len(s))
totalLength = lineLengths.reduce(lambda a, b: a + b)

lineLengths.persist()

if __name__ == "__main__":
  def myFunc(s):
    words = s.split(" ")
    return len(words)
    
  sc = SparkContext(...)
  sc.textFile("file.txt").map(myFunc)

class MyClass(object):
  def func(self, s):
    return s
  def doStuff(self, rdd):
    return rdd.map(self.func)

class MyClass(object):
  def __init__(self):
    self.field = "Hello"
  def doStuff(self, rdd):
    return rdd.map(lambda s: self.field + s)

def doStuff(self, rdd):
  field = self.field
  return rdd.map(lambda s: field + s)

counter = 0
rdd = sc.parallelize(data)

def increment_counter(x):
  global counter
  counter += x
rdd.foreach(increment_counter)

print("Counter value: ", counter)

lines = sc.textFile("data.txt")
pairs = lines.map(lambda s: (s, 1))
counts = pairs.recduceByKey(lambda a, b: a + b)
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


