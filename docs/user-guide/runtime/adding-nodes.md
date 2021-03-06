---
layout: docs-user-guide
toc: toc-user-guide.html
title: パレットにノードを追加する
slug: ノードを追加
redirect_from:
  - /docs/getting-started/adding-nodes

---

Node-REDは有用なコアノードを一通り備えていますが、
Node-REDプロジェクトおよびより多くのコミュニティの両方からさらに多くのノードを入手することができます。

[Node-REDライブラリ](http://flows.nodered.org)で入手可能なノードを探すことができます。

### エディタを利用する

メインメニューから`パレットを管理する`オプションを選択して[パレットマネージャ](/docs/user-guide/editor/palette/manager)を開くことで、
エディタ内で直接ノードをインストールすることができます。

「現在のノード」タブはインストール済の全モジュールを一覧にしています。
どのノードを使用しているか、それらのどれかがアップデートできるかを示しています。

「ノードを追加」タブでは入手可能なノードモジュールのカタログを検索し、
インストールすることができます。


### npmでインストールする

コマンドラインからノードモジュールをインストールするため、
ユーザデータディレクトリ（デフォルトでは`$HOME/.node-red`）内から以下のコマンドを利用することができます:

    npm install <npm-package-name>

そして、新しいノードを見つけるためにNode-REDを再起動する必要があります。

### The package.json file

When first started, or a new project created, Node-RED will create an initial `package.json` file in your user directory, or project directory. This allows you to manage your additional dependencies, and release versions of your project, using standard npm practices. The initial version is 0.0.1 but should be edited according to your project release requirements.

`npm` will automatically add additional installed modules to the dependencies section of the `package.json` file in your user directory.

### ノードをアップグレードする

ノードのアップデートを確認する最も簡単な方法はエディタで[パレットマネージャ](/docs/user-guide/editor/palette/manager)を開くことです。
そして必要であればアップデートを適用することができます。

`npm`を利用することでコマンドラインからアップデートを確認することもできます。
ユーザディレクトリ`~/.node-red`で以下のコマンドを実行する:

```
npm outdated
```

これはアップデートを利用可能なモジュールを強調します。
モジュールの最新バージョンをインストールためには、以下のコマンドを実行します:

```
npm install <name-of-module>@latest
```

どちらの方法でも、アップデートをロードするためにはNode-REDを再起動する必要があります。

<div class="doc-callout"><em>Note</em> : <code>--unsafe-perm</code>オプションを使用する理由は、
node-gypはネイティブなライブラリをリコンパイルしようとするときに「nobody」ユーザとして実行しようとし、
特定の依存関係へのアクセスに失敗するからです。
これにより、問題のノード（たとえば、serialportノード）はインストールされません。
インストール時にルートアクセスを許可することで、
アップグレード時にノードを正しくインストールできます。</div>
