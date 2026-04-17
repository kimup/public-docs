# Directory Structure

公開用と非公開用を分けるための推奨ディレクトリ構造です。

## Public Repository

公開してよいルール、テンプレート、チェックリストを置く。

```text
public-docs/
  codex/
  notion/
  x-content/
```

## Private Workspace

非公開の作業ファイル、API設定、下書き、作業ログを置く。

```text
workspace/
  public-docs/              # 公開リポジトリ
  settings/                 # ローカル設定。公開しない
    notion-local-cli/       # Notion操作用CLIやdocs
    x-api/                  # X API用.envやログ
  codex-knowledge/          # Codex運用知見。公開前に要確認
  skills/                   # workspaceから参照するCodex skill
```

## Knowledge Directory

Codexの知見を残す場合の例。

```text
codex-knowledge/
  incidents/    # エラー、原因、対処
  runbooks/     # 再利用できる手順
  decisions/    # 運用判断
  commands/     # よく使うコマンド
  projects/     # プロジェクト別メモ
  templates/    # 記録用テンプレート
```

## Rule of Thumb

| Content | Place |
|---|---|
| 公開テンプレート | `public-docs/` |
| 公開チェックリスト | `public-docs/` |
| 非公開の投稿下書き | private Notion or private workspace |
| API token | local `.env` only |
| APIエラーの詳細ログ | private workspace |
| 抽象化した運用ルール | `public-docs/` |
