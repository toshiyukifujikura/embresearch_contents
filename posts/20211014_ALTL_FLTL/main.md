---
Keywords: 時相論理式, ALTL, FLTL, fluent  
Copyright: (C) 2021 Laboratory Design  
---

# 動作ベースと状態ベースの仕様記述について  
仕様をLTLで記述する方法に，動作ベースと状態ベースがある．お薦めは状態ベースである．動作で記述するより状態で記述する方が簡潔で一般性がある．

## 動作ベースの問題点  
動作ベースLTLをALTLと呼ぶ．ALTLでは、命題Pのセットは、アクション（またはイベント）命題の集合になる．解釈は、各時点で発生するアクションの割り当てになる．
一度に1つのアクションが発生するインターリーブモデルでは、これらのセットはシングルトンになる．
LTSの無限実行<a<sub>0</sub>a<sub>1</sub>a<sub>2</sub>···>は、各時点iϵNにアクションa<sub>i</sub>を割り当てる解釈を定義する．
LTS Mは、Mの実行によって定義されたすべての解釈でφが成り立つ場合にのみ、LTLプロパティφを満たす．
ALTLは、イベントベースのシステム記述のコンテキストでLTL式の明確で明白な解釈を提供するが、プロパティを指定する容易さには制限がある．

## テレビチューナの例  
このシステムに必要な特性は、チャンネルを変更するときに画面にアーティファクトが発生しないようにするために、チューナーが新しいチャンネルにチューニングしているときに画面をブランクにすることである．
画面はアクションblankによってブランクになり、アクションunblankが発生すると新しいチャネル信号が表示される．チューナーは、アクションtuneによって新しいチャネルへのチューニングを開始し、アクションendtuneによってチューニングが終了したことを示す．必要な安全特性は、「チューナーがチューニングされている場合は、画面をブランクにする必要がある」と表現できる．

これをALTLに変換するのは簡単ではない．画面が最初にブランクになっていると仮定すると、必要なプロパティは次のように表すことができる．

G( (unblank ⇒ (￢tune W blank)) ∧ (tune ⇒ (￢unblank W endtune)))  

実際のTVモデルでは、チューニングとブランキングを開始する方法が複数あり、これらのアクティビティと状態を終了する方法が複数ある．
さらに、このプロパティは、複数のチューナーと複数の出力デバイスを備えたアーキテクチャーに対して指定する必要もある．
ALTLで必要なプロパティを指定することは、すぐに管理できなくなる．  
その理由は、ALTLがアクションの提案に限定されているためである．(特定の瞬間に当てはまるのはそのうちの1つだけ) 
LTLプロパティをアクションの観点から直接表現する場合は、特にこれらのアクションを使用して時間間隔とそれらの間の関係を定義することが重要になる．
このような間隔は、多くの場合、それらを特徴付ける(システム)状態述語によって定義する方が簡単である．


# 状態ベース  

たとえば、ドライバーがチューニングしているときに真であるチューナードライバーの述語TUNINGと、画面がブランクになっているときに真であるスクリーンドライバーの述語BLANKEDを観察できれば、以下の様に，LTLで目的のプロパティを単純にGとして表すことができる．

G（TUNING ⇒ BLANKED）


## 関連情報  
1.[Action-LTL: D. Giannakopoulou, Model Checking for Concurrent Software Architectures, PhD Thesis, Imperial College London, 1999](https://ti.arc.nasa.gov/m/profile/dimitra/publications/thesis.pdf)  
2.[Fluent-LTL: Fluent Model Checking for Event-based Systems](https://ti.arc.nasa.gov/m/profile/dimitra/publications/esecfse03.pdf) <!-- 元ネタ C:\Users\toshiyuki\Dropbox\Work\LTSA\Fluent Model Checking for Event-based Systems esecfse03.pdf  -->

