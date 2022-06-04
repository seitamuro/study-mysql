# 概要

MySQLをざっくり学びます｡

# つまづいたこと

## "Access denied for user 'root'@'localhost' (using password: YES)"

docker-composeを使わずにMySQLのコンテナを作ると発生する｡
dockerコマンドでイメージから直接コンテナを作ると初期化をうまくできないらしい｡
docker-composeを使うと初期化がうまくいくっぽい｡
要検証｡

- 参考

https://github.com/seitamuro/docker-compose-mysql

https://stackoverflow.com/questions/59838692/mysql-root-password-is-set-but-getting-access-denied-for-user-rootlocalhost
