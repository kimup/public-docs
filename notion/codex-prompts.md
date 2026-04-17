# Codex Prompts

Notionや公開用ドキュメントを作成・レビューするときに使うプロンプト例です。

## 公開用ドキュメント作成

```text
公開用ドキュメントをMarkdownで作成してください。

条件:
- 外部公開してよい内容だけを書く
- APIキー、内部URL、個人情報、顧客情報は書かない
- Notionにも貼りやすい見出し構成にする
- 最後に公開前チェック観点を簡単にまとめる
```

## Notionメモ作成

```text
以下の内容をNotionの「メモ」配下に置く短い運用メモとして整理してください。

条件:
- タイトルは日本語を優先する
- tokenやsecretは書かない
- 外部URLは公開してよいものだけ使う
- 手順、注意点、次回確認ポイントを分ける

内容:
...
```

## Codex作業ログ作成

```text
以下の作業内容を「Codex作業ログ / 作業ログDB」に記録する形式でまとめてください。

出力:
- 作業タイトル
- 日付
- Summary
- Files
- Notion updates
- GitHub updates
- Next actions

条件:
- tokenやsecretは書かない
- 変更したファイルと作成したページを明確にする
```

## 公開前レビュー

```text
このドキュメントを公開前レビューしてください。

観点:
- 秘密情報が含まれていないか
- 個人情報や顧客情報が含まれていないか
- 内部運用やセキュリティ詳細を出しすぎていないか
- 外部の読者にとって分かりやすいか

出力:
- 公開可否: OK / NG / 要修正
- 問題箇所
- 修正案
```

## Notion登録用要約

```text
このMarkdownをNotionのDocs Databaseに登録するため、以下を作成してください。

- Name
- Category
- Status
- Tags
- Summary
- Source Path
- GitHub URL
- Last Reviewed
```
