# ステップバイステップの実装アプローチガイド

このガイドでは、タスクを確実に実装するためのステップバイステップのアプローチを説明します。各タスクはこの共通のアプローチに従って実装することで、一貫性のある高品質な成果物を効率的に提供することができます。

## 1. タスク準備フェーズ

タスクに取り掛かる前に、タスクの内容を理解し、適切な準備を行うことが重要です。

### 1.1 タスクの詳細確認

- **タスク説明とユースケースを再確認**
  - タスクの説明を詳細に読み、目的と範囲を理解する
  - 関連するユースケースやビジネス要件を確認する
  - 不明点があれば、タスク作成者や技術リードに質問する

- **入力と出力の要件を明確化**
  - タスクが受け取る入力データや条件を特定する
  - タスクが生成すべき出力や成果物を明確にする
  - 入出力のフォーマットや制約を確認する

- **依存関係を確認**
  - タスクの前提条件となる他のタスクや成果物を確認する
  - 依存するコンポーネントやサービスの状態を確認する
  - 外部APIやサービスの制限やドキュメントを確認する

- **完了基準を理解**
  - タスクの成功を判断する明確な基準を確認する
  - レビュー時に評価される品質基準を理解する
  - 必要なテストカバレッジや性能要件を確認する

### 1.2 実装計画の作成

- **具体的な実装ステップを列挙**
  - タスクを小さな実装ステップに分解する
  - ステップ間の論理的な順序を定義する
  - 各ステップの見積もり時間を設定する

- **必要なテストを特定**
  - 単体テストのケースを計画する
  - 統合テストの必要性を検討する
  - エッジケースやエラーケースを特定する

- **影響範囲を確認**
  - タスクが影響を与える可能性のある他のコンポーネントを特定する
  - 既存機能への影響を評価する
  - 非機能要件（パフォーマンス、セキュリティなど）への影響を検討する

- **見積もり時間を検証**
  - 実装ステップの合計時間を計算する
  - 過去の類似タスクとの比較による妥当性確認
  - リスクファクターを考慮した余裕を持たせる

### 1.3 作業環境の準備

- **最新のコードベースを取得**
  - リモートリポジトリから最新のコードをプル
  - 適切なブランチから派生させる
  - マージ競合がないことを確認する

- **専用のフィーチャーブランチを作成**
  - 命名規則に従ったブランチ名を設定
    - 例: `feature/task-1-2-3-brief-description`
    - 例: `fix/task-1-2-4-issue-description`
  - ブランチの作成をリモートにプッシュ
  - ブランチ保護ルールを確認する

- **開発環境が正常に動作することを確認**
  - ローカル開発サーバーを起動し動作確認
  - 依存関係が正しくインストールされていること
  - 環境変数が適切に設定されていること

- **必要なツールや依存関係を準備**
  - 必要なライブラリやツールをインストール
  - 開発に必要なドキュメントやリソースを用意
  - IDE拡張機能や設定を整える

## 2. TDDアプローチの実装フェーズ

実装フェーズではテスト駆動開発（TDD）のアプローチを採用し、小さなサイクルで開発を進めます。

### 2.1 テストファーストの実装

- **失敗するテストを作成（Red）**
  - 期待される動作をテストコードとして記述
  - テストを実行し、失敗することを確認
  - テストが正しい理由で失敗していることを確認

- **最小限のコードでテストをパス（Green）**
  - テストを通過する最小限のコードを実装
  - コードの最適化よりもテスト通過を優先
  - テストを再実行し、通過することを確認

- **コードのリファクタリング（Refactor）**
  - コードの品質を改善（重複除去、名前の改善など）
  - テスト通過を維持しながらリファクタリング
  - コード規約とベストプラクティスに従う
  - 必要に応じてテストコードもリファクタリング

- **このサイクルを繰り返す**
  - 次の機能や要件に対する新しいテストを作成
  - サイクルを繰り返し、機能を段階的に追加
  - 常に実行可能な状態を維持する

### 2.2 段階的な実装

