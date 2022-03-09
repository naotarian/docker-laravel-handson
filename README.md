# docker-laravel-handson

Docker Composeの現在の安定リリースバージョンをダウンロード
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

実行権限を付与する
sudo chmod +x /usr/local/bin/docker-compose

バージョン確認
docker-compose -v

いらないimageを削除
docker rmi $(docker images -q)

リポジトリフォーク
git clone git@github.com:naotarian/docker-laravel-handson.git

作業ディレクトリに移動
cd docker-laravel-handson

コンテナ立ち上げ
docker-compose up -d

コンテナに入る
docker-compose exec app bash

書き込み権限がないとキャッシュやログにエラーを書き込めない。権限を付与。
chmod -R 777 storage bootstrap/cache

composer install

cp .env.example .env

php artisan key:generate

php artisan migrate

コンテナを抜ける
exit

コンテナを落とす
docker-compose down
