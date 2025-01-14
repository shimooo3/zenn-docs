---
title: "【LaTex】chapter見出しを二重線で装飾しよう!!"
emoji: "🐮"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["LaTex", "overleaf"]
published: false
---
# chapter見出しを二重線で装飾しよう
結論としてはoutput.pdfに出力されるものは期待通り，ソースは不格好というものになりました．
## 出力結果とソース
実際の出力結果が以下の通りになります．

![](https://storage.googleapis.com/zenn-user-upload/629df37d70bc-20250114.png)

#### ソース（インデントぐちゃぐちゃですいません）
```latex
\titleformat{\chapter}[display] 
  {\normalfont\huge\bfseries} 
  {\titlerule[1pt]\vspace{1pt}\titlerule[0.5pt]\vspace{4ex} 第\thechapter{}章 序論}
  {4ex}
  {\titlerule[0.5pt]\vspace{1pt}\titlerule[1pt]\vspace{-2ex} }
\chapter{}
\section{はじめに}
  こんにちは
\section{研究概要}
```

### 実行環境
LaTexの実行環境は以下を参考にしています．

https://qiita.com/haradakaito/items/26ae779db23a1c862158

## 本文のような何か

### 動機
卒論をLaTexで書きたい!!でも，テンプレートが微妙に違う．多分大丈夫だけど，どうせなら見た目にも拘りたい．

### できたもの
当初の予定では`\chapter{序論}`で上画像のような出力を目指していました．しかしながら，筆者のLaTex力では以下のようなものが限界でした．
![](https://storage.googleapis.com/zenn-user-upload/f7819540c91d-20250114.png)
どうしても`第一章`と`序論`の間の改行が消せませんでした．
改行を消そうとすると，下側の二重線と合体したり
![](https://storage.googleapis.com/zenn-user-upload/5a99a0ad1fd9-20250114.png)
上側の二重線まで消えたりしました．
![](https://storage.googleapis.com/zenn-user-upload/25c7faf0c839-20250114.png)
結局`\chapter{}`を使用するたびに，`\titleformat`を用いながらハードコーディングでタイトルを記述するという形になりました．
```latex
\titleformat{\chapter}[display] 
  {\normalfont\huge\bfseries} 
  {\titlerule[1pt]\vspace{1pt}\titlerule[0.5pt]\vspace{4ex} 第\thechapter{}章 序論}
  {4ex}
  {\titlerule[0.5pt]\vspace{1pt}\titlerule[1pt]\vspace{-2ex} }
\chapter{}
\section{はじめに}

\titleformat{\chapter}[display] 
  {\normalfont\huge\bfseries} 
  {\titlerule[1pt]\vspace{1pt}\titlerule[0.5pt]\vspace{4ex} 第\thechapter{}章 関連研究}
  {4ex}
  {\titlerule[0.5pt]\vspace{1pt}\titlerule[1pt]\vspace{-2ex} }
\chapter{}
\section{研究A}
```
![](https://storage.googleapis.com/zenn-user-upload/83255db3c8f3-20250114.png)

### おわりに
LaTexの装飾はとても難しいです．今回は見える部分のみ頑張りました．修論を書くころにはソースを洗練させたいです．
これを読んでいる論文執筆者さん，私と一緒に頑張っていきましょう!!!