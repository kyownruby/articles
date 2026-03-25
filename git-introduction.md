# Git入門

## Gitとは

Gitは、ソースコードの変更履歴を管理するための**分散型バージョン管理システム**です。Linus Torvalds氏がLinuxカーネルの開発のために2005年に作成しました。

Gitを使うことで、以下のようなことが可能になります。

- ファイルの変更履歴を記録・追跡できる
- 過去の状態にいつでも戻せる
- 複数人で同時に開発を進められる
- 変更内容の競合を検出・解決できる

## インストール

### macOS

```bash
brew install git
```

### Ubuntu / Debian

```bash
sudo apt install git
```

### Windows

[Git for Windows](https://gitforwindows.org/) からインストーラをダウンロードしてインストールします。

### バージョン確認

```bash
git --version
```

## 初期設定

Gitを使い始める前に、ユーザー名とメールアドレスを設定します。

```bash
git config --global user.name "あなたの名前"
git config --global user.email "your-email@example.com"
```

設定内容は以下のコマンドで確認できます。

```bash
git config --list
```

## 基本的なワークフロー

### 1. リポジトリの作成

新しいプロジェクトを始めるには、`git init` でリポジトリを初期化します。

```bash
mkdir my-project
cd my-project
git init
```

既存のリポジトリを取得するには `git clone` を使います。

```bash
git clone https://github.com/user/repository.git
```

### 2. 変更の記録

Gitでは、変更をコミットするまでに3つの領域を経由します。

```
作業ディレクトリ → ステージングエリア → リポジトリ
   (Working)        (Staging/Index)      (Repository)
```

#### 状態の確認

```bash
git status
```

#### 変更をステージングエリアに追加

```bash
# 特定のファイルを追加
git add ファイル名

# すべての変更を追加
git add .
```

#### コミット（変更の確定）

```bash
git commit -m "コミットメッセージ"
```

コミットメッセージには、**何を・なぜ変更したか**を簡潔に書きましょう。

### 3. 履歴の確認

```bash
# コミット履歴を表示
git log

# 1行ずつ簡潔に表示
git log --oneline

# 変更内容の差分を確認
git diff
```

## ブランチ

ブランチは、メインの開発ラインから分岐して独立した作業を行うための機能です。

```bash
# ブランチの一覧を表示
git branch

# 新しいブランチを作成して切り替え
git switch -c feature/new-function

# ブランチを切り替え
git switch main

# ブランチをマージ（統合）
git merge feature/new-function

# 不要になったブランチを削除
git branch -d feature/new-function
```

## リモートリポジトリとの連携

GitHubなどのリモートリポジトリと連携することで、チームでの共同開発が可能になります。

```bash
# リモートリポジトリを追加
git remote add origin https://github.com/user/repository.git

# ローカルの変更をリモートに送信
git push origin main

# リモートの変更をローカルに取得・統合
git pull origin main
```

## よく使うコマンドまとめ

| コマンド | 説明 |
|---|---|
| `git init` | リポジトリを新規作成 |
| `git clone <URL>` | リモートリポジトリを複製 |
| `git status` | 作業ディレクトリの状態を表示 |
| `git add <ファイル>` | 変更をステージングエリアに追加 |
| `git commit -m "メッセージ"` | 変更をコミット |
| `git log` | コミット履歴を表示 |
| `git diff` | 変更の差分を表示 |
| `git branch` | ブランチの一覧を表示 |
| `git switch <ブランチ名>` | ブランチを切り替え |
| `git merge <ブランチ名>` | ブランチを統合 |
| `git push` | リモートに変更を送信 |
| `git pull` | リモートの変更を取得・統合 |

## .gitignore

バージョン管理に含めたくないファイルは `.gitignore` に記述します。

```
# 環境変数ファイル
.env

# 依存パッケージ
node_modules/

# ビルド成果物
dist/
build/

# OS固有のファイル
.DS_Store
Thumbs.db
```

## まとめ

Gitの基本的な使い方を紹介しました。最初は `init` → `add` → `commit` の流れを覚えるところから始めましょう。慣れてきたらブランチやリモートリポジトリを活用して、より効率的な開発ワークフローを構築していくことができます。
