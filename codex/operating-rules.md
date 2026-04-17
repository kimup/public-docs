# Codex Operating Rules

Codexを使うときの基本ルールです。

## General Rules

- 既存ファイルを確認してから編集する
- ユーザーが作った変更を勝手に戻さない
- 不要な重複ファイルや一時ファイルを残さない
- 大きな変更では、何を変更したか作業ログに残す
- 公開用リポジトリには公開してよい情報だけを書く
- 非公開情報はprivate Notion、private repository、またはローカル環境で管理する

## Secrets Rule

以下は公開リポジトリに書かない。

```text
.env の中身
API key
Access token
Refresh token
Password
Secret key
Private key
個人情報
顧客情報
内部URL
実際のNotion page/database ID
実際のX account ID
```

環境変数名や抽象化した設定例は書いてよい。

```text
X_USER_ACCESS_TOKEN=...
NOTION_ACCESS_TOKEN=...
```

## External Service Rule

外部サービスを操作する場合は、以下を守る。

- NotionやX APIへの書き込み前に対象を確認する
- 投稿や公開前はdry-runまたはレビューを挟む
- 成功/失敗を作業ログに残す
- APIエラーは原因、対処、次回ルールとして記録する

## Notion Naming Rule

Notion上でCodexが作成・更新するページや主要見出しは、日本語タイトルを優先する。

例:

| English | Preferred Japanese |
|---|---|
| Memo | メモ |
| Codex Work Log | Codex作業ログ |
| Codex Hub Guide | Codex Hubガイド |
| Work Logs database | 作業ログDB |

X固有のデータベース名は、対応関係が分かりやすい場合は英語名を維持してよい。

例:

```text
X Ideas
X Drafts
X Post History
```

## Cleanup Rule

- Codexが作った一時ファイルは作業完了時に削除する
- Notionで重複ページを作った場合は、正本を決めて不要な方をゴミ箱へ移動する
- メモ系ページをCodex Hub直下に増やさず、メモ配下へ集約する
- 削除や整理をした場合は作業ログに残す
