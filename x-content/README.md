# X Content Workflow

X向けの投稿アイデア、下書き、レビュー、投稿履歴をCodexとNotionで管理するための公開用ワークフローです。

## Goals

- 投稿アイデアを継続的に蓄積する
- 投稿前本文と投稿後履歴を分けて管理する
- 人間のレビューなしに投稿しない
- API投稿する場合も、Review OKとdry-runを必須にする
- 公開してはいけない情報を投稿に含めない

## Recommended Notion Databases

X投稿は1つの巨大DBではなく、3つに分けて管理します。

```text
X Ideas        # 投稿前アイデア
X Drafts       # 投稿前本文、レビュー状態
X Post History # 投稿済みURL、結果、学び
```

同じ投稿に関係する行は、共通の `Content ID` で結びつけます。

例:

```text
X-YYYYMMDD-001
```

## Basic Flow

1. アイデアを `X Ideas` に登録する
2. 投稿本文を作り、`X Drafts` に同じ `Content ID` で登録する
3. 投稿本文に `Ready To Post` セクションを用意する
4. 人間が確認し、`Review OK` をチェックする
5. CLIや手動でdry-run相当の確認をする
6. 問題なければXへ投稿する
7. 投稿後、`X Post History` にURLと結果を記録する

## Documents

- [Posting Guide](./posting-guide.md): 手動投稿、Codex補助、X API投稿の流れ
- [Notion Database Schema](./notion-database-schema.md): 3DB構成の推奨schema
- [Publishing Checklist](./publishing-checklist.md): 投稿前チェック
- [Codex Prompts](./codex-prompts.md): 投稿案作成・レビュー用プロンプト

## Templates

- [Single Post Template](./templates/single-post-template.md)
- [Thread Template](./templates/thread-template.md)
- [Article to Post Template](./templates/article-to-post-template.md)

## Safety

- `Review OK` がない投稿は公開しない
- tokenやsecretはGitHubに置かない
- 未公開情報、個人情報、顧客情報を投稿に含めない
- API投稿前に必ず本文を確認する
