# Codex Workflow

Codexを安全に使って、公開用ドキュメント、Notion運用、X投稿ワークフローを整備するための公開用ルールです。

## Goals

- Codexに任せる作業の型を明確にする
- 公開してよい情報と非公開情報を分ける
- NotionやXの運用を再利用できる形にする
- 作業ログ、メモ、下書き、公開物の置き場所を混ぜない

## Documents

- [Operating Rules](./operating-rules.md): Codexに作業を任せるときの基本ルール
- [Directory Structure](./directory-structure.md): 公開/非公開を分けるディレクトリ構造
- [Public / Private Boundary](./public-private-boundary.md): GitHubに置いてよいもの、置かないもの
- [Work Log Template](./templates/work-log-template.md): 作業ログのテンプレート

## Basic Workflow

1. ユーザーが目的を伝える
2. Codexが既存ファイルとルールを確認する
3. 必要なファイルだけ編集する
4. 秘密情報が入っていないか確認する
5. NotionやGitHubなど外部更新がある場合は結果を記録する
6. 不要な一時ファイルや重複ページを整理する

## Safety First

Codexは便利ですが、公開判断は人間が行います。

- 公開前に必ず人間がレビューする
- tokenやsecretはCodexに表示させない
- `.env` はローカルだけに置く
- API投稿や外部公開はdry-runを挟む
