# How to Post to Notion

Notionへドキュメントやメモを登録する方法を、手動、Codex補助、API自動化の3段階で整理します。

## 1. 手動で登録する

最初はこの方法が安全です。

### 手順

1. 登録したい内容が公開用か非公開用か確認する
2. Notionの保存先を選ぶ
3. 新しいページまたはDB行を作る
4. タイトル、ステータス、Source URL、Source Pathなどを入力する
5. 公開前チェックリストで確認する
6. 必要なら `Publish OK` や `Review OK` をチェックする

## 2. CodexでNotion登録用の内容を作る

CodexにNotionへ貼る内容を作らせます。Notionへの貼り付けや公開判断は人間が行います。

### プロンプト例

```text
以下のMarkdownをNotionに登録するための内容に変換してください。

出力:
- Name
- Category
- Status
- Tags
- Summary
- Source Path
- GitHub URL
- Notion本文

条件:
- 公開してよい情報だけ使う
- 秘密情報や内部情報は含めない
- 本文はNotionに貼りやすいMarkdownにする

Markdown:
...
```

## 3. Notion APIで自動登録する

Notion APIを使うと、Markdownや投稿案をNotionに自動登録できます。

### 必要なもの

- Notion Integration
- Integration Token
- 対象ページ、データベース、またはData Sourceへのアクセス権
- 保存先のpage ID、database ID、またはdata source ID

### 安全ルール

- Integration TokenはGitHubにcommitしない
- `.env` やsecret managerで管理する
- 公開用DBには公開してよい情報だけ送る
- 自動登録後も人間が確認する

## API投稿の最小例

Notion APIのページ作成は `POST /v1/pages` を使います。

```bash
curl -X POST 'https://api.notion.com/v1/pages' \
  -H "Authorization: Bearer $NOTION_ACCESS_TOKEN" \
  -H 'Notion-Version: 2026-03-11' \
  -H 'Content-Type: application/json' \
  --data '{
    "parent": {
      "data_source_id": "YOUR_DATA_SOURCE_ID"
    },
    "properties": {
      "Name": {
        "title": [
          {
            "text": {
              "content": "New Public Doc"
            }
          }
        ]
      }
    },
    "markdown": "# Summary\n\nGitHubで管理している公開ドキュメントです。"
  }'
```

## Recommended Placement

| Content | Notion Place |
|---|---|
| 短い運用メモ | `メモ` |
| API課金や設定メモ | `メモ` |
| Codex作業履歴 | `Codex作業ログ / 作業ログDB` |
| X投稿アイデア | `X Ideas` |
| X投稿本文 | `X Drafts` |
| 投稿済みURL | `X Post History` |
| 一般的な下書き | `Drafts` |
| 非公開ドキュメント | `Private Docs` |

## Common Errors

### `object_not_found`

対象ページやデータベースがIntegrationに共有されていない可能性があります。

対処:

1. Notionで対象ページを開く
2. `Connections` を確認する
3. Integrationを追加する
4. APIを再実行する

### Network restriction

ローカル環境や実行環境によっては、Notion APIへのネットワーク接続が制限されることがあります。

対処:

- 実行環境のネットワーク権限を確認する
- 失敗ログを保存する
- tokenやAuthorizationヘッダーはログに残さない

## Official References

- Notion API Authentication: https://developers.notion.com/reference/authentication
- Notion Authorization: https://developers.notion.com/docs/authorization
- Notion Create a page: https://developers.notion.com/reference/post-page