- **小さな機能単位で実装を進める**
  - 一度に1つの小さな機能に集中する
  - 複雑な問題は小さく分解して対処する
  - 各機能の実装後に統合テストを行う

- **各機能実装後にテストを実行**
  - 単体テストの自動実行
  - 既存のテストが壊れていないことを確認
  - テストカバレッジを確認し必要に応じて追加

- **問題が発生した場合は即座に対応**
  - 問題の根本原因を特定
  - 修正と検証を迅速に行う
  - 同様の問題の再発を防ぐためのテストを追加

- **定期的にコミットを行い変更を記録**
  - 論理的な単位ごとにコミット
  - 明確なコミットメッセージを記述
  - 大きな変更を一度にコミットしない
  - コミット前にはビルドとテストを実行

### 2.3 コードレビュー準備

- **コードスタイルとリンターを確認**
  - リンターを実行し警告やエラーを修正
  - コードフォーマッターでスタイルを統一
  - プロジェクトのコード規約に準拠しているか確認

- **ドキュメンテーションコメントを追加**
  - 関数やクラスの目的と使用方法をコメントで説明
  - 複雑なロジックや判断の理由を記録
  - APIドキュメントを生成するための正しいフォーマットを使用

- **不要なコードやコメントを削除**
  - デバッグ用のコードや`console.log`の削除
  - コメントアウトされた古いコードの削除
  - TODOコメントの解決または整理

- **自己レビューを実施**
  - コードを客観的に見直す
  - 潜在的な問題や改善点を特定
  - エッジケースが適切に処理されているか確認
  - 認知的複雑性が高すぎる部分を特定し簡素化

## 3. 検証フェーズ

実装後は、徹底的な検証を行い、品質基準を満たしていることを確認します。

### 3.1 テストの完全実行

- **単体テストの実行**
  - すべての単体テストが通過することを確認
  - モックやスタブが適切に利用されているか確認
  - テスト環境とテストデータの問題がないか確認

- **統合テストの実行**
  - コンポーネント間の相互作用をテスト
  - エンドツーエンドのシナリオを検証
  - 外部依存関係との結合テスト

- **カバレッジの確認**
  - コードカバレッジレポートを生成し確認
  - 最低限の要求カバレッジを満たしているか検証
  - 重要なロジックが十分にテストされているか確認

- **エッジケースのテスト**
  - 極端な入力値や境界条件をテスト
  - エラー処理とリカバリーをテスト
  - 並行処理や競合条件のテスト（該当する場合）

### 3.2 手動検証

- **実装した機能を手動で確認**
  - 想定されるユースケースを手動で実行
  - UIの場合は視覚的な確認
  - ユーザー体験の評価

- **エッジケースを手動でテスト**
  - 自動テストでカバーできない状況の検証
  - 実際のユーザー操作を模倣したテスト
  - 意図的に誤った操作や入力を試す

- **UIの場合は表示を複数環境で確認**
  - 異なるブラウザでの表示確認
  - モバイルとデスクトップでのレスポンシブネス
  - 異なる画面サイズでのレイアウト

- **ユーザーシナリオに沿った検証**
  - エンドツーエンドのユーザーフローを実行
  - 実際のユースケースの完遂を確認
  - フィードバックの収集（可能な場合）

### 3.3 品質チェック

- **コード品質ツールの実行**
  - 静的解析ツールによるコード品質のチェック
  - 潜在的なバグやコード臭の検出
  - セキュリティの脆弱性のスキャン

- **パフォーマンスの確認**
  - メモリ使用量の測定
  - 実行時間やレスポンス時間の測定
  - ボトルネックの特定と最適化（必要な場合）

- **セキュリティの確認**
  - 入力検証の適切な実装
  - 認証と認可の正確な実装
  - データ保護とプライバシーの考慮

- **アクセシビリティの確認（UI関連の場合）**
  - アクセシビリティガイドラインへの準拠
  - スクリーンリーダー対応の確認
  - キーボードナビゲーションの確認

## 4. タスク完了フェーズ

検証が完了し、すべての基準を満たしたら、タスクの完了処理を行います。

### 4.1 ドキュメント更新

