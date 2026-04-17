# Notion Management

このディレクトリは、公開用ドキュメントをNotionで管理するためのルール、テンプレート、データベース設計をまとめます。

## 目的

- GitHub上の公開ドキュメントをNotionから探しやすくする
- 公開してよい情報だけを扱う
- 公開前レビューの観点を統一する
- Codexでドキュメントを作成・更新しやすくする

## 基本方針

- GitHubを公開ドキュメントの正本にする
- Notionは目次、ステータス管理、検索用ポータルとして使う
- APIキー、パスワード、秘密鍵、個人情報、顧客情報は記載しない
- 内部用ドキュメントは private repository または private Notion に分ける

## 推奨フロー

1. `docs/` または公開用MarkdownをGitHubで作成する
2. 公開前チェックリストで内容を確認する
3. NotionのDocs Databaseにページを登録する
4. `GitHub URL` と `Source Path` をNotionに記録する
5. 定期的に `Last Reviewed` を更新する

## ファイル構成

```text
notion/
  README.md
  database-schema.md
  publishing-checklist.md
  codex-prompts.md
  templates/
    public-doc-template.md
    notion-page-template.md
```
