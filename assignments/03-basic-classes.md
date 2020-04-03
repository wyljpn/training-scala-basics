## この課題で身につく能力

戻り値と引数の型を正しく組み合わせて簡単なクラスを書ける

## 課題

以下の課題の結果をこのファイルに貼り付けて、Pull Requestを送る形で提出してください

1. IDEを使って新しいプロジェクトを作り、その中でMainクラスを定義し、ソースコードとプロジェクト・ディレクトリの階層構造をを貼り付けて提出して下さい

これは何も見なくても書けるくらいになってください。これがすぐに書けないと「IDEで動作確認するの面倒だなー」となって、ソースコードの動作確認をする頻度が減ります。
ある程度複雑なコードはどうしてもIDEから動作確認する必要があるため、そのハードルをすこしでも下げられるよう手を慣らして下さい。

![image](https://user-images.githubusercontent.com/37242439/78221366-32bd3f80-74fe-11ea-8627-4297a1beb7d7.png)

2. 「実践Scala入門」第2章p.54 -> p.55「クラスを定義する」のPointクラスを定義して下さい。(p.55「先回りして例示しておくと…」直後です) 

![image](https://user-images.githubusercontent.com/37242439/78222614-7b75f800-7500-11ea-9f75-c37d19e7d62e.png)

3. 「実践Scala入門」第2章p.54 -> p.55「クラスを定義する」の (p.55「まず、先程あげたPointを定義することについて考えてみましょう…」直後です）を 上記課題1. のMainクラスのmain関数の中で呼び出して、実行結果を貼り付けて下さい

![image](https://user-images.githubusercontent.com/37242439/78222662-8e88c800-7500-11ea-9fa5-5e61d6115bd8.png)
![image](https://user-images.githubusercontent.com/37242439/78222711-a4968880-7500-11ea-9b7d-5c7bc5df6317.png)

4. 3.で定義したPointクラスを参考に、xとy座標のみを持つPoint2Dクラスを定義して、TriangleAreaクラスとそのメソッド`def area: Double`を実装して下さい
  - 4.1 TriangleAreaクラスはPoint2Dを3つフィールドに持つクラスです
  - 4.2 Point2D(1,2),Point2D(3,4),Point2D(0,0)の３頂点をもつ三角形の面積を求めるコードを書いて下さい。答えは面積 = 1です。 https://mathwords.net/x1y2hikux2y1
  - 4.3 Point2D(5,7),Point2D(3,4),Point2D(1,2)の３頂点をもつ三角形の面積を求めるコードを書いて下さい。答えは面積 = 1です。 https://mathwords.net/x1y2hikux2y1
![image](https://user-images.githubusercontent.com/37242439/78225820-c0505d80-7505-11ea-840d-9bc4cf2bcdf3.png)
![image](https://user-images.githubusercontent.com/37242439/78225860-ce05e300-7505-11ea-9ebe-42dfb0cc62b4.png)
![image](https://user-images.githubusercontent.com/37242439/78225927-f1c92900-7505-11ea-9646-a2d723925a4c.png)
![image](https://user-images.githubusercontent.com/37242439/78225955-fc83be00-7505-11ea-9088-bb5d3076cc97.png)
