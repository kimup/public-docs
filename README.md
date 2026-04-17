# public-docs

公開してよい運用ドキュメント、テンプレート、チェックリストを管理するリポジトリです。

## Contents

- [Codex Workflow](./codex/README.md): Codexを使うときの作業ルール、ディレクトリ構造、公開/非公開の分け方
- [Notion Management](./notion/README.md): Notionでドキュメント、メモ、作業ログを管理するための公開用ルール
- [X Content Workflow](./x-content/README.md): X向け投稿のアイデア、下書き、レビュー、投稿履歴を管理する運用ルール

## Repository Role

このリポジトリは公開用です。公開してよいルール、テンプレート、抽象化した手順だけを置きます。

非公開情報、実token、個別のNotion page ID、個別のX account ID、内部URL、個人情報は置きません。

## Recommended Directory Structure

```text
public-docs/
  README.md
  codex/
    README.md
    operating-rules.md
    directory-structure.md
    public-private-boundary.md
    templates/
      work-log-template.md
  notion/
    README.md
    codex-hub-structure.md
    database-schema.md
    posting-guide.md
    publishing-checklist.md
    codex-prompts.md
    templates/
  x-content/
    README.md
    posting-guide.md
    notion-database-schema.md
    publishing-checklist.md
    codex-prompts.md
    templates/
```

## Core Policy

- 公開してよい情報だけを保存する
- APIキー、トークン、パスワード、秘密鍵、個人情報、顧客情報は保存しない
- 非公開の下書き、作業ログ、API設定はprivate Notionまたはローカル環境で管理する
- Codexが作った内容は、人間が確認してから公開する
- 公開用ドキュメントは、再利用できるルールとテンプレートに寄せる

## Quick Links

- [Codex operating rules](./codex/operating-rules.md)
- [Public/private boundary](./codex/public-private-boundary.md)
- [Notion Codex Hub structure](./notion/codex-hub-structure.md)
- [How to post to Notion](./notion/posting-guide.md)
- [X content database schema](./x-content/notion-database-schema.md)
- [How to post to X](./x-content/posting-guide.md)
