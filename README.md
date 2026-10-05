# pitagora-game-docs

## ドキュメント運用

- `develop` への push で Zensical をビルドし、生成物を `docs/` にコミットします。Pages へのデプロイは行いません。
- `main` を対象とするプルリクエストがマージされると、生成物 `docs/` を除く差分のキーワードから関連領域を判定し、インフラ関連の変更は `marunaka610/pitagora-game-infra`、機能実装関連の変更は `marunaka610/pitagora-game-front` に issue を作成します。差分に両方の種類があれば、両方に作成します。

Issue 作成には、両リポジトリの Issues 書き込み権限を持つ fine-grained personal access token を `CROSS_REPO_ISSUES_TOKEN` という Actions secret として登録してください。