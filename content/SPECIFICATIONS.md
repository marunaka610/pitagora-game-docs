# Pitagora Simulator 仕様書

## 1. プロジェクト概要

Pitagora Simulator は、物理現象や音響現象を操作しながら学べるブラウザー向けシミュレーターです。共通の画面構成とページルーティングを用意し、複数のシミュレーションを一つのアプリケーションから利用できるようにします。

### 技術スタック

- TypeScript 7.0.2（strict mode）
- Vite 8.3.2
- Phaser 4.2.1
- Matter.js 0.20.0

## 2. アーキテクチャ

アプリケーションは、ページ選択、共通 UI、シミュレーション固有の実装を分離します。

| 要素 | 役割 |
| --- | --- |
| `src/main.ts` | アプリケーションの起動とルートコンポーネントのマウント |
| `src/App.tsx` | URL に応じたページ選択と画面遷移 |
| `src/components/HamburgerMenu.ts` | ナビゲーションメニューの表示、選択、閉じる操作 |
| `src/components/SimulationContainer.ts` | シミュレーション共通のレイアウトとシーン表示領域 |
| シミュレーションの Scene / Controls | 現象の描画、シミュレーション状態、操作 UI |

共通コンテナは選択中のシミュレーションに対応する Scene と Controls を配置します。シミュレーションを切り替えるときは、前の Scene を破棄してから遷移先の Scene を読み込み、イベントや描画リソースを残さないようにします。

## 3. シミュレーション

シミュレーションごとの目的、表示、操作、状態遷移を個別ページに定めます。共通の画面構成とルーティングは本書、シミュレーション固有の仕様は以下を参照してください。

- **3.1 [物体落下（Drop Simulation）](specifications/simulations/drop.md):** 既存の落下シミュレーションを共通コンテナへ統合します。
- **3.2 [音波フーリエ解析（Audio Fourier Analysis）](specifications/simulations/audio-fourier.md):** 入力信号の波形と周波数成分を比較します。
- **3.3 [共鳴現象（Resonance Phenomenon）](specifications/simulations/resonance.md):** 外力の周期と系の応答の関係を観察します。

## 4. ルーティング

ページ遷移は URL に反映し、ブラウザーの戻る・進む操作でも現在のページを復元します。

| URL | ページ |
| --- | --- |
| `/` | [Drop Simulation](specifications/simulations/drop.md) |
| `/audio` | [Audio Fourier Analysis](specifications/simulations/audio-fourier.md) |
| `/resonance` | [Resonance Phenomenon](specifications/simulations/resonance.md) |
| `/#/settings` | Settings |
| `/#/about` | About |

Settings と About はハッシュルートを使用します。未知のパスでは Drop Simulation にフォールバックします。ページ遷移時は対応する内容を表示し、シミュレーションページでは選択した Scene を読み込みます。

## 5. UI / UX

### 5.1 ハンバーガーメニュー

- 左上に `☰` ボタンを配置し、クリックまたはキーボード操作でメニューを開閉します。
- メニューは画面左からスライドインします。
- 以下の項目をこの順序で表示します。
  1. Drop Simulation
  2. Audio Fourier Analysis
  3. Resonance Phenomenon
  4. 区切り線
  5. Settings
  6. About
  7. Documentation（Zensical サイト）
- 現在のページを視覚的に強調し、現在位置を支援技術にも伝えます。
- 項目を選択すると対応するページへ移動してメニューを閉じます。
- パネル外のクリック、Escape キー、メニュー項目の選択で閉じます。
- 開いている間はフォーカスをメニュー内に保ち、閉じたときは起動ボタンへ戻します。
- モバイル画面でも操作できる十分なボタン領域を確保します。

### 5.2 シミュレーション共通レイアウト

- 画面上部のおよそ 60〜70% を Canvas、下部のおよそ 30〜40% をパラメーター操作パネルに割り当てます。
- ハンバーガーメニューはすべてのページから利用できます。
- 画面サイズに応じて領域を調整し、操作パネルや Canvas が画面外にはみ出さないようにします。
- モバイルでは操作パネルを縦に並べ、タブレット・PC では画面幅に合わせて配置を調整します。

## 6. 実装フェーズ

1. **共通フレームワーク** — ハンバーガーメニュー、ルーティング、共通コンテナを実装し、[物体落下シミュレーション](specifications/simulations/drop.md)を統合する。
2. **音波フーリエ解析** — [個別仕様](specifications/simulations/audio-fourier.md)に従って入力・解析・可視化を実装し、共通コンテナに組み込む。
3. **共鳴現象** — [個別仕様](specifications/simulations/resonance.md)に従ってモデル、操作項目、可視化を実装する。
4. **仕上げ** — レスポンシブ表示、キーボード操作、各画面の動作を確認する。

## 7. 技術上の検討事項

- Scene の生成・破棄と、ページ遷移時のイベント／リソース解放
- URL と表示中ページの同期、および未知の URL の扱い
- Canvas と操作パネルの領域配分、狭い画面での表示
- メニューのキーボード操作、フォーカス管理、現在ページのアクセシビリティ表現
- 音波解析と共鳴シミュレーションで用いる具体的な数理モデル・操作パラメーター
- `CODING_CONVENTIONS.md` がアプリケーションリポジトリに存在する場合は、その規約に従うこと
