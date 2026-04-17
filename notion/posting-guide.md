# How to Post to Notion

Notionへドキュメントや投稿案を登録する方法を、手動、半自動、API自動化の3段階で整理します。

## 1. 手動で登録する

最初はこの方法が安全です。

### 手順

1. GitHub上の公開ドキュメントを開く
2. Notionの `Public Docs` データベースを開く
3. `New` で新しいページを作る
4. `Name`、`Category`、`Status`、`GitHub URL`、`Source Path` を入力する
5. 本文には概要、リンク、補足だけを書く
6. `publishing-checklist.md` を確認する
7. 問題なければ `Publish OK` をチェックする

### Notion本文の例

```markdown
# X Content Workflow

## Summary

X向け投稿案をCodexで作るための公開用ワークフローです。

## Source

- GitHub URL: https://github.com/kimup/public-docs/blob/main/x-content/README.md
- Source Path: x-content/README.md

## Status

Published
```

## 2. CodexでNotion登録用の内容を作る

CodexにNotionへ貼る内容を作らせます。Notionへの貼り付けは人間が行います。

### プロンプト例

```text
以下のMarkdownをNotionの Public Docs データベースに登録するための内容に変換してください。

出力:
- Name
- Category
- Status
- GitHub URL
- Source Path
- Tags
- Summary
- Notion本文

条件:
- 公開してよい情報だけ使う
- 秘密情報や内部情報は含めない
- 本文はNotionに貼りやすいMarkdownにする

Markdown:
...
```

## 3. Notion APIで自動登録する

Notion APIを使うと、GitHub上のMarkdownやX投稿案をNotionのデータベースに自動登録できます。

### 必要なもの

- Notion Integration
- Integration Token
- 対象データベース、またはData SourceのID
- Integrationに対象ページまたはデータベースへのアクセス権を付与すること

### 安全ルール

- Integration TokenはGitHubにcommitしない
- `.env` やsecret managerで管理する
- 公開用データベースには公開してよい情報だけ送る
- 自動登録後も人間が `Publish OK` を確認する

## Notion Integrationの準備

1. NotionのMy integrationsでInternal Integrationを作る
2. Integration Tokenを取得する
3. Notionの対象データベースを開く
4. `Add connections` から作成したIntegrationを追加する
5. データベースID、またはData Source IDを控える

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
    "markdown": "# Summary\\n\\nGitHubで管理している公開ドキュメントです。"
  }'
```

## JavaScript SDKの例

```javascript
import { Client } from "@notionhq/client";

const notion = new Client({ auth: process.env.NOTION_ACCESS_TOKEN });

await notion.pages.create({
  parent: {
    data_source_id: process.env.NOTION_PUBLIC_DOCS_DATA_SOURCE_ID,
  },
  properties: {
    Name: {
      title: [
        {
          text: {
            content: "New Public Doc",
          },
        },
      ],
    },
  },
  markdown: "# Summary\n\nGitHubで管理している公開ドキュメントです。",
});
```

## 自動化するときの流れ

```text
GitHub Markdown
  -> CodexでNotion用メタデータ作成
  -> 公開前チェック
  -> Notion APIでPublic Docsに登録
  -> Notion上で人間が確認
  -> Publish OK
```

## 公式リファレンス

- Notion API Authentication: https://developers.notion.com/reference/authentication
- Notion Authorization: https://developers.notion.com/docs/authorization
- Notion Create a page: https://developers.notion.com/reference/post-page
