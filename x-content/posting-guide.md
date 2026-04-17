# How to Post to X

Xへ投稿する方法を、手動、半自動、API自動化の3段階で整理します。

## 1. 手動で投稿する

最初はこの方法が安全です。

### 手順

1. `x-content/templates/` のテンプレートを使って投稿案を作る
2. `x-content/publishing-checklist.md` で公開前チェックをする
3. Notionの `X Content Pipeline` に登録する
4. `Status` を `Review` にする
5. 問題なければ `Scheduled` または `Published` にする
6. Xの投稿画面に本文を貼り付けて投稿する
7. 投稿後、Notionに `X URL` を記録する

## 2. Codexで投稿本文を作る

Codexに投稿案を作らせ、投稿自体は人間が行います。

### 1投稿のプロンプト

```text
以下のメモをXの1投稿にしてください。

条件:
- 1つの主張に絞る
- 外部公開してよい情報だけ使う
- 冒頭で読者の関心を作る
- 誇張しない
- 投稿前チェック項目も最後に出す

メモ:
...
```

### スレッドのプロンプト

```text
以下の内容をXのスレッドにしてください。

条件:
- 5から8投稿
- 1投稿目はテーマと読む価値を明確にする
- 各投稿は1メッセージに絞る
- 内部情報、秘密情報、個人情報は含めない
- 最後に関連リンクか次の行動を入れる

内容:
...
```

## 3. X APIで自動投稿する

X APIを使うと、プログラムから投稿を作成できます。

### 必要なもの

- X Developer Account
- 承認済みのApp
- User Access Token
- 投稿に必要な権限
- API利用料金や制限の確認

X APIは投稿作成に `POST /2/tweets` を使います。公式ドキュメントでは、認証済みユーザーとして投稿を作成・削除できるManage Posts系エンドポイントとして説明されています。

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

## スレッド投稿の考え方

スレッドは、2投稿目以降を直前の投稿への返信として作ります。

```text
1. 1投稿目をPOST /2/tweetsで作成
2. レスポンスの data.id を取得
3. 2投稿目を reply.in_reply_to_tweet_id に1投稿目のIDを入れて作成
4. 以降、直前の投稿IDに返信する形で続ける
```

### スレッド2投稿目の例

```bash
curl -X POST 'https://api.x.com/2/tweets' \
  -H "Authorization: Bearer $X_USER_ACCESS_TOKEN" \
  -H 'Content-Type: application/json' \
  -d '{
    "text": "2つ目の投稿です。",
    "reply": {
      "in_reply_to_tweet_id": "FIRST_POST_ID"
    }
  }'
```

## 自動化するときの流れ

```text
公開ドキュメント or メモ
  -> Codexで投稿案生成
  -> NotionのX Content Pipelineへ登録
  -> Review OKを人間が確認
  -> X APIで投稿
  -> 投稿IDとURLをNotionへ記録
```

## 自動投稿で守るルール

- `Review OK` が未チェックの投稿は送信しない
- SecretやTokenはGitHubにcommitしない
- 投稿直前に公開前チェックを必ず走らせる
- APIで投稿した本文、投稿ID、投稿URLをNotionに記録する
- まずは自動投稿ではなく「下書き生成」から始める

## 投稿URLの形式

投稿後に取得したIDを使って、Notionには次の形式でURLを保存します。

```text
https://x.com/USER_NAME/status/POST_ID
```

## 公式リファレンス

- X API Overview: https://docs.x.com/x-api/overview
- X Manage Posts: https://docs.x.com/x-api/posts/manage-tweets/introduction
- X Manage Posts Quickstart: https://docs.x.com/x-api/posts/manage-tweets/quickstart
- X Create or Edit Post: https://docs.x.com/x-api/posts/create-post
