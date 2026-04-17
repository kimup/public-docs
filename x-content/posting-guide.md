# How to Post to X

Xへ投稿する方法を、手動、Codex補助、API自動化の3段階で整理します。

## 1. 手動で投稿する

最初はこの方法が安全です。

### 手順

1. `X Ideas` に投稿アイデアを登録する
2. `X Drafts` に投稿本文を作る
3. 投稿本文に `Ready To Post` セクションを用意する
4. [Publishing Checklist](./publishing-checklist.md) で確認する
5. Notionの `Review OK` をチェックする
6. Xの投稿画面に本文を貼り付けて投稿する
7. 投稿後、`X Post History` にX URLを記録する

## 2. Codexで投稿本文を作る

Codexに投稿案を作らせ、投稿自体は人間が行います。

### 1投稿のプロンプト

```text
以下のメモをXの1投稿にしてください。

条件:
- 1つの主張に絞る
- 外部公開してよい情報だけ使う
- 冒頭で読者の関心を作る
- 280文字以内にする
- 誇張しない
- 最後に投稿前チェック項目も出す

メモ:
...
```

### アイデア肉付けのプロンプト

```text
以下の粗いアイデアを、X Ideasに登録できる形へ肉付けしてください。

出力:
- Name
- Content ID案
- Category
- Target Reader
- Angle
- Priority
- Tags
- Notes

条件:
- まだ投稿本文にしすぎない
- 読者と切り口が分かるようにする
- 公開してよい情報だけ使う

アイデア:
...
```

## 3. X APIで自動投稿する

X APIを使うと、プログラムから投稿を作成できます。

### 必要なもの

- X Developer Account
- 承認済みのApp
- OAuth 2.0 User Context token
- 投稿に必要なscope
- API利用料金やcreditsの確認

必要scopeの例:

```text
tweet.read
tweet.write
users.read
offline.access
```

`offline.access` はrefresh tokenで継続運用する場合に使います。

## API投稿の最小例

```bash
curl -X POST 'https://api.x.com/2/tweets' \
  -H "Authorization: Bearer $X_USER_ACCESS_TOKEN" \
  -H 'Content-Type: application/json' \
  -d '{
    "text": "Hello from the X API!"
  }'
```

成功すると、投稿IDと本文を含むレスポンスが返ります。

```json
{
  "data": {
    "id": "POST_ID",
    "text": "Hello from the X API!"
  }
}
```

## Safe Automation Flow

```text
X Ideas
  -> X Drafts
  -> Review OK
  -> dry-run
  -> X API post
  -> X Post History
```

守るルール:

- `Review OK` が未チェックの投稿は送信しない
- dry-runで投稿本文を確認する
- 280文字を超える場合は投稿しない、またはスレッド化する
- tokenやsecretはGitHubにcommitしない
- 投稿後はPost ID、URL、Content IDを記録する

## Refresh Token

Access Tokenは期限切れになるため、refresh tokenを使って更新します。

公開ドキュメントには実tokenを書かず、環境変数名だけを記載します。

```text
X_AUTH_MODE=oauth2
X_USER_ACCESS_TOKEN=...
X_REFRESH_TOKEN=...
X_CLIENT_ID=...
X_CLIENT_SECRET=...
X_USERNAME=...
```

## Billing Credits

X APIで `CreditsDepleted` が出る場合は、X Developer ConsoleのBilling / Creditsを確認します。

公開ドキュメントには個別のaccount IDを含むbilling URLを書かないでください。

## 投稿URLの形式

投稿後に取得したIDを使って、Notionには次の形式でURLを保存します。

```text
https://x.com/USER_NAME/status/POST_ID
```

## Official References

- X API Overview: https://docs.x.com/x-api/overview
- X Manage Posts: https://docs.x.com/x-api/posts/manage-tweets/introduction
- X Manage Posts Quickstart: https://docs.x.com/x-api/posts/manage-tweets/quickstart
- X Create or Edit Post: https://docs.x.com/x-api/posts/create-post
