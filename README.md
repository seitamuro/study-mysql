# 概要

MySQLをざっくり学びます｡

# やったこと

以下のサイトの練習問題に取り組んだ｡

https://tech.pjin.jp/blog/tag/sql%E7%B7%B4%E7%BF%92%E5%95%8F%E9%A1%8C/

## 問題62

mysql> select c.name, g.goal_time, p.position, p.name from goals g left join players p on g.pairing_id = p.id left join countries c on p.country_id = c.id;

## 問題63

mysql> select p.kickoff, c1.name as my_country, c2.name as enemy_country from pairings p left join countries c1 on c1.id = p.my_country_id left join countries c2 on c2.id = p.enemy_country_id limit 5;

## 問題64

mysql> select g.id, g.goal_time, (SELECT p.name FROM players p WHERE p.id = g.player_id) FROM goals g WHERE g.player_id IS NOT NULL limit 5;

## 問題65

mysql> select g.id, g.goal_time, p.name FROM goals g LEFT JOIN players p ON g.player_id = p.id limit 13;
# つまづいたこと

## "Access denied for user 'root'@'localhost' (using password: YES)"

docker-composeを使わずにMySQLのコンテナを作ると発生する｡
dockerコマンドでイメージから直接コンテナを作ると初期化をうまくできないらしい｡
docker-composeを使うと初期化がうまくいくっぽい｡
要検証｡

- 参考

https://github.com/seitamuro/docker-compose-mysql

https://stackoverflow.com/questions/59838692/mysql-root-password-is-set-but-getting-access-denied-for-user-rootlocalhost
