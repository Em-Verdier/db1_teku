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

db_1-# ALTER TABLE users ADD COLUMN bio TEXT DEFAULT 'Hello, world!';

db_1=# SELECT * FROM users;
 id |  name   | password |      bio      
----+---------+----------+---------------
  1 | alice   | 123      | Hello, world!
  2 | bob     | 456      | Hello, world!
  3 | charlie | 789      | Hello, world!
  4 | dan     | 101112   | Hello, world!
  5 | eve     | 131415   | Hello, world!
  6 | faythe  | 161718   | Hello, world!
(6 rows)

db_1=# UPDATE users SET bio = Concat('Hello, i am ', name); 

db_1=# SELECT * FROM users;
 id |  name   | password |         bio         
----+---------+----------+---------------------
  1 | alice   | 123      | Hello, i am alice
  2 | bob     | 456      | Hello, i am bob
  3 | charlie | 789      | Hello, i am charlie
  4 | dan     | 101112   | Hello, i am dan
  5 | eve     | 131415   | Hello, i am eve
  6 | faythe  | 161718   | Hello, i am faythe
(6 rows)

db_1=# SELECT * FROM users ORDER BY id DESC LIMIT 2;
 id |  name  | password |        bio         
----+--------+----------+--------------------
  6 | faythe | 161718   | Hello, i am faythe
  5 | eve    | 131415   | Hello, i am eve
(2 rows)

db_1=# SELECT * FROM users WHERE((id%2)=1);
 id |  name   | password |         bio         
----+---------+----------+---------------------
  1 | alice   | 123      | Hello, i am alice
  3 | charlie | 789      | Hello, i am charlie
  5 | eve     | 131415   | Hello, i am eve
(3 rows)

db_1=# DELETE FROM users WHERE ((id%2)=0);
DELETE 3
db_1=# SELECT * FROM users;
 id |  name   | password |         bio         
----+---------+----------+---------------------
  1 | alice   | 123      | Hello, i am alice
  3 | charlie | 789      | Hello, i am charlie
  5 | eve     | 131415   | Hello, i am eve
(3 rows)

db_1=# DROP TABLE users;
DROP TABLE
db_1=# SELECT * FROM users;
ERROR:  relation "users" does not exist
LINE 1: SELECT * FROM users;

db_1-# \c postgres
postgres=# DROP DATABASE db_1;
postgres-# \db_1
       List of tablespaces
    Name    |  Owner   | Location 
------------+----------+----------
 pg_default | postgres | 
 pg_global  | postgres | 
(2 rows)















