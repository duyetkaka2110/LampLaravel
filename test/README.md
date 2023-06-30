# 環境構築  
### コンテナ構築  
```
$ docker-compose build
```
  
### コンテナ起動
```
$ docker-compose up -d
```

### Laravelプロジェクトを作成
```
$ docker-compose exec app composer create-project laravel/laravel *プロジェクト名* --prefer-dist "6.0.*"
```

### nginxのルート設定変更
docker/nginx/default.conf内のroot設定を変更
```
server {
    listen 80;

    root /var/www/html/*プロジェクト名*/public;  ←ここ

    ...
}
```

### 作成したら再構築して再起動
```
$ docker-compose build web
$ docker-compose up -d
```

### もしlocalhostにアクセスしてもエラーが出た場合
laravelプロジェクト内のstorageフォルダ配下に権限を付与する。
```
$ docker-compose exec app chmod -R 777 *プロジェクト名*/storage
```



