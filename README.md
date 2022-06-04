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

## 問題66

mysql> select p.position, p.height, p2.name, p2.club from (select position, max(height) as height from players GROUP BY position) p left join players p2 on p2.height = p.height AND p2.position = p.position;

## 問題67

mysql> SELECT p2.position, max(p2.height) as height, (SELECT p1.name FROM players p1 WHERE p1.position =
 p2.position AND max(p2.height) = p1.height) as name FROM players p2 GROUP BY p2.position;

## 問題68

mysql> SELECT p.uniform_num, p.position, p.name, p.height FROM players p WHERE p.height < (SELECT avg(p2.height) FROM players p2) limit 10;

## 問題69

mysql> SELECT c.group_name, max(c.ranking), min(c.ranking) FROM countries c GROUP BY c.group_name HAVING max(c.ranking) - min(c.ranking) > 50;

## 問題70

mysql> select "1980",  count(birth) from players where birth between "1980-01-01" and "1980-12-31" union select "1981" , count(birth) from players where birth between "1981-01-01" and "1981-12-31";


# つまづいたこと

## "Access denied for user 'root'@'localhost' (using password: YES)"

docker-composeを使わずにMySQLのコンテナを作ると発生する｡
dockerコマンドでイメージから直接コンテナを作ると初期化をうまくできないらしい｡
docker-composeを使うと初期化がうまくいくっぽい｡
要検証｡

- 参考

https://github.com/seitamuro/docker-compose-mysql

https://stackoverflow.com/questions/59838692/mysql-root-password-is-set-but-getting-access-denied-for-user-rootlocalhost
