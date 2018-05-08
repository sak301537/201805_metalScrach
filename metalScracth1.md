

#A Generic Deep-Learning-Based Approach
for Automated Surface Inspection

##金属表面のキズ・腐食検査をスマート化できないの？~SORAサクライ　櫻井　敏明
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

![例](https://image.ibb.co/dd5kM7/scratch01.jpg)


## 動機
* どのような製品も仕様上は「キズがないこと。」　でも金属材料のキズは絶対なくならない！
* キズや腐食は視認検査。検査基準は主観的であいまい。
* 出荷側と受入れ側でよく揉める。担当者が代わると基準が変わってまた揉める。

![例](http://cdn-ak.f.st-hatena.com/images/fotolife/d/dobonkai/20130430/20130430040517.jpg)


---

## どうやって有効だと検証した？

金属損傷のデータベースサイトから300のサンプルを取得するなど、データ数は非常に少ない。
<img src="http://faculty.neu.edu.cn/yunhyan/Webpage%20for%20article/NEU%20surface%20defect%20database/Fig.1.jpg" width="400" height="400" />


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
* 画像認識技術SURFより優れる、など評価が高い 　(以下は画像クラスタリングの精度比較)

![例](https://image.ibb.co/eMdEYn/scratch03.jpg)




//![DSCイメージ](http://faculty.neu.edu.cn/yunhyan/Webpage%20for%20article/NEU%20surface%20defect%20database/Fig.1.jpg　=)

---

## 先行研究と比べて何がすごい？

* Decafの転移学習＋MLR(多項ロジスティック回帰)を使うことで、いずれのモデルより高い精度が出た。

![例](https://image.ibb.co/iLhKzS/scratch04.jpg)

---

## 議論はある？


* Decafなど転移学習を応用すれば、少ない画像データでもDeepLeaningビジネスが提供できそう。

* 日本国内の企業向けに細かく多様な展開ができる可能性あり？

* ところでこの論文書いたのはシンガポールの女性技術者。日本も頑張れ！
<img src="https://ieeexplore.ieee.org/mediastore/IEEE/content/freeimages/6221036/8283862/7864335/ren-2668395-small.gif" width="150" height="200" />


---

## 次に読むべき論文は？

* 技術視点＋ビジネス視点で！

