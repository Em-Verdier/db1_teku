# db1_teku

db_1 git:(main) sudo service postgresql start

psql -d postgres -U postgres

postgres=> CREATE DATABASE db_1;

postgres-# \c db_1

db_1=# CREATE TABLE users (id SERIAL PRIMARY KEY, name VARCHAR(30), password VARCHAR(30));

db_1=# INSERT INTO users (name, password) VALUES ('alice', '123'), ('bob', '456'), ('charlie', '789');

db_1=# SELECT * FROM users;

db_1=# SELECT * FROM users;
 id |  name   | password 
----+---------+----------
  1 | alice   | 123
  2 | bob     | 456
  3 | charlie | 789
(3 rows)
\
db_1=# INSERT INTO users (name, password) VALUES ('dan', '101112'), ('eve', '131415'), ('faythe', '161718');
INSERT 0 3
db_1=# SELECT * FROM users;
 id |  name   | password 
----+---------+----------
  1 | alice   | 123
  2 | bob     | 456
  3 | charlie | 789
  4 | dan     | 101112
  5 | eve     | 131415
  6 | faythe  | 161718
(6 rows)

db_1=# SELECT * FROM users WHERE length(password)>3;
 id |  name  | password 
----+--------+----------
  4 | dan    | 101112
  5 | eve    | 131415
  6 | faythe | 161718
(3 rows)






