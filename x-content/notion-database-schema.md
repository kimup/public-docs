# X Content Notion Database Schema

X投稿をNotionで管理するための推奨データベース設計です。

## Overview

```text
X Ideas        # 投稿前アイデア
X Drafts       # 投稿前本文、レビュー状態
X Post History # 投稿済みURL、結果、学び
```

同じ投稿に属するレコードは、共通の `Content ID` で結びつけます。

例:

```text
X-YYYYMMDD-001
```

## X Ideas

投稿前アイデアを管理するDB。

| Property | Type | Required | Description |
|---|---|---:|---|
| Name | Title | Yes | アイデア名 |
| Content ID | Text | Yes | 投稿単位の共通ID |
| Status | Select | Yes | Idea / Selected / Drafted / Archived |
| Category | Select | No | Codex / Notion / Workflow / Memo / Other |
| Target Reader | Select | No | Beginner / Developer / Founder / General |
| Angle | Text | No | 切り口、主張、肉付け |
| Source Path | Text | No | 元メモやファイルパス |
| Priority | Select | No | Low / Medium / High |
| Tags | Multi-select | No | トピックタグ |
| Notes | Text | No | 補足 |

## X Drafts

投稿前本文を管理するDB。

| Property | Type | Required | Description |
|---|---|---:|---|
| Name | Title | Yes | 投稿タイトル |
| Content ID | Text | Yes | `X Ideas` と共通のID |
| Status | Select | Yes | Draft / Review / Approved / Rejected / Archived |
| Type | Select | Yes | Single Post / Thread / Article Summary / Release Note / Tip / Question |
| Hook | Text | No | 冒頭の一文 |
| Related Idea | Text | No | 関連するIdea名やURL |
| Source Path | Text | No | ローカルMarkdownや元ファイル |
| Review OK | Checkbox | Yes | 投稿してよいかの人間レビュー |
| Tags | Multi-select | No | トピックタグ |
| Notes | Text | No | 補足 |

本文には `Ready To Post` セクションを作り、そのまま投稿できる文面を置きます。

## X Post History

投稿後履歴を管理するDB。

| Property | Type | Required | Description |
|---|---|---:|---|
| Name | Title | Yes | 投稿タイトル |
| Content ID | Text | Yes | `X Ideas` / `X Drafts` と共通のID |
| Post Date | Date | Yes | 投稿日 |
| Type | Select | No | Single Post / Thread / Reply / Quote |
| X URL | URL | Yes | 投稿URL |
| Draft URL | URL | No | 元DraftのNotion URL |
| Status | Select | Yes | Published / Deleted / Archived |
| Result | Text | No | 投稿結果 |
| Learnings | Text | No | 学び、反応 |
| Next Action | Text | No | 次の投稿や改善 |
| Tags | Multi-select | No | トピックタグ |

## Review Rule

- `Review OK` が未チェックのDraftは投稿しない
- 投稿前に本文を人間が確認する
- 投稿後は必ず `X Post History` に記録する
- 同じ投稿のIdea、Draft、Historyは同じ `Content ID` を使う
