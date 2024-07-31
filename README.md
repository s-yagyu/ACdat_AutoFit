# ACdat-AutoFit

20240731　改訂版（Version1)

理研計器ACシリーズで測定したdatファイルをアップロードすると、自動で閾値を推定するお試し版のWebアプリです。
（あくまでもお試しですので、利用者の責任で閾値の最終判断をしてください。）

https://acdat-autofit-huy3ftxmaqjr4ivninr3rh.streamlit.app/

測定結果の1/2乗、1/3乗を計算して、拡張されたReLU関数をFitting関数として、最小化関数として絶対誤差を用いて推定を行っています。

それぞれのべき乗に対してFittingの当てはまり（決定係数）を評価し、決定係数が1に近い方を推奨としています。

R2が全体の決定係数、R2Sが閾値よりエネルギーが高い領域のみで計算した決定係数です。バックグラウンド成分に大きなノイズが乗っているときはR2Sの方の指標を優先した方がよいかもしれません。

なお、datファイルフォーマットの仕様および変換については理研計器社にお問い合わせください。

理研計器社が配布している変換ツールで

- AC-2、AC-3：（MDB型）変換ソフトで.datフォーマット（新形式0） へ変換
- AC-5：.datフォーマット（旧形式） 変換ソフトで.datフォーマット（新形式）へ変換

  
---

![AF01](./figs/AF01.png)

Datファイルをドラッグアンドドロップしてください。（複数のファイルも可能）

GithubリポジトリにあるtestDataの中のファイルをテストとして利用することができます。

----

![AF02](./figs/AF02.png)

PYSの強度を1/2、1/3乗したグラフぞれぞれにReLU関数でのFittingを行います。そして決定係数を求めて比較します。

比較の結果、１つ目のデータは1/2乗の方が当てはまりがよいので、1/2乗で解析した閾値が選ばれています。なお、1/2乗のUserの線は人が引いた線です。

Download(zip) ボタンを押すとグラフと解析結果のレポートのダウンロードができます。
- グラフイメージ
- 解析結果　Text形式
- 解析結果　Toml形式（Txdで読み込むこともできます。）

![AF03](./figs/AF03.png)

---


