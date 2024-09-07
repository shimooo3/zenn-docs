---
title: "【n番煎じ】PyGithubでコミットメッセージを取得する"
emoji: "🐮"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["github"]
published: true
---
:::message alert
自身のリポジトリの扱いには気を付けてください.特にプライベートなプロジェクト!!
:::

### 目的
日報を送信する際の本文水増し+具体的に何をしたのか簡単に記述すること．
### できること
自身のリポジトリから本日のコミットメッセージを取得する．
### 使うもの
- Githubのアクセストークン
- Python
### 準備（Githubのアクセストークン）
まずは自身のGithubにログインしてください．その後右上のアイコンを選択し`Settings`に移動してください．
![](https://storage.googleapis.com/zenn-user-upload/0c3bcfabc94e-20240907.jpg)
次に画面左下の`Developers settings`を選択してください．
![](https://storage.googleapis.com/zenn-user-upload/f4cf496f0a89-20240907.jpg)
次に`Tokens(classic)`を選択してください
![](https://storage.googleapis.com/zenn-user-upload/f19d6e19da37-20240907.jpg)
その後`Generate new token`を選択し，以下のようにスコープを設定してください．
![](https://storage.googleapis.com/zenn-user-upload/e5a273404c30-20240907.jpg)
`repo`全体ではなく`public_repo`のみを選択すればプライベートリポジトリにはアクセスしません．`Expiration`を用途に合わせて設定して，画面下部の`Generate token`からアクセストークンを作成して完了です．
### プログラム
自身のGithubにおけるコミットメッセージを取得します．先ほど取得したアクセストークンをプログラムにコピペしてください（今回は.envを利用しました．）
```python
from github import Github
from dotenv import load_dotenv
import os
from datetime import datetime, timezone

load_dotenv("./.env")
GITHUB_TOKEN = os.getenv("GITHUB_TOKEN")
token = GITHUB_TOKEN
g = Github(token)
today = datetime.now(timezone.utc).replace(hour=0, minute=0, second=0, microsecond=0)

def print_commit_info(repo, branch, commit):
    print(f"リポジトリ: {repo.name}")
    print(f"  ブランチ: {branch.name}")
    # print(f"    コミットSHA: {commit.sha}")
    # print(f"    作成者: {commit.commit.author.name}")
    print(f"    日時(UTC): {commit.commit.author.date}")
    message_lines = commit.commit.message.split('\n')
    print(f"      タイトル: {message_lines[0]}")
    # print("      本文:")
    # for line in message_lines[1:]:
    #     print(f"        {line}")
    # print("    変更されたファイル:")
    # for file in commit.files:
    #     print(f"      - {file.filename} ({file.status})")
    print("----")

for repo in g.get_user().get_repos(type='owner'):
    repo_has_changes = False
    branches = repo.get_branches()
    for branch in branches:
        try:
            commits = repo.get_commits(sha=branch.name, since=today)
            for commit in commits:
                commit_date = commit.commit.author.date
                if commit_date >= today:
                    if not repo_has_changes:
                        repo_has_changes = True
                        print_commit_info(repo, branch, commit)
                    else:
                        print_commit_info(repo, branch, commit)
        except Exception as e:
            print(f"リポジトリ {repo.name} のブランチ {branch.name} の処理中にエラーが発生しました: {str(e)}")
```
出力結果は以下のようになります．
```
リポジトリ: tools
  ブランチ: main
    日時(UTC): 2024-08-20 05:32:01+00:00
      タイトル: fix typo
```
出力を自身の用途に合わせて使ってください．
今回は日報の記述を少しでも楽にしたいという動機で本プログラムを作成しました．

#### 参考文献

https://github.com/PyGithub/PyGithub

https://qiita.com/yshr10ic/items/a416ba6fbea7637be552