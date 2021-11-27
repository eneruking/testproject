# 準備
## Visual Studio Code(vscode)のインストール
## dockerのインストール
## docker-composeのインストール
# 開発環境の作成
## 仮想環境用の設定を行う
`server/youtubelike/.env.example`に環境構築に必要な環境変数サンプルがあるので`.env`というファイルを同じディレクトリに作成し、中身をコピペしてください。  
```
DB_ROOT_PASSWORD=rootユーザ用のパスワード
DATABASE_NAME=database名
DB_USER=DBの通常ユーザ名
DB_USER_PASSWORD=通常ユーザ用パスワード
TIMEZONE=Asia/Tokyo
```
## 仮想環境(docker)の実行
※Mac osの環境で動作確認済み  
vscode上のツールバーTerminalからNew Terminalを選択  
すると下部にTERMINALタブのウィンドウがでているはずなので、そこでコマンドを実行する  
docker-compose.ymlがあるディレクトリで下記のコマンドを実行  
```Bash
docker-compose up -d
```
しばらく待つ
## 仮想環境の中に入る
```Bash
docker-compose exec web bash
```
Dockerfileに記載したWORKDIRのディレクトへ移動しているはず
```Bash
pwd
```
上記のコマンドで自分が現在いるカレンとディクトリがわかる  
/var/www/html  
と表示されれば問題なし
## プログラミングを行うためのフレームワーク(Laravel)で環境を作る
serverディレクトリ配下に`youtubelike`のフォルダがすでにあれば既にlaravel環境ができているのでこの手順は省略する。 
```Bash
composer create-project "laravel/laravel=6.*" youtubelike
``` 
composer create-project "laravel/laravel=6.*" プロジェクト名  
プロジェクト名は「youtubelike」にしてください。  
Apacheのプロジェクトルートを`/var/www/html/youtubelike/public`に設定してあるためです。

