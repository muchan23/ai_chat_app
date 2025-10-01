# AI Chat Application

ChatGPTのような機能を持つWebベースのチャットアプリケーションです。

## 🚀 機能概要

### 主要機能
- **リアルタイムチャット** - OpenAI GPT APIを使用したAIとの対話
- **会話管理** - 会話履歴の保存・検索・管理
- **ファイルアップロード** - 画像・PDF・テキストファイルのアップロード
- **ユーザー認証** - メール認証・Google OAuth連携
- **カスタマイズ** - ダークモード・テーマ設定

### AI機能
- **ストリーミング応答** - リアルタイムでAI応答を表示
- **コンテキスト保持** - 会話履歴を考慮した応答
- **モデル選択** - GPT-3.5、GPT-4などのモデル選択
- **プロンプト設定** - システムプロンプトのカスタマイズ

## 🛠 技術スタック

### フロントエンド
- **Next.js 14** - React フレームワーク（App Router）
- **TypeScript** - 型安全な開発
- **Tailwind CSS** - ユーティリティファーストCSS
- **shadcn/ui** - モダンなUIコンポーネント
- **Zustand** - 軽量な状態管理

### バックエンド
- **Next.js API Routes** - サーバーサイドAPI
- **Prisma** - 型安全なORM
- **PostgreSQL** - リレーショナルデータベース
- **NextAuth.js** - 認証ライブラリ

### 外部サービス
- **OpenAI GPT API** - AI応答生成
- **Google OAuth** - ソーシャルログイン
- **AWS S3** - ファイルストレージ
- **Vercel** - デプロイメント

## 📁 プロジェクト構造

```
ai_chat_app/
├── src/
│   ├── app/                    # Next.js App Router
│   │   ├── api/                # API Routes
│   │   ├── auth/               # 認証ページ
│   │   ├── chat/               # チャットページ
│   │   └── settings/           # 設定ページ
│   ├── components/             # Reactコンポーネント
│   │   ├── chat/              # チャット関連コンポーネント
│   │   ├── ui/                # 基本UIコンポーネント
│   │   └── auth/              # 認証関連コンポーネント
│   ├── lib/                   # ユーティリティ・設定
│   │   ├── auth.ts            # 認証設定
│   │   ├── prisma.ts          # データベース接続
│   │   └── openai.ts          # OpenAI API設定
│   ├── types/                 # TypeScript型定義
│   └── stores/                # 状態管理
├── prisma/                    # データベーススキーマ
├── public/                    # 静的ファイル
└── docs/                      # ドキュメント
```

## 🚀 セットアップ

### 前提条件
- Node.js 18.0以上
- npm または yarn
- PostgreSQL データベース
- OpenAI API キー

### インストール

1. **リポジトリのクローン**
```bash
git clone <repository-url>
cd ai_chat_app
```

2. **依存関係のインストール**
```bash
npm install
```

3. **環境変数の設定**
```bash
cp .env.example .env.local
```

`.env.local`ファイルを編集：
```env
# データベース
DATABASE_URL="postgresql://username:password@localhost:5432/ai_chat_app"

# NextAuth
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET="your-secret-key"

# OpenAI
OPENAI_API_KEY="your-openai-api-key"

# Google OAuth
GOOGLE_CLIENT_ID="your-google-client-id"
GOOGLE_CLIENT_SECRET="your-google-client-secret"

# AWS S3
AWS_ACCESS_KEY_ID="your-aws-access-key"
AWS_SECRET_ACCESS_KEY="your-aws-secret-key"
AWS_S3_BUCKET="your-s3-bucket"
```

4. **データベースのセットアップ**
```bash
npx prisma generate
npx prisma db push
```

5. **開発サーバーの起動**
```bash
npm run dev
```

アプリケーションは `http://localhost:3000` で起動します。

## 📚 使用方法

### 基本的な使い方

1. **アカウント作成・ログイン**
   - メールアドレスとパスワードでアカウント作成
   - またはGoogleアカウントでログイン

2. **新しい会話を開始**
   - 「新しい会話」ボタンをクリック
   - メッセージを入力してAIと対話

3. **会話の管理**
   - サイドバーで会話履歴を確認
   - 会話の検索・削除・エクスポート

4. **設定のカスタマイズ**
   - AIモデルの選択
   - テーマの変更
   - 通知設定

### 高度な機能

- **ファイルアップロード**: 画像やPDFをアップロードしてAIに分析
- **プロンプト設定**: システムプロンプトでAIの応答スタイルを調整
- **会話のエクスポート**: 会話履歴をJSONやPDFで保存

## 🔧 開発

### 開発環境のセットアップ

```bash
# 依存関係のインストール
npm install

# データベースのマイグレーション
npx prisma migrate dev

# 開発サーバーの起動
npm run dev

# 型チェック
npm run type-check

# リント
npm run lint

# ビルド
npm run build
```

### テスト

```bash
# ユニットテスト
npm run test

# E2Eテスト
npm run test:e2e
```

## 📊 データベース設計

### 主要テーブル

- **users** - ユーザー情報
- **conversations** - 会話情報
- **messages** - メッセージ情報
- **files** - アップロードファイル情報
- **settings** - ユーザー設定

### リレーション

```
users (1) ──→ (N) conversations
conversations (1) ──→ (N) messages
users (1) ──→ (1) settings
messages (1) ──→ (N) files
```

## 🔒 セキュリティ

- **認証**: JWT トークンベース認証
- **データ保護**: HTTPS通信、パスワードハッシュ化
- **入力検証**: 全入力値の検証・サニタイゼーション
- **API保護**: レート制限、CSRF対策

## 🚀 デプロイ

### Vercel（推奨）

```bash
# Vercel CLIのインストール
npm i -g vercel

# デプロイ
vercel

# 本番環境の環境変数を設定
vercel env add
```

### その他のプラットフォーム

- **AWS**: Amplify、ECS、Lambda
- **Google Cloud**: Cloud Run
- **Azure**: App Service

## 📈 パフォーマンス

- **ページ読み込み**: 3秒以内
- **メッセージ送信**: 1秒以内
- **AI応答開始**: 2秒以内
- **同時接続**: 1000ユーザー対応

## 🤝 コントリビューション

1. このリポジトリをフォーク
2. フィーチャーブランチを作成 (`git checkout -b feature/amazing-feature`)
3. 変更をコミット (`git commit -m 'Add amazing feature'`)
4. ブランチにプッシュ (`git push origin feature/amazing-feature`)
5. プルリクエストを作成

## 📄 ライセンス

このプロジェクトはMITライセンスの下で公開されています。詳細は[LICENSE](LICENSE)ファイルを参照してください。

## 📞 サポート

- **Issues**: [GitHub Issues](https://github.com/your-repo/issues)
- **Discussions**: [GitHub Discussions](https://github.com/your-repo/discussions)
- **Email**: support@example.com

## 🙏 謝辞

- [OpenAI](https://openai.com/) - GPT API
- [Next.js](https://nextjs.org/) - React フレームワーク
- [Vercel](https://vercel.com/) - デプロイメントプラットフォーム
- [Tailwind CSS](https://tailwindcss.com/) - CSS フレームワーク