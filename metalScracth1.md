

#A Generic Deep-Learning-Based Approach
for Automated Surface Inspection

##金属表面のキズ・腐食検査をスマート化できないの？~SORAサクライ　櫻井　敏明
===

Submitted on 2018/03
by Ruoxu Ren, Terence Hung, and Kay Chen Tan, Fellow, IEEE

<img src="https://ieeexplore.ieee.org/mediastore/IEEE/content/freeimages/6221036/8283862/7864335/ren-2668395-small.gif" width="150" height="190" />


https://ieeexplore.ieee.org/document/7864335/

---

#どんなもの？

## 背景

* 製造現場のスマート化の時代、人に依存する仕事はたくさん残っている
* 金属表面の検査もその１つ。キズや腐食の検査は自動化できず、人の視認検査に依存する。
* 金属部品は多品種少量。DeepLeaningを使うには、写真データの収集が困難。

![例](https://image.ibb.co/dd5kM7/scratch01.jpg)


## 動機
* 顧客の要求仕様は「キズがないこと」。　でも金属材料のキズは絶対なくならない！
* 視認検査は基準があいまい。検査者の主観に頼る。
* 出荷側と受入れ側でよく揉める。担当者が代わると基準が変わってまた揉める。。(限度見本をよく使う )

<img src="http://01.gatag.net/img/201506/03l/gatag-00006107.jpg" width="190" height="230" />



---

## どうやって有効だと検証した？

データ数は非常に少ない。金属損傷のデータベースサイトから300のサンプル、ロールスロイスシンガポールから


そこで画像認識の既存学習モデル・・・Decafを利用、少量データ学習を試した。



<img src="http://faculty.neu.edu.cn/yunhyan/Webpage%20for%20article/NEU%20surface%20defect%20database/Fig.1.jpg" width="400" height="380" />




* ①　画像を入力データに
* ②　畳み込み＋プーリング　→　Decaf 活用（後述）
* ③　出力データを全結合
* ④　異常（異なるパターン）を検知できた箇所がわかるようにヒートマップを生成
* ⑤　しきい値で問題箇所を洗い出し
* ⑥　最終出力　　



![例](https://image.ibb.co/bTsnZS/scratch02.jpg)

## 技術や手法の肝は？

Decaf（画像認識の既存学習モデル）による転移学習を活用したこと。

## →　Decaf（ディーキャフ）って何？
Caffe（BAIR） の前身。ImageNetで1000の分類で鍛えた画像認識の学習モデル。

* 画像認識技術では既存のSURFより優れる、など評価が高い 
* 転移学習（あらかじめ学習を行ったモデルを別のものに反映させる）の１つとして注目。
* 画像認識に強く、既存のディープラーニングモデルを少ないデータ数で活用。


　(以下は画像クラスタリングの精度比較)

![例](https://image.ibb.co/eMdEYn/scratch03.jpg)


* Decafの畳込み＋プーリングは一般的な層なのでそのまま。
* 結合層のfc6 も特定イメージに特化しない特徴抽出層なので残した。
* 最後の層だけLR(ロジスティック回帰）に変えた　（元々はSoftmax）

![例](https://image.ibb.co/h3q5ty/scratch02x.jpg)




---

## 先行研究と比べて何がすごい？

* 先行研究では、1800の教師あり学習データ＋同じ300のデータセットを使って98.61％が最高だった
* Decaf＋MLR(多項ロジスティック回帰)では、教師あり学習なしで 99.27%が出た。

![例](https://image.ibb.co/iLhKzS/scratch04.jpg)

---

## 議論はある？


* 転移学習を応用すれば、少ない画像データでもDeepLeaningビジネスが提供できそう。

* 日本国内の中小企業向けに細かく多様な展開ができる可能性ありでは？

* ところでこの論文書いたのはシンガポールの女性技術者。日本も頑張れ！






---

## 次に読むべき論文は？
金属表面の欠陥対応モデルに関する論文、他にもいろいろ読んだ。

* 熱間圧延鋼板の表面欠陥　(1675のサンプルデータで学習）
www.mdpi.com/2075-4701/7/8/311/pdf

* 鋼鉄の表面欠陥のための機械学習
http://mit.imt.si/Revija/izvodi/mit171/zhou.pdf

* 線路の表面欠陥
https://pdfs.semanticscholar.org/b2b8/ab163fb0183325dd3458e3cbaad2f8bf265e.pdf

でも転移学習は今回の論文だけ、US$30で買いました。

---

## →　画像回りのニッチなAIビジネスには転移学習で！

おわり






