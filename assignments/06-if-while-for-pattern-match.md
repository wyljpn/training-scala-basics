## この課題で身につく能力

if/else、パターンマッチを使える

## 課題

以下の課題の結果をこのファイルに貼り付けて、Pull Requestを送る形で提出してください

1. 「実践Scala入門」第2章p.71、「2−7」制御構文のif式の例をREPLで書き写して実行し、結果を貼り付けて下さい

2. 「実践Scala入門」第2章p.72 -> p.74、「2−7」制御構文のwhile式、for式の例をREPLで書き写して実行し、結果を貼り付けて下さい

3. 九九表の出力をforで実現して下さい。↓のような表の出力です。

```
1  2  3  4  5  6  7  8  9
2  4  6  8 10 12 14 16 18
3  6  9 12 15 18 21 24 27
...
...
9 18 27 36 45 54 63 72 81
```

4. コップ本「Scalaスケーラブルプログラミング第3版」の第15章「ケースクラスとパターンマッチ」からリスト15.1と15.2を書き写して、以下を実行して結果を貼り付けて下さい。

```scala
simplifyTop(UnOp("-", Var("x")))
simplifyTop(UnOp("-", UnOp("-", Var("x"))))
simplifyTop(BinOp("+", Number(1), Number(2)))
simplifyTop(BinOp("+", Number(1), Number(0)))
simplifyTop(BinOp("*", Number(7), Number(8)))
simplifyTop(BinOp("*", Number(7), Number(1)))

val e1 = BinOp("*", Number(3), Number(1))
val e2 = BinOp("+", Number(4), Number(0))
simplifyTop(BinOp("*", simplifyTop(e1), simplifyTop(e2)))
```

