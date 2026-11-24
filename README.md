# kaibunshoHokanko

Java / Spring Boot で作成した文章管理アプリの学習用プロジェクト（2023年）。

- ユーザー登録・一覧・更新・削除
- 文章の登録・管理

## DB 設定の外部化

データベースの接続情報（URL・ユーザー名・パスワード）はソースコードや
`application.properties` にハードコードせず、外部から注入する方針です。

- Spring Boot の `SPRING_DATASOURCE_URL` / `SPRING_DATASOURCE_USERNAME` /
  `SPRING_DATASOURCE_PASSWORD` などの環境変数で上書き可能にします。
- リポジトリには値を置かず、必要なキー名だけをプレースホルダとして
  管理します。ローカル開発の値は Git 管理外のファイルに限定します。
- 本番環境ではシークレット管理サービスの参照（例: `op://...`）を
  起動時に解決して注入し、接続情報はログや例外へ出力しません。

## ライセンス

本プロジェクトは `AGPL-3.0-or-later` で提供されます。
全文は [LICENSE](LICENSE) を参照してください。
