
#A Generic Deep-Learning-Based Approach
for Automated Surface Inspection

##(櫻井メモ)金属表面のキズ・腐食の検査をスマート化できないの？
===

Submitted on 2018/03
by Ruoxu Ren, Terence Hung, and Kay Chen Tan, Fellow, IEEE


https://arxiv.org/abs/1708.06297

論文紹介 by github.com/exoego

---

#どんなもの？

## 背景

* 製造現場のスマート化の時代、人に依存する仕事はたくさん残っている
* 金属表面の検査もその１つ。キズや腐食は自動計測できず、視認検査に依存する。
* カメラ設備は高価。DeepLeaningを使うには、写真データの収集が困難。


## 動機
* 金属キズの検査基準は主観的であいまい。
* 出荷側と受入れ側でよく揉める。担当者が代わると基準が変わる？
* 仕様上は「キズがないこと。」　でもキズは絶対なくならない！

![例](https://image.ibb.co/dd5kM7/scratch01.jpg)

---

## どうやって有効だと検証した？

* ①　画像を分割して入力データに
* ②　畳み込み＋プーリング　→　ImageNet/Decaf 活用（後述）
* ③　出力データを全結合
* ④　異常（異なるパターン）を検知できた箇所がわかるようにヒートマップを生成
* ⑤　しきい値で調整（大津の二値化法など）
* ⑥　最終出力　　


![例](https://image.ibb.co/bTsnZS/scratch02.jpg)

## 技術や手法の肝は？

Decafによる転移学習を製造現場に活用

## →　Decaf（ディーキャフ）って何？
* 転移学習（あらかじめ学習を行ったモデルを別のものに反映させる）の１つとして注目。
* 少ないデータ数でディープラーニングできる。

金属損傷のデータベースサイトから300のサンプルを取得するなど、データ数は非常に少ない。（http://faculty.neu.edu.cn/yunhyan/NEU_surface_defect_database.html）

![DSCイメージ](http://faculty.neu.edu.cn/yunhyan/Webpage%20for%20article/NEU%20surface%20defect%20database/Fig.1.jpg)

---

## 先行研究と比べて何がすごい？

* エラーアノテーションを除去するにあたり、事前に専門家がつけた高品質アノテーションを必要としない。
	* →データセットがまだない領域にも使えるかも？

---

## 議論はある？

（感想）
* 分野固有の手法を使わず、一般的なmax-flowセグメンテーションを使っているのは大丈夫？　逆に一般性があってよい？
* 今回の医療用3次元セグメンテーションタスクでは矩形（RR）アノテーションがロバストという結果が得られたが、一般的な2次元画像のセグメンテーションでも同じ？
    * CTスキャン画像という分野では、内臓の位置や形状はだいたい同じなので、類似画像を検索してアノテーションの重なりを評価できるかもしれないが、一般的には難しいのでは……


---

## 次に読むべき論文は？

アノテーションへのクラウドソーシング活用の先行研究（個人的な興味）

+ Estell´es-Arolas, E., Gonz´alez-Ladr´on-De-Guevara, F., 2012. Towards　an integrated crowdsourcing definition. Journal of Information science　38, 189–200
* Albarqouni, S., Baur, C., Achilles, F., Belagiannis, V., Demirci, S., Navab, N., 2016. Aggnet: Deep learning from crowds for mitosis detection in breast cancer histology images. IEEE transactions on medical imaging 35, 1313–1321.

