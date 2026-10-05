# ピタゴラゲーム ドキュメント

ピタゴラゲームのルール、シミュレーションの仕様、Pitagora Simulator の実装ガイド、および関連リポジトリ間の開発フローをまとめたドキュメントです。

## ドキュメント

### ゲーム仕様

- [概要](game/1-game-overview.md)、[遊び方](game/2-gameplay.md)、[ステージ構成](game/3-1-stage-structure.md)、[プレイの進行](game/3-2-play-progression.md)、[クリアと結果](game/3-3-clear-and-results.md)、[共通仕様](game/common-specifications.md)

### シミュレーション仕様

- [物体落下](specifications/simulations/drop.md)、[音波フーリエ解析](specifications/simulations/audio-fourier.md)、[共鳴現象](specifications/simulations/resonance.md)

### 実装ガイド

- [Pitagora Simulator フレームワーク](implementation-guide.md): アプリケーションの構成、ルーティング、共通 UI

### 開発フロー

- [リポジトリ間の開発フロー](development-flow.md): `pitagora-game-docs`、`pitagora-game-infra`、`pitagora-game-front` 間の進め方

各ページの「要確認」は、プロダクト上の決定が必要な項目です。実装済みの挙動と混同しないよう、合意・実装後に内容を更新してください。
