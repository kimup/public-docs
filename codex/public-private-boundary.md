# Public / Private Boundary

公開用リポジトリに置いてよいもの、置かないものの境界です。

## Public OK

- 抽象化した運用ルール
- 公開用テンプレート
- 公開前チェックリスト
- NotionやXの一般的なワークフロー
- 環境変数名だけの例
- 実値を含まないCLI例
- 公開済みURL

## Private Only

- `.env` の中身
- API token / refresh token
- Notion integration token
- X API key / client secret
- 実際のNotion page/database ID
- 実際のX account IDやbilling URL
- 非公開の投稿下書き
- 作業ログの詳細
- 個人情報、顧客情報、内部URL

## Before Publishing

公開前に以下を確認する。

- [ ] tokenやsecretがない
- [ ] 個別のNotion IDやX account IDがない
- [ ] ローカル絶対パスが不要に含まれていない
- [ ] 非公開の下書きや作業ログを含んでいない
- [ ] 外部読者に伝えてよい抽象度になっている
