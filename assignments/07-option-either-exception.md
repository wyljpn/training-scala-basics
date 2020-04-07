## この課題で身につく能力

Option、Either、Exceptionを使ってエラー表現できる

## 課題

以下の課題の結果をこのファイルに貼り付けて、Pull Requestを送る形で提出してください

1. 「実践Scala入門」第2章p.81 throw式、の`RuntimeException`を投げるコードを実行して結果を貼り付けて下さい。
  - 1.1 REPLから実行して下さい
  
  ![image](https://user-images.githubusercontent.com/37242439/78625161-48e44a80-78c6-11ea-9ea6-7b85a448fa13.png)

  - 1.2 IDEでプロジェクトをセットアップし、ターミナル/コンソールからプロジェクトディレクトリに移動し、sbtから実行して下さい
```scala
package kadai07

object Main {
  def main(args: Array[String]): Unit ={
    throw new RuntimeException("実行時例外！")
  }
}
```
```
yulong.wang@MV-LT-015noMacBook-Pro kadai % cd src/main/scala/kadai07 
yulong.wang@MV-LT-015noMacBook-Pro kadai07 % sbt
[info] Updated file /Users/yulong.wang/Documents/GitHub/kadai/src/main/scala/kadai07/project/build.properties: set sbt.version to 1.3.8
[info] Loading global plugins from /Users/yulong.wang/.sbt/1.0/plugins
[info] Loading project definition from /Users/yulong.wang/Documents/GitHub/kadai/src/main/scala/kadai07/project
[info] Set current project to kadai07 (in build file:/Users/yulong.wang/Documents/GitHub/kadai/src/main/scala/kadai07/)
[info] sbt server started at local:///Users/yulong.wang/.sbt/1.0/server/19f740084034ccedd6a2/sock

sbt:kadai07> run
[info] running kadai07.Main 
[error] (run-main-0) java.lang.RuntimeException: 実行時例外！
[error] java.lang.RuntimeException: 実行時例外！
[error]         at kadai07.Main$.main(Main.scala:5)
[error]         at kadai07.Main.main(Main.scala)
[error]         at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
[error]         at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
[error]         at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
[error]         at java.base/java.lang.reflect.Method.invoke(Method.java:567)
[error] stack trace is suppressed; run last Compile / bgRun for the full output
[error] Nonzero exit code: 1
[error] (Compile / run) Nonzero exit code: 1
[error] Total time: 1 s, completed 2020/04/07 11:58:50

```

2. 「実践Scala入門」第2章 p.81 try式のコード例ひとつめを実行して結果を貼り付けて下さい。
  - 「以下のようなコードで、例外を補足できます。(RuntimeExceptionを投げるのはあまりよいことではありませんが)」の直後、
  - 「より一般的には次のような構文になります」の直前です
  
  ![image](https://user-images.githubusercontent.com/37242439/78625785-ef7d1b00-78c7-11ea-935c-e5f95918f70c.png)

3. 「実践Scala入門」第2章 p.80 例外機構のJavaコード例、`public class UsingException`をIDE上でScalaに直し、ターミナル/コンソールから実行して下さい。
  - sbtでMain関数に引数を渡すには`sbt run 1`や`sbt run 0`のようにしてください
  - Javaの`public static`はScalaの`object`(コンパニオンオブジェクト)を使えば同等の使い方が出来ます
  - Javaの`Integer.parseInt(args[0])`の代わりにScalaの`args(0).toInt`を使ってください
```scala
package kadai07

object UsingException {
  // 引数のtypeをFloatに変更した方が正しい。
  // Intなら、残りがあったら、小数がtrimされてしまう。例えば、　4/5=0。
  def divide(m: Float, n: Float): Float = {
    if (n == 0) throw new Exception("0除算エラー")
    else m / n
  }

  def main(args: Array[String]): Unit ={
    // toInt、toFloat両方OK
    val n = args(0).toInt
    try {
      // nはInt typeなら、自動的にFloatに変更する
      println(divide(10, n))
    } catch {
      case e: Exception => println(e.getMessage)
    }
  }
}

```

```
sbt:kadai07> run 1
[info] Compiling 1 Scala source to /Users/yulong.wang/Documents/GitHub/kadai/src/main/scala/kadai07/target/scala-2.12/classes ...
[info] running kadai07.UsingException 1
10.0
[success] Total time: 5 s, completed 2020/04/07 12:33:16

sbt:kadai07> run 0
[info] running kadai07.UsingException 0
0除算エラー
[success] Total time: 2 s, completed 2020/04/07 12:33:26

sbt:kadai07> run 15
[info] running kadai07.UsingException 15
0.6666667
[success] Total time: 1 s, completed 2020/04/07 12:33:37
```

4. 「実践Scala入門」第3章 p.103のコード例3つを全てREPLから実行して結果を貼り付けて下さい 

![image](https://user-images.githubusercontent.com/37242439/78628320-c744ea80-78ce-11ea-8ec6-c31bccebbee3.png)

Q1: Optionを使ったら、如何やってArray[File]のメソッドを呼び出すか？
A1: 
```scala
    // maybeFilesがNoneの場合には、for loopの中のコードが実行されない。
    for (x <- maybeFiles){
      println(x.length)
    }

    // or 
    maybeFiles.get.length
```
    
5. 「実践Scala入門」第2章 p.80 例外機構のJavaコード例、`public class UsingException`をIDE上でOptionを使ってScalaに直し、ターミナル/コンソールから実行して下さい。
  - 例外を投げるかわりに`None`を返します
  - `return m/n`を返すかわりに`Some（m／n）`を返します

```scala
package kadai07

object UsingExceptionOption {
  def divide(m: Float, n: Float): Option[Float] = {
    if (n == 0)  None
    else Some(m / n)
  }

  def main(args: Array[String]): Unit ={
    val n = args(0).toInt
    divide(10, n) match {
      case Some(res) => println(res)
      case None => println("divided by 0")
    }
  }
}
```
```
[info] running kadai07.UsingExceptionOption 0
divided by 0
[success] Total time: 1 s, completed 2020/04/07 14:13:29

sbt:kadai07> run 5
[info] running kadai07.UsingExceptionOption 5
2.0
```

6. [Scala 公式APIドキュメント Either](https://www.scala-lang.org/api/2.13.0/scala/util/Either.html)のコード例
より、IDEから以下のコードをもつmainクラス/メソッドを作って実行して下さい。`readLine`に渡すターミナル/コンソールからの入力は`1`, `2`, `abc`, です。結果を貼り付けて下さい。

```scala
import scala.io.StdIn._
val in = readLine("Type Either a string or an Int: ")
val result: Either[String,Int] =
  try Right(in.toInt)
  catch {
    case e: NumberFormatException => Left(in)
  }

result match {
  case Right(x) => s"You passed me the Int: $x, which I will increment. $x + 1 = ${x+1}"
  case Left(x)  => s"You passed me the String: $x"
}
```

```scala
package kadai07

object EitherTest {
  def main(args: Array[String]): Unit = {
    import scala.io.StdIn._
    val in = readLine("Type a String or an Int:")
    val result: Either[String, Int] =
      try{
        Right(in.toInt)
      } catch {
        case e: NumberFormatException => Left(in)
      }

    result match{
      case Right(x) => println("You passed me an Int: $x, which I will increment. $x + 1 = ${x + 1}")
      case Left(x) => println("You passed me a String.")
    }

  }
}
```

```
Type a String or an Int:1
You passed me an Int: 1, which I will increment. 1 + 1 = 2

Type a String or an Int:2
You passed me an Int: 2, which I will increment. 2 + 1 = 3

Type a String or an Int:abc
You passed me a String:abc
```