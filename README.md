# 増井 友紀 / Yuki Masui

生産技術として設備設計・制御業務に従事しています。
**現場で「これがあれば楽になる」と感じたものを、自宅環境で実際に作って検証しています。**
このアカウントはその成果の置き場です。

---

## 主なプロジェクト

### [ymcad](https://github.com/yukimasui/ymcad) — 2D CAD アプリケーション

[![CI](https://github.com/yukimasui/ymcad/actions/workflows/ci.yml/badge.svg)](https://github.com/yukimasui/ymcad/actions/workflows/ci.yml)
![Rust](https://img.shields.io/badge/Rust-000000?logo=rust&logoColor=white)
![egui](https://img.shields.io/badge/egui-2E2E2E)

![ymcad の画面](https://raw.githubusercontent.com/yukimasui/ymcad/main/docs/images/screenshot.png)

AutoCAD ライクな操作性を持つ 2D 専用 CAD。Rust + egui 製、Ubuntu ネイティブ。

**作った理由** — 仕事では 2D CAD を日常的に使いますが、趣味で使うには市販ソフトは
**高すぎ、そして高機能すぎました。** かといって無償 CAD へ移ると操作の癖を覚え直すコストがかかります。
そこで **AI エージェントによる開発で、自分に必要な機能だけをコンパクトに作る**方針にしました。
機能の取捨選択を自分で握れるなら、「高すぎる」も「高機能すぎる」も同時に解けます。

- 作図 / 編集 / 選択 / オブジェクトスナップ / レイヤ / Undo・Redo
- TRIM・EXTEND・FILLET・CHAMFER、コンポーネント（定義 + インスタンス）のインプレース編集
- ダイナミックブロックの「アクション」を**テキストの式**に置き換え（識別子に日本語が使える）
- ネイティブ形式 `.ymc`（無損失）と DXF R12（交換用）の入出力

**設計面で意識したこと** — エージェントに実装を任せる以上、壊れてはいけない不変条件を
文章の規約ではなく **CI の機械検査**で守っています（コアの依存方向、`f64` 一貫、
`as f32` の局所化、トレランスの直書き禁止）。エンティティの変更経路も型で 1 本に絞っています。
ファイル入出力は、往復テストの盲点を埋めるために **Rust とは別実装の Python 検証スクリプト**を
CI で走らせています。

`約 38,000 行 / テスト 1,029 件 / ADR 33 件 / コアの依存パッケージ 0`

---

### [Team Timeline](https://github.com/yukimasui/team-timeline) — チーム進捗管理ツール

![Rust](https://img.shields.io/badge/Rust-000000?logo=rust&logoColor=white)
![Axum](https://img.shields.io/badge/Axum-000000)
![React](https://img.shields.io/badge/React-20232A?logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?logo=sqlite&logoColor=white)

![Team Timeline のスクリーンショット](https://github.com/user-attachments/assets/cef555ec-0eab-4293-a737-8bd04271d37e)

チームの誰がいま何をやっているかをひと目で把握するための進捗管理ツール。
**Excel での進捗管理を置き換える**目的で作りました。業務固有の要素は含まない汎用ツールです。

- **タイムライン** — ガント風。バーはドラッグで日付をスライド／リサイズでき、依存関係は矢印で表示
- **カンバン** — ステータス別ボード / **テーブル** — 一覧表示
- Axum が React のビルド成果物の配信と API を兼ねる**単一コンテナ構成**。`docker compose up` だけで動く
- データは 1 ファイルの SQLite に永続化

---

### [my-home_laundry-done-notifier](https://github.com/yukimasui/my-home_laundry-done-notifier) — 洗濯終了通知

![ESP32](https://img.shields.io/badge/ESP32-E7352C)
![Rust](https://img.shields.io/badge/Rust-000000?logo=rust&logoColor=white)
![MQTT](https://img.shields.io/badge/MQTT-660066?logo=mqtt&logoColor=white)

洗濯機の終了音を ESP32 で検知し、MQTT を介して KIOSK 端末へ通知するシステム。

- ESP32 / FFT / MQTT / Rust / Slint / Ubuntu Server
- 🚧 開発中（FFT による洗濯中ノイズ由来の誤作動を対策中）

---

### [stm32-modbus-remote-io_for-robot](https://github.com/yukimasui/stm32-modbus-remote-io_for-robot) — 外部配線レス構想

![STM32](https://img.shields.io/badge/STM32-03234B?logo=stmicroelectronics&logoColor=white)
![Modbus](https://img.shields.io/badge/Modbus%20RTU-555555)

産業用ロボットの**機内配線**を活用し、外部配線を追加せずにリモート IO を Modbus で実現する構想。
ロボット立ち上げ時にクイックチェンジャーからの配線をまとめ、動作を考えてたるみを調整する手間が
きっかけです。

- 💡 構想段階（業務に関わる内容のため、公開しているのは構想と想定構成まで）

---

## スキル

### CAD
- **2D** — AutoCAD, IJCAD
- **3D** — CATIA, Autodesk Inventor, SolidWorks（個人向けライセンス）

### 加工・製造
- **汎用工作機械** — 旋盤, フライス盤, 研削盤
- **NC 工作機械** — 旋盤, フライス盤, ワイヤ放電加工機

### 電気・制御
- 制御盤製作（第二種電気工事士 合格）
- ラダー回路設計（主に KEYENCE）
- ロボットティーチング — FANUC, 川崎重工, 不二越, DENSO

### ソフトウェア（個人プロジェクトで使用）
- **言語** — Rust, TypeScript, Python
- **フロントエンド** — React, Vite, Tailwind CSS
- **バックエンド・基盤** — Axum, SQLite, Docker, GitHub Actions
- **GUI** — egui, Slint
- **組み込み** — ESP32（Rust）, MQTT
- **開発環境** — Ubuntu, Git, AI エージェントを使った開発（Claude Code）
