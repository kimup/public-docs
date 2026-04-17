# X Content Workflow

X向けの記事、ポスト、スレッドをCodexで作成するための公開用ワークフローです。

## 目的

- 投稿案を継続的に作れるようにする
- NotionやGitHub上の公開ドキュメントを投稿ネタに変換する
- 投稿前レビューの観点を統一する
- 公開してはいけない情報を投稿に含めない

## 基本方針

- 投稿の元ネタは公開してよい情報だけにする
- GitHubにはテンプレートと運用ルールを置く
- Notionには投稿候補、ステータス、投稿日、URLを管理する
- Codexは初稿作成、言い換え、スレッド化、公開前チェックに使う
- 投稿の最終判断は人間が行う

## 推奨フロー

1. 公開ドキュメントやメモから投稿テーマを選ぶ
2. CodexでX向けの投稿案を作る
3. 投稿前チェックリストで内容を確認する
4. Notionの投稿管理データベースに登録する
5. 投稿後にURL、反応、学びを記録する

## ファイル構成

```text
x-content/
  README.md
  notion-database-schema.md
  publishing-checklist.md
  codex-prompts.md
  templates/
    single-post-template.md
    thread-template.md
    article-to-post-template.md
```

## 投稿タイプ

| Type | Description |
|---|---|
| Single Post | 1投稿で完結する短文 |
| Thread | 複数ポストで説明する連投 |
| Article Summary | 記事やドキュメントの要約投稿 |
| Release Note | 更新内容の告知 |
| Tip | 小さな知見や手順 |
| Question | 読者に問いかける投稿 |

## Posting Guide

- [How to Post to X](./posting-guide.md): 手動投稿、Codex補助、X API自動投稿の具体手順
