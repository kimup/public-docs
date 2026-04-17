# Notion Management

Notionでドキュメント、メモ、作業ログ、投稿管理を行うための公開用ルールです。

## Purpose

- 非公開の作業ハブを整理する
- メモ、下書き、作業ログ、投稿管理を混ぜない
- 公開できるドキュメントだけGitHubへ出す
- CodexがNotionを更新するときの置き場所を明確にする

## Recommended Hub Structure

```text
Codex Hub
  メモ
    X API Billing Credits
    X投稿ができるまで
  Codex作業ログ
    作業ログDB
  X Ideas
  X Drafts
  X Post History
  Drafts
  Private Docs
  Ideas
```

詳しくは [Codex Hub Structure](./codex-hub-structure.md) を参照。

## Basic Policy

- Notionは非公開の作業ハブとして使う
- GitHub public repositoryには公開してよいルールとテンプレートだけ置く
- token、secret、`.env` の中身はNotionにもGitHubにも書かない
- 単発メモは `メモ` 配下に集約する
- 作業履歴は `Codex作業ログ / 作業ログDB` に記録する
- X投稿は `X Ideas`、`X Drafts`、`X Post History` の3つで管理する

## Documents

- [Codex Hub Structure](./codex-hub-structure.md): Notion内の推奨ページ構成
- [Database Schema](./database-schema.md): 公開ドキュメント管理用DBの例
- [Posting Guide](./posting-guide.md): Notionへの登録方法
- [Publishing Checklist](./publishing-checklist.md): 公開前チェック
- [Codex Prompts](./codex-prompts.md): Codexに依頼する時のプロンプト

## File Structure

```text
notion/
  README.md
  codex-hub-structure.md
  database-schema.md
  posting-guide.md
  publishing-checklist.md
  codex-prompts.md
  templates/
    public-doc-template.md
    notion-page-template.md
```
