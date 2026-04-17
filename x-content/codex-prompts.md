# Codex Prompts for X Content

X向け投稿案をCodexで作るためのプロンプト集です。

## アイデアをX Ideas用に肉付けする

```text
以下の粗いアイデアを、X Ideasに登録できる形へ肉付けしてください。

出力:
- Name
- Content ID案
- Status
- Category
- Target Reader
- Angle
- Priority
- Tags
- Notes

条件:
- まだ完成本文にしすぎない
- 切り口と読者が分かるようにする
- 公開してよい情報だけ使う
- 誤解を招く断定を避ける

アイデア:
...
```

## X Drafts用の本文を作る

```text
以下のX Ideasの内容を、X Draftsに登録できる本文へ展開してください。

出力:
- Name
- Content ID
- Status: Draft
- Type
- Hook
- Related Idea
- Tags
- Notes
- Markdown本文

Markdown本文には必ず以下を含めてください:
- Summary
- Draft Notes
- Ready To Post
- Alternatives
- Review Checklist

条件:
- Ready To Postはそのまま投稿できる文面にする
- 1投稿なら280文字以内にする
- 公開してよい情報だけ使う
- 最終投稿判断は人間が行う

Idea:
...
```

## 公開ドキュメントから投稿案を作る

```text
以下の公開ドキュメントを元に、X向け投稿案を作成してください。

条件:
- 外部公開してよい情報だけ使う
- 1投稿案を5本作る
- それぞれ Hook、本文、想定読者、投稿タイプを出す
- 誇張表現を避ける
- 秘密情報や内部情報が含まれそうな箇所は使わない

元ドキュメント:
...
```

## 1投稿に整える

```text
以下のメモをXの1投稿に整えてください。

条件:
- 1つの主張に絞る
- 冒頭で読者の関心を作る
- 具体例を1つ入れる
- 280文字以内にする
- 外部公開してよい内容だけにする
- 最後に軽い問いかけか次の行動を入れる

メモ:
...
```

## スレッド化する

```text
以下の内容をXのスレッドにしてください。

条件:
- 5から8投稿
- 1投稿目はテーマと読む価値を明確にする
- 各投稿は1メッセージに絞る
- 最後にまとめと関連リンクを入れる
- 内部情報、秘密情報、個人情報は含めない

内容:
...
```

## 投稿前レビュー

```text
以下のX投稿案を公開前レビューしてください。

観点:
- 秘密情報、内部情報、個人情報が含まれていないか
- 誤解を招く表現がないか
- 主張が強すぎないか
- X向けに読みやすいか
- 280文字以内か
- Review OKを付けてよい内容か

出力:
- 投稿可否: OK / NG / 要修正
- 問題箇所
- 修正版
```

## 投稿後の履歴を作る

```text
以下の投稿結果をX Post Historyに登録する形でまとめてください。

出力:
- Name
- Content ID
- Post Date
- Type
- X URL
- Draft URL
- Status
- Result
- Learnings
- Next Action
- Tags

投稿結果:
...
```
