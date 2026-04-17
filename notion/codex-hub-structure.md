# Codex Hub Structure

CodexとNotionを連携して使う場合の推奨構成です。

## Top Level

```text
Codex Hub
  メモ
  Codex作業ログ
  X Ideas
  X Drafts
  X Post History
  Drafts
  Private Docs
  Ideas
```

## メモ

短い運用メモ、外部URL、API課金・設定メモを置く場所。

置くもの:

- API billingやcreditsの確認先
- OAuth設定時の注意点
- 「X投稿ができるまで」のような短い手順メモ
- 調査中に残しておきたい小さな運用メモ

置かないもの:

- tokenやsecret
- `.env` の値
- 作業履歴の詳細
- 長い下書き本文

## Codex作業ログ

Codexが行った実作業を記録する場所。

推奨DB名:

```text
作業ログDB
```

記録するもの:

- 作業日
- 作業タイトル
- 変更内容
- 触ったファイル
- 作成・更新したNotionページ
- GitHubへpushした場合のcommitやURL
- 未完了の次アクション

## X Ideas / X Drafts / X Post History

X投稿は3つのデータベースで分ける。

```text
X Ideas        # 投稿前アイデア
X Drafts       # 投稿前本文、レビュー状態
X Post History # 投稿後URL、結果、学び
```

同じ投稿に関係するレコードは、共通の `Content ID` で結びつける。

例:

```text
X-YYYYMMDD-001
```

## Drafts

X以外も含めた文章下書きの置き場。

例:

- 記事の下書き
- 複数案
- 公開前のメモ
- NotionやGitHubへ移す前の素材

## Private Docs

公開しないドキュメントの置き場。

例:

- 内部運用メモ
- 非公開の設計メモ
- 公開前の判断材料

ただし、tokenやpasswordはPrivate Docsにも書かず、ローカル `.env` やsecret managerで管理する。

## Naming Rule

CodexがNotionページや主要見出しを作成・更新するときは、日本語タイトルを優先する。

| Use | Title |
|---|---|
| メモ置き場 | メモ |
| Codex作業履歴 | Codex作業ログ |
| Work log database | 作業ログDB |
| Hub guide | Codex Hubガイド |

X固有のDB名は、運用上分かりやすい場合は英語名を維持してよい。
