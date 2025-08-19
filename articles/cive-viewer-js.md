---
title: "【可視化】緑領域抽出指標の可視化"
emoji: "🐮"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ['ExG', 'CIVE']
published: true
---
# 緑領域抽出指標の可視化
RGB値を用いて画像内の緑色の領域を抽出する指標として`ExG`，`CIVE`が存在します．これらがRGB空間において，どのような平面をとっているのかを可視化することで，二値化のイメージをつかむことを目的とします．今後，枝領域や空のみを抽出する指標を作成した際に，視覚的に検証しやすくなります．

## 緑領域抽出指標とは
- カメラで撮影された画像からRGB値を用いて，植物の領域を抽出するための指標であり，`G`の値が強い場合にフラグが立ちます．
- 使用目的は，農地の雑草検出であったり，都市部における緑化率の測定に使用されます．
- 人間でさえも計算可能な低次元の数値計算のみで抽出を行うため，計算量が非常に少ないです．
- 葉に囲まれた果実の検出に利用することも可能です．

## 二値化画像
実際にExG，CIVEを用いて二値化を行った画像を以下に示します．
注意点として`ExG > 0`ならば緑，`CIVE < 0`ならば緑と正負が逆です．
以下は私が撮影した紫陽花の画像です．この画像を二値化します．
![](https://storage.googleapis.com/zenn-user-upload/304a6e3c8f0f-20250819.jpg)

左端は処理の都合でグレースケースになった元画像，中央がExGによる画像，右側がCIVEによる画像です．
![](https://storage.googleapis.com/zenn-user-upload/cbfa8f7a3a46-20250819.png)

画像内のどのピクセルが抽出対象なのか，分かりやすくするために以下のwebアプリケーションを作成しました．

## グラフによる可視化

https://github.com/shimooo3/CIVE_viewer

ターミナルで以下を実行することで，ローカル環境で確認できます．
簡易的な確認であればindex.htmlをブラウザで開くだけでも大丈夫です．
```
$ python3 -m http.server 8000
```
以下は動作例です．3Dグラフはドラッグによる回転，色選択による点描，平面の描画が可能です．
![](https://storage.googleapis.com/zenn-user-upload/b154bc93000d-20250819.jpg)
![](https://storage.googleapis.com/zenn-user-upload/d304c45ab534-20250819.jpg)


### 参考文献（緑領域抽出指標）
ExG

https://www.sciencedirect.com/science/article/abs/pii/S0168169908001063

CIVE

https://ieeexplore.ieee.org/document/1225492

https://www.jstage.jst.go.jp/article/jsam1937/67/2/67_2_37/_article

