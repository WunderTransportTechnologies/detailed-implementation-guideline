# 技術スタックと制約

## コア技術
- TypeScript: ^5.0.0
- Node.js: ^20.0.0

## フロントエンド
- Next.js: ^15.1.3
- React: ^19.0.0
- Tailwind CSS: ^3.4.17
- shadcn/ui: ^2.1.8

## バックエンド
- Firebase: ^10.5.0
- Firestore: ^10.5.0
- Firebase Authentication: ^10.5.0
- Firebase Cloud Functions: ^10.5.0 (オプション)

## テスト
- Jest: ^29.7.0
- React Testing Library: ^15.0.0
- Cypress: ^13.6.0 (E2Eテスト)

## サポートツール
- ESLint
- Prettier
- husky (git hooks)
- GitHub Actions (CI/CD)

## バージョン管理
- Git
- GitHub

## 技術選定の理由
- **Next.js**: SSRとSSGのサポート、最適化されたパフォーマンス、簡易なルーティング
- **Firebase**: 迅速な開発、スケーラブルなインフラストラクチャ、認証の簡易化
- **TypeScript**: 型安全性、エラーの早期発見、IDEのサポート向上
- **Tailwind CSS**: 迅速なUI開発、カスタマイズ性、小さなバンドルサイズ
- **shadcn/ui**: 再利用可能なコンポーネント、一貫したデザイン、アクセシビリティ

## 注意事項
- 依存関係のバージョンは定期的に更新し、セキュリティパッチを適用すること
- 本番環境への展開前には依存関係の脆弱性チェックを実施すること
- 将来の技術債を最小限に抑えるため、厳格な型定義を維持すること
- サードパーティライブラリの追加は、チームの同意と評価の後に行うこと