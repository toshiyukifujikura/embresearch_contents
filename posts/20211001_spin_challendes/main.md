---
Keywords: モデル検査, SPIN  
Copyright: (C) 2021 Laboratory Design  
---

# SPINの課題

おそらく日本で利用者の多いモデル検査ツールはSPINだと思われる．SPINの特徴は，モデルの記述がC言語ライクなことであり，その結果以下の様なメリットがある．

- プログラマには取っ付き易い
- ソースコードからモデルを作って問題点を検証し易い

ソースコードレベルのデバッグには良いかも知れないが，一般的に恐ろしく長いログを読まなければならない．また，複数のプロセスを記述した場合，そのプロセスの動き方がデバッグ対象のシステムにおけるプロセスあるいはタスクと同一か，割込ハンドラと同一なのか，ハードウェアコンポーネントも含んでいる場合並列性は記述できているのかを慎重に検討しなければならない．ここが曖昧だと，システムをデバッグしているのかSPINモデルをデバッグしているのか分からなくなる．首尾良くSPIN上で問題が解決しても，「だから何?」と言うことになる．SPINでは，問題を発見できたらそれ以降はSPIN以外で問題解決した方が良い場合が多い．それは，動作モデルが対象システムとは異なっているからである．また，問題が発見できなくても，それは対象システムに問題が無いことを示してはいない．やはり動作モデルが異なるからである．SPINを利用する場合の課題としては，

- ソースコードより抽象度の高い情報とSPINモデルをリンクさせること
- 開発対象の動作モデルと整合性を取ること

が必要となる．

## 上流工程が無いこと

SPINは極端に言えば，promelaソースコードから始まる．あるいは，せいぜいUMLやSysMLの状態図やシーケンス図をpromelaのプロセスに変換するところから始まる．その上が無いのが問題である．状態図やシーケンス図をpromelaに変換して問題が検出されたら，もとの状態図やシーケンス図を修正して再度SPINで検査すると言うのが正しい使い方になるが，何故その様な状態図やシーケンス図が出てきたのかについてはSPINの対象外になる．それらの図の妥当性については，より上流の要求から導く必要があり，この部分の改善には直接SPINは寄与しない．プロセス代数などの上位理論を持っているFDRやLTSA等のツールであれば要求からの動作モデルをLTLで記述してそこから検査用モデルを生成することができる．SPINにもLTL式からプロセスを生成する機能はあるが，あくまでも検査用のプロセスであり要求分析には使えない．

要求レベルでの検証をFDRやLTSAで実施し，そのモデルをpromelaに変換して利用するプロセスが必要になる．

## 動作モデルについて

組込システムをモデル化する場合には，コンポーネントの振る舞いを正確に記述しなければならない．少なくとも以下の動作とモデル検査用モデルとの間でマッピングが取れなければ正確な検証はできない．

- プロセスやタスク: 優先順位とFIFOベースのスイッチング動作，Wait状態の表現
- 割込ハンドラ: 優先度付きでWait状態が無いカスケード動作
- ハードウェアコンポーネント: 完全な並列動作

通信については，

- 1対1通信
- ブロードキャスト通信

の区別が必要である．SPINについて言えば，並列動作の記述は困難である．並列動作を記述するにはNuSMVの様な同期合成をサポートしているツールか，FDRやLTSAの様に同時イベントを定義できるツールを利用する必要が有る．

## まとめ

以上，2点がSPINを利用する上で考慮すべき点であると認識している．

## 関連情報  
1.[SPIN](https://github.com/nimble-code/Spin)  
2.[SPIN Model Checker, The: Primer and Reference Manual](https://amzn.to/3FkJUKj)

