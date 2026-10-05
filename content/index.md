# ピタゴラゲーム ドキュメント

ピタゴラゲームのルール、複数のシミュレーションを提供するアプリの仕様、および関連リポジトリ間の開発フローをまとめたドキュメントです。

## ドキュメント

### ゲーム仕様

- [仕様書の概要](specifications/index.md): ゲーム概要、遊び方、ステージ構成・進行、共通仕様

### シミュレーター仕様

- [全体仕様](SPECIFICATIONS.md): アプリケーションの構成、シミュレーション一覧、ルーティング、共通 UI
- 個別ページ: [物体落下](specifications/simulations/drop.md)、[音波フーリエ解析](specifications/simulations/audio-fourier.md)、[共鳴現象](specifications/simulations/resonance.md)

### 開発フロー

- [リポジトリ間の開発フロー](development-flow.md): `pitagora-game-docs`、`pitagora-game-infra`、`pitagora-game-front` 間の進め方

各ページの「要確認」は、プロダクト上の決定が必要な項目です。実装済みの挙動と混同しないよう、合意・実装後に内容を更新してください。
