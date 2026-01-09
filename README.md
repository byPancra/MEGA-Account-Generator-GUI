<div align="center">

[English](https://github.com/byPancra/MEGA-Account-Generator-GUI) | [Português (Brasil)](https://github.com/byPancra/MEGA-Account-Generator-GUI/tree/lang-pt-BR) | [Español](https://github.com/byPancra/MEGA-Account-Generator-GUI/tree/lang-es) | **日本語**

</div>
<br>

<div align="center">

  ![Mega Account Generator GUI](./img/readme-icon.png)

  <h1 align="center">Mega Account Generator GUI</h1>
  
  **MEGA.nzアカウントの作成と管理を自動化する究極のツール。**
  
  *プロフェッショナルなインターフェースでアカウントを生成、管理、タグ付け、エクスポート。*

  [![Python Version](https://img.shields.io/badge/python-3.8%2B-blue?style=for-the-badge&logo=python)](https://www.python.org/)
  [![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)](./LICENSE)
  [![Status](https://img.shields.io/badge/status-active-success?style=for-the-badge)]()
  [![Releases](https://img.shields.io/github/downloads/byPancra/Mega-Account-Generator-GUI/total?style=for-the-badge&color=orange)](https://github.com/byPancra/Mega-Account-Generator-GUI/releases)

  [機能](#-機能) • [インストール](#-インストール) • [使い方](#-使い方) • [高度な管理](#-高度な管理) • [FAQ](#-faq)

</div>

---

## 📋 概要

**Mega Account Generator GUI** は、[MEGA.nz](https://mega.nz) アカウントを大量に生成および管理する必要があるパワーユーザー向けに設計された堅牢なデスクトップアプリケーションです。単純なスクリプトとは異なり、このツールは、タグ付け、フィルタリング、ステータス追跡、データエクスポートなど、アカウントのライフサイクル管理のための完全なエコシステムを提供します。

**Modern Python** (CustomTkinter) と **スレッドセーフアーキテクチャ** で構築されており、数百のアカウントを処理する場合でも信頼性を保証します。

![Demo](./img/intro2.gif)

---

## :zap: 機能

### 🚀 コア生成
*   **高速マルチスレッド**: 同時に最大8つのアカウントを生成します。
*   **スマートレート制限**: Mail.tmの制限を回避するためのインテリジェントな遅延と再試行ロジック（最大12回試行）。
*   **バンドルされた依存関係**: 実行可能バージョンには `megatools` が事前にパッケージ化されており、外部設定は不要です。

### 🛠️ 高度な管理
*   **タグ付けシステム**: カスタムタグ（例：`個人用`、`バックアップ`、`クライアントA`）でアカウントを整理し、簡単に検索できます。
*   **検索とフィルター**: メール、ステータス（`Active`、`Disabled`、`Failed`）、またはタグでアカウントを即座に見つけます。
*   **一括操作**:
    *   **Keep-Alive**: アクティビティがないことによるアカウント削除を防ぐための自動ログイン。
    *   **ストレージチェック**: すべてのアカウントの使用済み/空きストレージクォータを自動更新します。
    *   **アカウント制御**: 特定のアカウントを無効にして、削除することなく一括操作（例：Keep-Aliveチェック）から除外します。

### 💾 データの自由
*   **プロフェッショナルエクスポート**: データベースを、フォーマットされたスタイルを持つ **Excel (.xlsx)** またはプログラムで使用するための **JSON** にエクスポートします。
*   **シームレスなインポート**: JSON/Excelインポートを介して、他のツールやバックアップからデータを移行します。
*   **クリップボード統合**: メールとパスワードをワンクリックでコピーします。

### 🔒 セキュリティと信頼性
*   **スレッドセーフCSV**: 同時書き込み中のデータ破損を防ぎます。
*   **クラッシュ回復**: 「Stop」ボタンは操作を正常に停止し、データの整合性を維持します。

---

## :rocket: インストール

### オプションA: スタンドアロン実行ファイル (推奨)
最新リリースをダウンロードします。Pythonや外部ツールは必要ありません。
1.  [Releases](https://github.com/byPancra/Mega-Account-Generator-GUI/releases) から `MegaGenerator.exe` をダウンロードします。
2.  実行ファイルを実行します。

### オプションB: ソースから実行

**前提条件:**
*   Python 3.8+
*   [Megatools](https://megatools.megous.com/) (PATHに追加済み)

**手順:**
1.  **リポジトリをクローン:**
    ```bash
    git clone https://github.com/byPancra/Mega-Account-Generator-GUI.git
    cd Mega-Account-Generator-GUI
    ```

2.  **依存関係をインストール:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **アプリケーションを実行:**
    ```bash
    python gui.py
    ```

---

## :computer: 使い方

### アカウントの生成
1.  **Generator** タブに移動します。
2.  生成する **Threads** (スレッド) と **Accounts** (アカウント) の数を設定します。
3.  **"Generate Accounts"** をクリックします。
4.  資格情報は `accounts.csv` に保存され、**Stored Accounts** タブに表示されます。

### アカウントの管理
**Stored Accounts** タブに移動します:
*   **検索**: メールを入力して即座にフィルタリングします。
*   **フィルター**: ドロップダウンを使用して、`Active`、`Disabled`、または `Failed` アカウントのみを表示します。
*   **編集**: "Edit" ボタンをクリックして、保存されたパスワードを変更したり、タグを管理したりします。
*   **コピー**: 資格情報をクリップボードにコピーするためのクイックボタン。

### 💻 CLI使用法 (コマンドライン)
ターミナルを好む上級ユーザーや、これをスクリプトに統合したい場合。

```bash
# 基本的な使用法 (3つのアカウントを生成)
python generate_accounts.py

# 5つのスレッドで50のアカウントを生成
python generate_accounts.py -n 50 -t 5

# すべてのアカウントに特定のパスワードを設定
python generate_accounts.py -n 10 -p "MySecretPass123!"
```

**引数:**
*   `-n`, `--number`: 作成するアカウントの数 (デフォルト: 3)
*   `-t`, `--threads`: 同時スレッド数 (1-8)
*   `-p`, `--password`: すべてのアカウントの共通パスワード (オプション)

#### Keep-Aliveチェック (ログインとストレージ)
`accounts.csv` 内のすべてのアカウントを確認し、ストレージクォータをチェックして、アクティブに保つには:

```bash
python signin_accounts.py
```

*   **引数は不要です。**
*   `accounts.csv` 内のすべてのアカウントを反復処理します。
*   **"Disabled" (無効) としてマークされたアカウントはスキップされます。**
*   ステータスを `Active` または `Login Failed` に更新します。
*   使用済み/空きストレージ値を更新します。


---

## :briefcase: 高度な管理

### データのエクスポート
バックアップや外部使用のために、アカウントデータベース全体をエクスポートできます。
1.  右上の **Export** をクリックします。
2.  フォーマットされたスプレッドシートの場合は **Excel**、生データの場合は **JSON** を選択します。
3.  保存場所を選択します。

*Excelエクスポートには、読みやすくするために色分けされたステータス列とフォーマットされたヘッダーが含まれます。*

### データのインポート
以前のバージョンや他のツールから移行します。
1.  **Import** をクリックします。
2.  有効な `.json` または `.xlsx` ファイルを選択します。
3.  ツールはデータを `accounts.csv` にマージします。

---

## :grey_question: FAQ

<details>
<summary><strong>なぜ8スレッドに制限されているのですか？</strong></summary>
一時メールプロバイダー (Mail.tm) には厳格なレート制限があります。同時スレッド数が8を超えると、IPBANや生成失敗の可能性が大幅に高まります。
</details>

<details>
<summary><strong>"Sign In" ボタンは何をしますか？</strong></summary>
"Keep-Alive" チェックを実行します。`megatools` を使用してアカウントへのログインを試みます。これにより、ストレージクォータ情報が更新され、アカウントがアクティブであることがMEGAに通知され、削除が防止されます。
</details>

<details>
<summary><strong>アカウントはどこに保存されますか？</strong></summary>
すべてのデータは、アプリケーションディレクトリ内の `accounts.csv` にローカルに保存されます。エクスポート機能を使用してこのデータをエクスポートすることもできます。
</details>

<details>
<summary><strong>"Megatools not found" エラーが表示されます。</strong></summary>
ソースから実行している場合は、`megatools` がインストールされ、システムPATHに追加されていることを確認してください。実行ファイルを使用している場合、これは自動的に処理されます。
</details>

---

## :warning: 免責事項

このツールは、**教育およびテスト目的のみ**に作成されています。このソフトウェアを使用してサードパーティのサービスを悪用したり、制限を回避したり、MEGA.nzまたはMail.tmの利用規約 (ToS) に違反したりすることは固く禁じられています。開発者は、悪用に対して一切の責任を負いません。

---

## :sparkling_heart: 謝辞

*   [f-o/MEGA-Account-Generator](https://github.com/f-o/MEGA-Account-Generator) によるオリジナルの作品に基づいています。
*   [TomSchimansky/CustomTkinter](https://github.com/TomSchimansky/CustomTkinter) によるGUIコンポーネント。
*   [byPancra](https://github.com/byPancra) によって強化および保守されています。

---

## :copyright: ライセンス

**MITライセンス**の下で配布されています。詳細は [LICENSE](LICENSE) を参照してください。

<div align="center">
  <sub>Developed with ❤️ by <a href="https://github.com/byPancra">byPancra</a></sub>
</div>
