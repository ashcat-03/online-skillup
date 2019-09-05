# online-skillup

Frontend オンラインスキルアップ

## 環境
+ node: 10.15.0
+ npm: 6.2.0以上

## パッケージのインストール
`$ npm install`

## ローカルでの開発
ローカルで開発するときは以下の2つのコマンドを2つのターミナルを使って実行する。

### フロントエンドサーバーの立ち上げ
`$ npm start`  
[http://localhost:3000](http://localhost:3000)にアクセスしてフロントエンドの開発をする。  

### websocketサーバーの立ち上げ
別のターミナルを開いて、以下を実行する。  
`$ npm run server`  
実行すると[http://localhost:4000](http://localhost:4000)にsocketサーバーが立ち上がる。  
ここへの接続は既に設定されているため特に設定する必要はない。
開発中はここにアクセスしてもエラーになるが、フロントエンドのコードをビルドするとビルドされたファイルが表示される。  

## ディレクトリ構成
```
.
├── server/          # サーバーを設定するディレクトリ
│   ├── public/      # ビルドしたときに生成先(特に触りません)
│   └── server.js    # サーバーの起動を設定するファイル
│
├── src/                  # フロントエンドのコードを管理するディレクトリ
│   ├── css/              # cssディレクトリ
│   │   ├── resources/    # 変数などの設定ファイル置き場
│   │   └── base.scss     # bodyタグやulタグなど、タグに対してスタイルを設定するファイル
│   ├── html/             # htmlを生成するディレクトリ(特に触りません)
│   ├── images/           # 画像ファイルを配置するディレクトリ
│   └── javascripts/      # javascriptディレクトリ
│       ├── components/   # componentを管理するディレクトリ
│       ├── constants/    # 定数を管理するディレクトリ
│       ├── utils/        # 汎用的なモジュールを管理するディレクトリ
│       ├── App.vue       # Vue.jsのエントリーポイント
│       └── entry.js      # JavaScriptのエントリーポイント
│
│ (これ以降のファイルは基本的に触る必要はない)
├── .babelrc                       # 古いブラウザにもサポートする為に使用するbabelの設定ファイル
├── .editorconfig                  # インデントの数や改行コードなどを統一するための設定ファイル
├── .eslintrc.yml                  # JavaScriptのコードをチェックするルールが書かれている設定ファイル
├── .gitignore                     # gitリポジトリに登録して欲しくない内容を記述する設定ファイル
├── .stylelintrc.yml               # CSSのコードをチェックするルールが書かれている設定ファイル
├── package-lock.json              # npm installでバージョンがずれてしまわないようにするlockファイル
├── package.json                   # npm packageや実行スクリプトを管理する設定ファイル
├── Procfile                       # Herokuにデプロイした後に実行するコードを書くファイル
├── README.md                      # github上に表示される最初に読んで欲しい内容を書くファイル
├── webpack.config.base.js         # webpackでビルドするときの基本設定ファイル
├── webpack.config.development.js  # 開発時に使用されるwebpackの設定ファイル
└── webpack.config.production.js   # productionビルド時に使用されるwebpackの設定ファイル
```

## その他のコマンド
### フロントエンドのコードのビルド
`$ npm run build`  
server/public以下に生成物を配置する。  
生成物が配置されたことで、`$ npm run server`を実行している時は[http://localhost:4000](http://localhost:4000)にアクセスするとビルドしたファイルを見ることができる。




## 自己評価
### この課題を通して学んだこと
+ vue.jsの使い方、簡単なできること
+ websocketの使い方
+ 自分が想像した機能を実装する難しさ


### 工夫した点
+ 文字の大きさなどの見やすさ
+ 色の統一

### 苦労した点
+ ソケット通信構築の仕方
+ 下記の時間があれば実装したかったことを途中で断念したこと
+ 既存のテンプレを読み解いて機能を実装する難しさ


### その他（あれば）
+ 時間があれば実装したいこと
+ 文字を自分と他人で左右に分ける(できるならアイコンもつけたい)
+ nameは固定、messageは送信後空欄にしたい
+ 文字のポップアップ後自動スクロール

### 今後実装してみたい機能
+ ボタンを押して入力欄の表示
+ messageのデータベース化
