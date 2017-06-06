# WordPress Template using Docker Compose

## how to use

### 環境変数ファイルの用意

`.env` ファイルを `docker-compose.yml` と同じディレクトリに作成する。このリポジトリではGitの管理化に含めていない。

```
WORDPRESS_DB_NAME=wordpress
WORDPRESS_DB_USER=wp_user
WORDPRESS_DB_PASSWORD=hogehoge
 
MYSQL_RANDOM_ROOT_PASSWORD=yes
MYSQL_DATABASE=wordpress
MYSQL_USER=wp_user
MYSQL_PASSWORD=hogehoge
```

### Docker
* 初めてスタートする時
  * `$ docker-compose up -d`
  * Webブラウザから `http://localhost:8080` にアクセス
* コンテナを停止
  * `$ docker-compse stop`
* コンテナを再起動
  * `$ docker-compse start` もしくは `$ docker-compse up`
* コンテナを削除
  * `$ docker-compse down`

## テーマの置き場所

`themes` ディレクトリにテーマを置く。

## DBのバックアップ

MySQLのコンテナが起動している状態で、下記のコマンドより `data-mysql` ディレクトリに `mysql.dump.sql` ファイルが生成される。

`$ docker exec -it dbのコンテナ名 sh -c 'mysqldump wordpress -u wp_user -phogehoge 2> /dev/null' > db-data/mysql.dump.sql
`

次回の立ち上げはこのファイルが読み込まれる。

