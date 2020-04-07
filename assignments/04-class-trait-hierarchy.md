## この課題で身につく能力

(クラス図を渡されれば)traitおよびclassをextendsして簡単なクラスを作れる

## 課題

以下の課題の結果をこのファイルに貼り付けて、Pull Requestを送る形で提出してください

1. 「実践Scala入門」第2章p.59 -> p.60、「クラスの継承」にあるShape, Triangle, Rectangle, UnknownShapeの定義およびそれらの`def shape`メソッドを呼び出すコードを書いて呼び出し結果を貼り付けて下さい

```scala
abstract class Shape {
  def draw(): Unit = {
    println("不明な図形")
  }
}

class Triangle extends Shape{
  override def draw(): Unit = {
    println("三角形")
  }
}

class Rectangle extends Shape{
  override def draw(): Unit = {
    println("四角形")
  }
}

class UnknownShape extends Shape
```

![image](https://user-images.githubusercontent.com/37242439/78322000-766c8380-75a8-11ea-8fff-070dae9c21cc.png)


2. 上記1. Shapeのインスタンスを直接newしてコンパイルエラーが発生するのを確認して下さい

![image](https://user-images.githubusercontent.com/37242439/78322053-9dc35080-75a8-11ea-8772-c222e23c4d02.png)

3. 上記1. Shapeの定義を以下のように書き換え、Shapeのインスタンスを直接newして、コンパイルエラーが消えるのを確認して下さい

```scala
class Shape {
  def draw(): Unit = {
    println(" 不明 な 図形")
  }
}
```

shapeをnewして、drawメソットを実行する
```scala
    shape = new Shape
    shape.draw()
```

![image](https://user-images.githubusercontent.com/37242439/78343713-36bc9080-75d6-11ea-8a25-22ddf3feec74.png)

4. 以下のクラス図をもとにtraitとclassを定義してください。それぞれのクラスでのrunメソッドは以下の文字列をprintlnで出力するよう実装し、クラスの定義と実装結果を貼り付けて提出してください。

<img width=400 src="https://user-images.githubusercontent.com/7414320/76874598-bf3af180-68b2-11ea-8659-b076dd4f29d0.jpg" />

```scala
class Cat:           // "I can run at 48km/h" 
class Cheetah:       // "I run at 93km/h, you can't see me" 
class Human:         // "20 km/h isn't so bad actually" 
class OlympicAthlete // "40 km/h at maximum" 
```

トレイトとクラスの定義

```scala

trait Namable{
  val name: String
  def display(): Unit = println(name)
}

trait Animal extends Namable {
  def run(): Unit
}

class Cat extends Animal{
  override def run(): Unit = {
    println("I can run at 48km/h")
  }
  override val name: String = "Cat"
}

class Cheetah extends Cat{
  override def run(): Unit = {
    println("I run at 93km/h, you can't see me" )
  }
  override val name: String = "Cheetah"
}

class Human extends Animal with Namable {
  override def run(): Unit = {
    println("20 km/h isn't so bad actually")
  }
  override val name: String = "Human"
}

class OlympicAthlete extends Human with Namable {
  override def run(): Unit = {
    println("40 km/h at maximum" )
  }
  override val name: String = "Human"
}

```

実装するコード

```scala
    var animal: Animal = new Cat
    animal.display()
    animal.run()

    animal = new Cheetah
    animal.display()
    animal.run()

    animal = new Human
    animal.display()
    animal.run()

    animal = new OlympicAthlete
    animal.display()
    animal.run()
```

実行する結果

![image](https://user-images.githubusercontent.com/37242439/78326214-ca7d6500-75b4-11ea-9bdf-3f2e7511fe20.png)
