# pitagora-game-docs

## ドキュメント運用

- `develop` への push で Zensical をビルドし、生成物を `develop` の `docs/` にコミットします。GitHub Pages の公開元は `develop` ブランチの `/docs` に設定してください。
- `main` を対象とするプルリクエストがマージされると、変更ファイルごとに issue を作成します。`content/` の変更は `marunaka610/pitagora-game-front`、Actions・ビルド設定の変更は `marunaka610/pitagora-game-infra` が対象です。生成物 `docs/` の変更は除外します。

Issue 作成には、両リポジトリの Issues 書き込み権限を持つ fine-grained personal access token を `CROSS_REPO_ISSUES_TOKEN` という Actions secret として登録してください。