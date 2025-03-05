# プロジェクト構造規約

## ディレクトリ構造

```
new/
├── .env                     # 環境変数（本番用、gitignore対象）
├── .env.local               # ローカル環境変数（開発用、gitignore対象）
├── .env.example             # 環境変数のテンプレート（gitignore対象外）
├── README.md                # プロジェクト概要と実装計画・進捗状況
├── src/
│   ├── app/                 # ページコンポーネント
│   │   └── api/            # APIルート (必要な場合)
│   ├── components/          # 再利用可能なコンポーネント
│   │   ├── ui/             # 基本UI要素
│   │   └── layout/         # レイアウトコンポーネント
│   ├── lib/                # ユーティリティ関数とヘルパー
│   │   ├── firebase/       # Firebase初期化と設定
│   │   │   ├── config.ts  # Firebase設定（環境変数を参照）
│   │   │   ├── auth/      # 認証関連の処理
│   │   │   └── firestore/ # Firestoreアクセス関数
│   │   └── utils/          # 汎用ユーティリティ
│   ├── types/              # TypeScript型定義
│   ├── styles/             # グローバルスタイル
│   ├── usecases/           # ユースケースの実装
│   └── tests/              # テストファイル
│       ├── unit/           # 単体テスト
│       ├── integration/    # 統合テスト
│       └── e2e/            # E2Eテスト
├── firebase/               # Firebaseの設定と関数
│   ├── firestore.rules     # Firestoreセキュリティルール
│   └── functions/          # Cloud Functions (オプション)
└── public/                 # 静的アセット
```

## ディレクトリの役割と命名規則

### `/src/app/`
- App Routerを使用したページコンポーネントを配置
- ルートディレクトリ構造がURLパスに対応
- 例: `/src/app/dashboard/page.tsx` → `/dashboard` のURLに対応
- 各ページディレクトリには `page.tsx` を含める
- レイアウトは `layout.tsx` で定義
- ローディング状態は `loading.tsx` で定義
- エラー状態は `error.tsx` で定義

### `/src/app/api/`
- サーバーサイドAPIルートを配置
- 例: `/src/app/api/users/route.ts` → `/api/users` のエンドポイントに対応
- 基本的にはFirebaseを直接利用し、自前のAPIは最小限にする

### `/src/components/`
- 再利用可能なReactコンポーネントを配置
- 機能やドメインではなくUI要素としての役割ごとに分類
- コンポーネント名はPascalCaseで記述（例: `Button.tsx`）

#### `/src/components/ui/`
- 基本的なUI要素（ボタン、フォーム要素、カードなど）
- できるだけ汎用的で再利用可能なものを配置
- shadcn/uiコンポーネントはここに配置

#### `/src/components/layout/`
- ページレイアウトに関わるコンポーネント
- ヘッダー、フッター、サイドバー、モーダルなど
- 複数のページで使用される構造的要素

### `/src/lib/`
- 再利用可能なユーティリティ関数やサービスを配置
- 具体的なビジネスロジックではなく汎用的な機能

#### `/src/lib/firebase/`
- Firebase関連の初期化と設定
- 各種Firebaseサービスへのアクセスラッパー

##### `/src/lib/firebase/config.ts`
- Firebase初期化とアプリ設定

##### `/src/lib/firebase/auth/`
- 認証関連のヘルパー関数
- ユーザー管理機能

##### `/src/lib/firebase/firestore/`
- Firestoreアクセス関数
- コレクション操作のラッパー

#### `/src/lib/utils/`
- 汎用的なユーティリティ関数
- 日付操作、文字列処理、数値計算など

### `/src/types/`
- プロジェクト全体で使用するTypeScript型定義
- モデル定義、API型、レスポンス型など
- ファイル名は明確に役割を示す（例: `user-types.ts`）

### `/src/styles/`
- グローバルなCSS定義
- Tailwindの設定ファイル
- テーマ設定

### `/src/usecases/`
- ビジネスロジックの実装
- 特定のユースケースに基づく処理
- コンポーネントから抽出された複雑なロジック

### `/src/tests/`
- テストファイル
- ファイル名は対象ファイル名 + `.test.ts(x)` または `.spec.ts(x)`

### `/firebase/`
- Firebaseの設定ファイル
- デプロイに必要な設定

### `/public/`
- 静的アセット（画像、フォント、マニフェストなど）
- Next.jsが自動的に処理

## ファイル命名規則

- **React Components**: PascalCase（例: `UserCard.tsx`）
- **Utility Functions**: camelCase（例: `formatDate.ts`）
- **Type Definitions**: kebab-case（例: `user-types.ts`）
- **Constants**: SNAKE_CASE（例: `API_ENDPOINTS.ts`内の定数）
- **CSS Modules**: コンポーネント名.module.css（例: `Button.module.css`）
- **Test Files**: 対象ファイル名 + `.test.ts(x)` または `.spec.ts(x)`

## インポート順序

ファイル内のインポート順序は以下の通りとする:
1. 外部ライブラリ (React, Next.js, Firebase など)
2. 内部コンポーネント
3. ユーティリティ関数
4. 型定義
5. スタイルシート

## 環境変数

- プロジェクトで使用する環境変数は `.env.example` に記載し、説明を添える
- 実際の値は `.env.local`（開発用）または `.env`（本番用）に記載
- 環境変数は `NEXT_PUBLIC_` プレフィックスを適切に使用
- 秘密鍵は常に非公開環境変数として設定