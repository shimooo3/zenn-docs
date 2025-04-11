---
title: "Stable Diffusionをローカルデータで訓練する際の備忘録"
emoji: "🐮"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["StableDiffusion"]
published: true
---
# Stable Diffusionをローカルデータで訓練する際の備忘録
diffusers版を使用してSD2.1を訓練する際に詰まった点をまとめたものです．

https://github.com/huggingface/diffusers/tree/main/examples/text_to_image

状況としてはReadme記載されているhugginface上のデータセットを用いたSDの追加学習は実行可能なものとします．

## 全無視の結論
環境構築後に以下をアンインストール&インストール
```
$ pip install datasets==2.13.0
$ pip install fsspec==2023.9.2
```
画像が格納されているフォルダの名前を`train`に変更．
```
data/
  |_/train
    |_*.jpg
  |_metadata.jsonl
```
.jsonlのカラム名を以下に合わせる．
```
{"file_name": "train/*.jpg", "text": "hogehoge"}
```

以上で解決しました．

## 詰まった点
ローカルデータを読み込めない．用意したデータは以下の様な形式でした．
```
data/
  |_/images
    |_*.jpg
  |_metadata.jsonl
```

metadata.jsonlの中身
```
{"image": "data/*.jpg", "text": "hogehoge"}
```
訓練時のエラーは.jsonlのカラム名が間違っているというエラーでした．
```
ValueError: --caption_column' value 'text' needs to be one of: image
```

初期対応として学習のスクリプトに以下を追加しましたが解決しませんでした．
```
--caption_column="text"
```

キャッシュが足りないという時はpc再起動が手っ取り早いです．

## 解決時に参考にしたもの

https://github.com/huggingface/diffusers/issues/6821

https://github.com/huggingface/diffusers/discussions/6671

