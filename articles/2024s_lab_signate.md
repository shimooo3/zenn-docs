---
title: "【SIGNATE】データ分析やってみよう"
emoji: "🐮"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["SIGNATE"]
published: true
---
SIGNATEの練習問題をやってみようという記事です．
![](https://storage.googleapis.com/zenn-user-upload/8a90d785775c-20240727.jpg)
*[ソース](https://signate.jp/faqs)*
### はじめに
研究室の夏休み課題の解説？記事です．SIGNATEというデータ分析コンペに参加してGoogle Colaboratoryで分析し提出するまで一緒に頑張りましょう．具体的な技術自体の解説はしません．研究室内ではB4のK.Tさん，M2のS.Kさんがデータ分析にがっつり取り組んでいるのでそちらに相談するのも◎です．逆に私は少しかじった程度です．
#### キーワード
あまり解説を見ずに自力で頑張りたい方は以下のキーワードだけ覚えてブラウザバック推奨です（全部を使う必要はないです）．
`データクレンジング` `特徴量エンジニアリング` `回帰・分類` `特徴量重要度` `混同行列` `アンサンブル学習`

### データのダウンロード
まずは以下のSIGNATE公式が提供しているgithubにアクセスして，Google Colaboratoryを開いてください．Googleアカウント作ってねアクセスしてね．Google Colaboratoryについては調べてください．オンライン環境でpythonが実行できるやつです．

https://github.com/signatelab/colaboratory

#### "注意" 練習問題を一緒に取り組む場合はこのページ下部の`データ分析してみよう!!`のリンクからGoogle Colaboratoryにアクセスしてください．
"Open in Colab"をクリックしてください．
![](https://storage.googleapis.com/zenn-user-upload/409079c92154-20240727.jpg)

開いたら"ファイル" -> "ドライブにコピーを保存"の順に選択してください．githubのフォークに近い感覚です．
![](https://storage.googleapis.com/zenn-user-upload/52a567cd1057-20240727.jpg)
次にInstallationの再生ボタン（横向き三角形）をクリックしてください．
![](https://storage.googleapis.com/zenn-user-upload/1d300ddc0c52-20240727.jpg)
次にAPI Tokenを取得するために[SIGNATEアカウント設定ページ](https://signate.jp/account_settings)に移動して画面下方の"API Token"から作成してください．新規作成をクリックすると以下画像の様なjsonファイルがダウンロードされるはずです．
![](https://storage.googleapis.com/zenn-user-upload/4d94afa195c0-20240727.jpg)
Google Colaboratoryに戻り"Upload token file"を実行し，先ほどダウンロードしたjsonファイルを選択してアップロードしてください．その後"Move token file"，"Check command"を実行してください．
次に開催中のコンペ一覧を確認しましょう．
![](https://storage.googleapis.com/zenn-user-upload/fdf428bdc133-20240727.jpg)
今回は`105  【練習問題】毒キノコの分類  `でデータ分析をやってみましょう．
コンペの参加規約に同意していない場合は以下画像の様な出力があるのでリンク先に遷移して，"投稿"をクリックし規約に同意することが必要です．
![](https://storage.googleapis.com/zenn-user-upload/3106c6dfbc74-20240727.jpg)
同意するとこんな感じになるはずです．
![](https://storage.googleapis.com/zenn-user-upload/3ebd9161d0d6-20240727.jpg)
"一括ファイルのダウンロード"を実行してファイルをダウンロードしてください．これにてデータ分析のための訓練データと評価データのダウンロード完了です．

### データ分析
以降はコードベースの説明が多くなるので以下githubのGoogle Colaboratryで解説します．以下リンク先のOpen in Colaboratoryを開いてファイル->コピーを保存してから実行していってください．

[データ分析してみよう!!](https://github.com/shimooo3/b3summer/blob/main/minelab_2024_summer.ipynb)

簡単な分析のみの紹介です．より深い分析のためにはキーワードに挙げたものを意識してみるとよいでしょう．
参考までに上のコードで分析を行った際のランキングを以下に示しておきます．
![](https://storage.googleapis.com/zenn-user-upload/3c602990dd42-20240727.jpg)

🎐よい夏休みを～
