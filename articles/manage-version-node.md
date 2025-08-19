---
title: "【備忘録】nodejs，npmのバージョンをあげる"
emoji: "🐮"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["linux", "nodejs", "npm"]
published: true
---

## 状況
nodejs，npmのバージョンを上げたい．なんかnvmが使えない．linux

## やること
```
$ sudo npm install n -g
$ sudo n lts
# 古いやつの削除
$ sudo apt purge nodejs npm
```

インストールしたやつが見つからない場合
```
$ node -v
  bash: /usr/bin/node: No such file or directory
# シェルのコマンドキャッシュをリセット
$ hash -r
```