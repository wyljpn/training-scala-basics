## この課題で身につく能力

companion objectとcase classを使える

## 課題

以下の課題の結果をこのファイルに貼り付けて、Pull Requestを送る形で提出してください

1. 「実践Scala入門」第2章p.67 -> p.69、「2-６ケースクラス」のclass Pointとobject Pointの定義をするコードを書いて下さい

```scala
class Point(val x: Int, val y: Int) {

  override def hashCode(): Int = x + y

  override def equals(that: Any): Boolean = that match {
    case that: Point => x == that.x && y ==that.y
    case _ => false
  }

  override def toString: String = "Point(" + x + "," + "y" + ")"
}

object Point{
  def apply(x: Int, y: Int): Point = new Point(x, y)
}
```
2. 上記1.で定義したPointをもとに、「2-2クラスを定義する」にあるPointを呼び出すコード（まず、先程あげたPointを定義することについて考えましょう…の直後です）を再び書いて出力を確認して貼り付けて下さい。`new` が消えることに気づくはずです。

```scala
    // newがない場合は、IntelliJでPointをクリックすると、object Pointを使用していることが分かりました。
    val p1: Point = Point(10, 10)
    val p2: Point = Point(100, 100)
    println(math.abs(p1.x - p2.x))

    // newがある場合は、IntelliJでPointをクリックすると、結果が同じですが、class Pointを使用することが分かりました。
    val p3: Point = new Point(10, 10)
    val p4: Point = new Point(100, 100)
    println(math.abs(p3.x - p4.x))

    // 疑問：
    //　newがあるか、ないか、何の影響を与える？

```

3. 上記1.のPointの定義を、「2-６ケースクラス」の`case class`で置き換えて下さい、10行近いコードが1行になります。

```scala
    case class CasePoint(x: Int, y: Int)
```

```scala
    // case classを使ったら、自動的にcompanion objectが生成されて、
    // newを使わなくてもobjectが生成できるようだ。
    val p5: CasePoint = CasePoint(10, 10)
    val p6: CasePoint = CasePoint(100, 100)
    println(math.abs(p5.x-p6.x))

    // case classの場合にもnewを書いても結果は同じです。しかし、newが灰色になってしまった。なの原因？
    // こちらはcompanion objectを使うか、CasePoint classを使うか？不明
    val p7: CasePoint = new CasePoint(10, 10)
    val p8: CasePoint = new CasePoint(100, 100)
    println(math.abs(p7.x-p8.x))
```

4. 次のコードの出力結果を確認して下さい

```scala
val p1 = Point(1,2)
val p2 = p1.copy(x = 10)
println(p1)
println(p2)
```
output:

CasePoint(1,2)

CasePoint(10,2)
