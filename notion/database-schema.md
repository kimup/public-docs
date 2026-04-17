# Notion Database Schema

公開用ドキュメントをNotionで管理するための推奨データベース設計です。

## Database Name

```text
Public Docs
```

## Properties

| Property | Type | Required | Description |
|---|---|---:|---|
| Name | Title | Yes | ドキュメント名 |
| Category | Select | Yes | ドキュメント種別 |
| Status | Select | Yes | 作成・公開状態 |
| Owner | Person | Yes | 管理者 |
| GitHub URL | URL | Yes | GitHub上の公開URL |
| Source Path | Text | Yes | リポジトリ内のパス |
| Tags | Multi-select | No | 検索用タグ |
| Last Reviewed | Date | No | 最終レビュー日 |
| Publish OK | Checkbox | Yes | 公開前確認済みか |
| Notes | Text | No | 補足 |

## Category Values

```text
Guide
Reference
FAQ
Release Notes
Policy
Template
Other
```

## Status Values

```text
Draft
Review
Published
Archived
```

## Visibility Rule

このリポジトリは公開用です。Notion上でも `Public` として扱える情報だけを登録します。

公開してはいけない情報は、NotionにもGitHubにも書かず、private repository やパスワードマネージャーで管理します。