- **コードのドキュメントを更新**
  - インラインコメントの完成
  - API仕様書の更新
  - アーキテクチャドキュメントの更新（必要な場合）

- **README.mdの関連部分を更新**
  - 新機能の説明を追加
  - 使用方法やサンプルコードを追加
  - 既存の情報を最新状態に更新

- **新しいAPI・コンポーネントの使い方を文書化**
  - パラメータと戻り値の説明
  - 使用例や制限事項の記述
  - エラーケースと回避策の説明

- **変更履歴を記録**
  - CHANGELOG.mdの更新（該当する場合）
  - バージョン情報の更新（該当する場合）
  - 互換性に関する注意点の記録

### 4.2 プルリクエスト作成

- **タスク完了報告を作成**
  - 実装した機能の概要
  - 完了基準の達成状況
  - テスト結果のサマリー

- **変更内容と目的を説明**
  - なぜこの変更が必要だったのか
  - 選択したアプローチとその理由
  - 検討したが採用しなかった代替案

- **テスト結果を共有**
  - 単体テストと統合テストの結果
  - カバレッジレポート
  - パフォーマンス測定結果（該当する場合）

- **レビュアーへの注意点を記載**
  - 特に注意深くレビューしてほしい部分
  - 複雑な実装の説明
  - 制約や妥協点の説明

### 4.3 レビュー対応

- **レビューコメントに対応**
  - すべてのレビューコメントを確認
  - 指摘された問題に対する修正を実装
  - 修正できない場合は理由を説明

- **必要な修正を実施**
  - レビュー指摘に基づく修正
  - 小さなコミットで修正を行う
  - 重要な変更には追加のテストを作成

- **修正後の再テスト**
  - 修正後に全テストを再実行
  - 修正がリグレッションを引き起こしていないことを確認
  - パフォーマンスやセキュリティへの影響を確認

- **レビュー承認の確認**
  - 必要な承認者全員の承認を得る
  - 残っている懸念事項がないことを確認
  - マージの前提条件をすべて満たしていることを確認

### 4.4 完了報告

- **タスク管理システムの更新**
  - タスクのステータスを「完了」に更新
  - 実作業時間と見積もり時間の記録
  - 関連ドキュメントやPRへのリンク追加

- **進捗報告の作成と共有**
  - タスク完了報告の共有
  - 成果のデモンストレーション（必要な場合）
  - 主要な決定や解決した課題の共有

- **次のタスクへの影響確認**
  - 依存するタスクへの影響を確認
  - 次のタスクの前提条件が満たされているか確認
  - 新たに発見された課題や懸念の共有

- **学びや気づきの共有**
  - プロセスや技術に関する学び
  - 次回のタスクに活かせる改善点
  - ベストプラクティスやパターンの共有

## 5. タスク実装チェックリスト

### 5.1 タスク開始前
- [ ] タスクの目的と要件を理解している
- [ ] 依存関係を確認した
- [ ] 技術的な制約を理解している
- [ ] 完了基準を確認した
- [ ] 実装計画を作成した
- [ ] 適切なブランチを作成した

### 5.2 実装中
- [ ] TDDアプローチを採用している
- [ ] コミットメッセージは明確で規約に従っている
- [ ] コード規約に従っている
- [ ] エラー処理を適切に実装している
- [ ] 適切なログ出力を行っている
- [ ] セキュリティを考慮している
- [ ] パフォーマンスを考慮している

### 5.3 完了前
- [ ] すべてのテストが通過している
- [ ] コードカバレッジが基準を満たしている
- [ ] 手動テストを実施した
- [ ] コード品質ツールで問題が検出されていない
- [ ] すべての完了基準を満たしている
- [ ] ドキュメントを更新した
- [ ] 不要なコードやコメントを削除した

### 5.4 PR提出前
- [ ] 最新のメインブランチをマージしている
- [ ] コードの変更はレビュー可能な大きさに制限されている
- [ ] PRの説明は明確で詳細である
- [ ] テスト結果のサマリーを含めている
- [ ] レビュアーへの注意点を記載している
- [ ] CIパイプラインのチェックが通過している