

```scala
object CribaEratostenes extends App{
  import scala.collection.mutable.Set
  import scala.collection.mutable.BitSet
  //Apartado a
  def primos(n:Int):Set[Int]={
    val p = Set[Int]()
    for (i<- 2 to n) p += i
    for (i <- 2 to n){
      for(j<-2 to n){
        var m = i*j
        if (p.contains(m)) p-=m
      }
    }
    p
  }
  //Apartado d
  def primosBit(n:Int):BitSet={
    val p = BitSet()
    for (i<- 2 to n) p += i
    for (i <- 2 to n){
      for(j<-2 to n){
        var m = i*j
        if (p.contains(m)) p-=m
      }
    }
    p
  }
  //Apartado e
  def raiz(x:Int):Int = math.sqrt(x.toDouble).toInt
  def criba(n:Int):BitSet= {
    val p = BitSet()
    for (i <- 2 to n) p += i
    val k = raiz(n)
    for (i <- 2 to k) {
      if (p.contains(i)) {
        for (j <- 2 to n) {
          var m = i * j
          p-=m
        }
      }
    }
    p
  }
  println("Con Raiz y BitSet:")
  tiemposPara(criba,List.iterate(16000,5)(_*2))
  println()
  println(primos(100))
  println(primosBit(100))
  println(criba(100))
```

