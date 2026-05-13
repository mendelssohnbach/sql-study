# CLAUDE.md

ユーザーとのやり取りは、日本語で行うこと。

このファイルは、リポジトリで作業する際に Claude Code (claude.ai/code) へのガイダンスを提供します。

## 概要

SQL の学習・練習用リポジトリです。GitHub Codespaces または VS Code Dev Containers で動作する PostgreSQL 環境を提供します。

## Dev Container

`.devcontainer/devcontainer.json` と `.devcontainer/compose.yml` で構成されています。

**起動方法**
- GitHub Codespaces: リポジトリページの「Code」→「Codespaces」から起動
- VS Code ローカル: 「Reopen in Container」コマンドを実行

**コンテナ構成**

| サービス | 内容 |
|----------|------|
| `workspace` | 開発作業用コンテナ |
| `db` | PostgreSQL 17 |
| `pgadmin` | pgAdmin 4（ブラウザ GUI）|

## PostgreSQL 接続情報

| 項目 | 値 |
|------|-----|
| ホスト | `db`（コンテナ内） / `localhost`（ホストから） |
| ポート | `5432` |
| データベース | `study` |
| ユーザー | `postgres` |
| パスワード | `postgres` |

**ターミナルから接続**

```bash
psql -h db -U postgres -d study
```

## GUI（pgAdmin）

ブラウザで `http://localhost:8080` にアクセス。
- メール: `admin@example.com`
- パスワード: `admin`

初回のみサーバーを手動登録してください。
- ホスト: `db`、ポート: `5432`、ユーザー: `postgres`、パスワード: `postgres`

## VS Code 拡張機能

| 拡張機能 | 用途 |
|----------|------|
| `ms-ossdata.vscode-pgsql` | PostgreSQL 接続・クエリ実行・スキーマ参照 |
| `inferrinizzard.prettier-sql-vscode` | SQL フォーマッター |

`.sql` ファイルは保存時に Prettier SQL VSCode で自動フォーマットされます。
