# X Content Notion Database Schema

X向け投稿案をNotionで管理するための推奨データベース設計です。

## Database Name

```text
X Content Pipeline
```

## Properties

| Property | Type | Required | Description |
|---|---|---:|---|
| Name | Title | Yes | 投稿テーマ |
| Type | Select | Yes | 投稿タイプ |
| Status | Select | Yes | 作成状態 |
| Source URL | URL | No | 元記事、GitHub、Notionページなど |
| Source Path | Text | No | GitHub内の元ファイルパス |
| Draft | Text | No | 投稿本文の下書き |
| Hook | Text | No | 冒頭の一文 |
| Target Reader | Select | No | 想定読者 |
| Tags | Multi-select | No | トピックタグ |
| Publish Date | Date | No | 投稿日 |
| X URL | URL | No | 投稿後のURL |
| Review OK | Checkbox | Yes | 投稿前レビュー済みか |
| Notes | Text | No | 反応、改善点、次回ネタ |

## Type Values

```text
Single Post
Thread
Article Summary
Release Note
Tip
Question
```

## Status Values

```text
Idea
Draft
Review
Scheduled
Published
Archived
```

## Target Reader Values

```text
Beginner
Developer
Founder
Customer
General
```

## 運用ルール

- `Review OK` が未チェックの投稿は公開しない
- `Published` にしたら `X URL` を記録する
- 内部情報、秘密情報、個人情報を含む投稿案は削除または非公開DBに移す
- 公開ドキュメント由来の場合は `Source URL` または `Source Path` を必ず記録する
