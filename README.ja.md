# OpusNode (TailCamp)

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Status](https://img.shields.io/badge/status-開発中-yellow)
![Version](https://img.shields.io/badge/version-0.1.0-orange)

**技術的な洗練とユーザーフレンドリーなデザインの融合**

[🇰🇷 한국어](README.ko.md) | [🇺🇸 English](README.en.md) | [🇯🇵 日本語](README.ja.md)

---

## 📋 プロジェクト情報

**プロジェクトタイプ**: AI駆動型コラボレーティブ学習プラットフォーム  
**プラットフォーム**: Webアプリケーション  
**アーキテクチャ**: フルスタックモダンWebアプリケーション

---

## 🚀 概要

**OpusNode (TailCamp)**は、断片化された学習リソースを個人化された学習ロードマップに変換し、類似した目標を持つ学習者をマッチングして、コラボレーティブなプロジェクトベースの学習を提供するAI駆動型学習プラットフォームです。各ユーザーは創造のコラボレーティブネットワークのノードとなります。

### コアバリュー提案

* 🎯 **個人化された学習パス**: AIが散在する学習資料を構造化された個人化カリキュラムに変換
* 👥 **インテリジェントなグループマッチング**: AIが類似した目標とスキルレベルの学習者をマッチングして効果的なコラボレーションを提供
* 🚀 **プロジェクトベースの学習**: 実世界のプロジェクト経験と自動ポートフォリオ生成
* 🤖 **AI駆動評価**: AIインタビューを通じた包括的なスキルレベル評価

---

## ✨ 主な機能

### 🧠 AI評価システム
* スキルレベル評価のためのインタラクティブなAIインタビュー
* 視覚的な進捗インジケーターを備えたリアルタイム分析
* 多次元スコアリング（バックエンド、フロントエンド、AI/ML、モバイル、DevOps）
* 個人化された学習推奨

### 👥 スマートグループマッチング
* 目標、レベル、コラボレーションスタイルに基づくAIマッチングアルゴリズム
* 最適なグループサイズ（3-6名）
* 透明なマッチング基準の表示
* 自動グループ形成と管理

### 📚 個人化されたカリキュラム
* 週単位の学習ロードマップ
* 前提条件関係の追跡
* 進捗に基づく適応型学習
* 公開リソースからのコンテンツマッピング

### 🛠️ プロジェクトワークスペース
* コラボレーティブなプロジェクト管理
* タスク割り当てと役割分担
* GitHub統合と自動PR分析
* ガイダンスのためのAIコーチチャットボット

### 🎨 ポートフォリオジェネレーター
* 自動プロジェクト要約
* 技術スタック抽出
* 複数のテンプレートスタイル（Minimal、Dev、Dark、Notion Style）
* PDFおよびWebホスティングエクスポートオプション

### 📊 学習ダッシュボード
* 視覚的インジケーターを備えた進捗追跡
* ゲーミフィケーション要素（レベル、バッジ、連続学習）
* AIタスクアシスタント
* グループプロジェクトステータスモニタリング

---

## 🎯 プロジェクト目標

* ✅ AI駆動スキル評価システムの実装
* ✅ インテリジェントなグループマッチングアルゴリズムの構築
* ✅ 個人化されたカリキュラムジェネレーターの作成
* ✅ コラボレーティブなプロジェクトワークスペースの開発
* ✅ 自動ポートフォリオ生成の有効化
* ✅ モダンでレスポンシブなUI/UXの確保
* ✅ パフォーマンスとスケーラビリティの最適化

---

## 🛠️ 技術スタック

### Frontend
![Next.js](https://img.shields.io/badge/Next.js-14+-black?logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue?logo=typescript)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.0+-38bdf8?logo=tailwind-css)

* **フレームワーク**: Next.js 14+ (App Router)
* **言語**: TypeScript
* **状態管理**: Recoil / Zustand
* **スタイリング**: Tailwind CSS + shadcn/ui
* **リアルタイム**: Socket.io Client

### Backend
![NestJS](https://img.shields.io/badge/NestJS-10.0+-e0234e?logo=nestjs)
![Node.js](https://img.shields.io/badge/Node.js-20+-339933?logo=node.js)

* **フレームワーク**: NestJS
* **言語**: TypeScript
* **API**: GraphQL (Apollo) + REST
* **リアルタイム**: Socket.io
* **タスクキュー**: Bull (Redisベース)

### AI & Data
![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4-412991?logo=openai)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15+-336791?logo=postgresql)
![Redis](https://img.shields.io/badge/Redis-7+-dc382d?logo=redis)

* **LLM**: OpenAI GPT-4 / Anthropic Claude 3.5
* **オーケストレーション**: LangChain / LangGraph
* **ベクトルDB**: Milvus / Pinecone
* **データベース**: PostgreSQL 15+
* **キャッシュ**: Redis 7+

### Infrastructure
![AWS](https://img.shields.io/badge/AWS-S3-232f3e?logo=amazon-aws)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ed?logo=docker)

* **ホスティング**: AWS / Vercel
* **ファイルストレージ**: AWS S3
* **CI/CD**: GitHub Actions

---

## 🏃 クイックスタート

### 前提条件

* **Node.js** 20+ インストール済み
* **PostgreSQL** 15+ インストール済み
* **Redis** 7+ インストール済み
* **npm** または **yarn** パッケージマネージャー

### インストールとセットアップ

1. **リポジトリのクローン**
   ```bash
   git clone <repository-url>
   cd OpusNode
   ```

2. **依存関係のインストール**
   ```bash
   # Frontend
   cd frontend
   npm install
   
   # Backend
   cd ../backend
   npm install
   ```

3. **環境設定**
   ```bash
   # 環境ファイルのコピー
   cp .env.example .env
   # .envを編集して設定
   ```

4. **データベース設定**
   ```bash
   # マイグレーションの実行
   npm run migrate
   ```

5. **アプリケーションの実行**
   ```bash
   # 開発モード
   npm run dev
   ```

6. **アプリケーションへのアクセス**
   ```
   Frontend: http://localhost:3000
   Backend API: http://localhost:4000
   ```

---

## 📁 プロジェクト構造

```
OpusNode/
├── frontend/                 # Next.jsフロントエンドアプリケーション
│   ├── app/                 # App Routerページ
│   ├── components/          # Reactコンポーネント
│   ├── lib/                 # ユーティリティとフック
│   └── public/              # 静的アセット
├── backend/                 # NestJSバックエンドアプリケーション
│   ├── src/
│   │   ├── modules/         # 機能モジュール
│   │   │   ├── assessment/  # AI評価モジュール
│   │   │   ├── matching/    # グループマッチングモジュール
│   │   │   ├── curriculum/  # カリキュラムジェネレーター
│   │   │   ├── projects/    # プロジェクトワークスペース
│   │   │   └── portfolio/   # ポートフォリオジェネレーター
│   │   ├── common/          # 共有ユーティリティ
│   │   └── config/          # 設定
│   └── test/                # テストファイル
├── ai-engine/               # AIサービスレイヤー
│   ├── assessment/          # 評価エンジン
│   ├── matching/            # マッチングアルゴリズム
│   └── curriculum/          # カリキュラムジェネレーター
├── docs/                    # ドキュメント
│   └── plans/               # 設計計画とPRD
└── README.md                # このファイル
```

---

## 🎨 デザインシステム

OpusNodeは、モダンな原則で構築された包括的なデザインシステムを特徴としています：

* 🎯 **コンポーネントベースのアーキテクチャ**: 再利用可能なUIコンポーネント
* 🌈 **デザイントークン**: 一貫したカラーパレットとタイポグラフィ
* 📱 **レスポンシブデザイン**: モバイルファーストアプローチ
* ♿ **アクセシビリティ**: WCAG 2.1 AA準拠
* 🎭 **ダークモード**: 完全なテーマサポート
* ⚡ **パフォーマンス**: 最適化されたアニメーションとローディング状態

---

## 📚 ドキュメント

| 言語 | ドキュメント | 説明 |
|------|------------|------|
| 🇰🇷 | [한국어](README.ko.md) | 韓国語完全ドキュメント |
| 🇺🇸 | [English](README.en.md) | 英語完全ドキュメント |
| 🇯🇵 | [日本語](README.ja.md) | 日本語完全ドキュメント |

### 追加リソース

* [製品要件ドキュメント](docs/plans/TailCamp_PRD.md) - 包括的なPRD
* デザインシステム - 視覚的デザインガイドライン（準備中）
* APIドキュメント - APIエンドポイントリファレンス（準備中）
* 開発ガイド - 開発セットアップとガイドライン（準備中）

---

## 🗓️ 開発ロードマップ

### Phase 1: MVP (1-3ヶ月)
* ✅ AIインタビューと評価システム
* ✅ グループマッチングアルゴリズム
* ✅ 学習ダッシュボード
* ✅ 基本的なプロジェクトワークスペース

### Phase 2: 強化 (4-6ヶ月)
* 🔄 プロジェクトワークスペース（全機能）
* 🔄 AIコーチチャットボット
* 🔄 ポートフォリオジェネレーター
* 🔄 ゲーミフィケーション要素

### Phase 3: スケール (7-12ヶ月)
* 📋 高度なAI機能
* 📋 モバイルアプリ（オプション）
* 📋 コミュニティ機能
* 📋 プレミアム機能

---

## 🤝 貢献

貢献を歓迎します！プルリクエストを自由に提出してください。

1. リポジトリをフォーク
2. 機能ブランチを作成 (`git checkout -b feature/AmazingFeature`)
3. 変更をコミット (`git commit -m 'Add some AmazingFeature'`)
4. ブランチにプッシュ (`git push origin feature/AmazingFeature`)
5. プルリクエストを開く

---

## 📄 ライセンス

このプロジェクトはMITライセンスの下で公開されています。詳細はLICENSEファイルを参照してください。

---

**学習者のために ❤️ で構築**

*各ユーザーが創造のコラボレーティブネットワークのノードとなるモジュール式学習プラットフォーム。*

