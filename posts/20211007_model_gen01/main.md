---
Keywords: モデル検査, 状態, 時相論理式  
Copyright: (C) 2021 Laboratory Design  
---

# 検査用モデルの作り方  
[1]に紹介されているプリンタマネージャの動作モデルを以下に示す．このモデルは，二人のユーザA, Bが一つのプリンタを共有している際のプリンタの動作モデルである．プリンタの基本的な動作としては，req, beg, endがある．reqはプリント要求受付，begはプリント開始，endはプリント終了．ユーザ毎にアクションを識別していて，たとえば req<sub>A</sub> は，ユーザAのプリント要求である．P, W, Rは命題で，どちらかと言うとユーザーの状態を表す．Pはプリントが終了するのを待っている，Wはプリントが始まるのを待っている，Rは特に要がない状態を表す．[状態の意味](https://embresearch.com/?post=20211006_state_logic)で説明したように，状態の意味は命題，別名プロパティで表す．Rはreqする前の状態，Wはgebの前，Pはbegの後でendの前に対応している．状態を表す円の中に，そこで成立する命題が書き込んである．

<img src="Fig1-6.jpg" title="A printer manager" width=70%>  
[1]のFig. 1.6.より  


［1］では，このモデルをどの様に作ったのかについて説明は無い．このモデルが与えられていて，要求が無いのにプリントすることは無いと言ったプロパティを証明している．このプロパティの例だとつまらないけれど，このモデルはユーザAの要求ばかり処理してフェアで無いというプロパティも検出できるので意味はある．しかし実際には，このモデルをどの様に作ったのかが重要であり，それが分からないと話が始まらない．それを説明するのがここでの目的である．

## ベースモデル
LTSA[2][3]というモデル検査を用いてベースモデルを作る．

## 状態分析

[状態の意味](https://embresearch.com/?post=20211006_state_logic)で説明した手法でベースモデルで生成されている状態を分析する．

## まとめ  


## 関連情報  
1.[Systems and Software Verification: Model-Checking Techniques and Tools](https://amzn.to/3FmU9xG)  
2.[LTSA](https://www.doc.ic.ac.uk/ltsa/)  
3.[Concurrency: State Models and Java Programs](https://amzn.to/3mxg3Wj)
