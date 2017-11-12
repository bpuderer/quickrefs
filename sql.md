# sqlite3 session

```
$ sqlite3 test.db
SQLite version 3.11.0 2016-02-15 17:29:24
Enter ".help" for usage hints.
sqlite> .tables
sqlite> create table artists (id integer primary key, name text);
sqlite> create table tracks (id integer primary key, name text, year integer, artist_id integer);
sqlite> /* create table tracks (id integer primary key, name text, year integer, artist_id integer, foreign key(artist_id) references artists(id)); */
sqlite> .tables
artists  tracks
sqlite> insert into artists(id, name) values(1, 'Led Zeppelin');
sqlite> insert into artists(id, name) values(2, 'Black Sabbath');
sqlite> insert into artists(id, name) values(3, 'Deep Purple');
sqlite> insert into tracks(name, year, artist_id) values('Black Dog', 1971, 1);
sqlite> insert into tracks(name, year, artist_id) values('Song Remains the Same', 1974, 1);
sqlite> insert into tracks(name, year, artist_id) values('Heartbreaker', 1969, 1);
sqlite> insert into tracks(name, year, artist_id) values('Zero the Hero', 1983, 2);
sqlite> insert into tracks(name, year, artist_id) values('I', 1992, 2);
sqlite> insert into tracks(name, year) values('Afterimage', 1984);
sqlite> insert into tracks(name, year, artist_id) values('N.I.B.', 1970, 2);
sqlite> insert into tracks(name, year, artist_id) values('Child in Time', 1970, 3);
sqlite> insert into tracks(name, year, artist_id) values('Mistreated', 1974, 3);
sqlite> insert into tracks(name, year, artist_id) values('Highway Star', 1972, 3);
sqlite>
sqlite> .output ./music.sql
sqlite> .dump
sqlite> .output stdout
sqlite>
sqlite> .mode column
sqlite> .headers on
sqlite>
sqlite> select * from tracks;
id          name        year        artist_id
----------  ----------  ----------  ----------
1           Black Dog   1971        1
2           Song Remai  1974        1
3           Heartbreak  1969        1
4           Zero the H  1983        2
5           I           1992        2
6           Afterimage  1984
7           N.I.B.      1970        2
8           Child in T  1970        3
9           Mistreated  1974        3
10          Highway St  1972        3
sqlite>
sqlite> select name, year from tracks;
name        year
----------  ----------
Black Dog   1971
Song Remai  1974
Heartbreak  1969
Zero the H  1983
I           1992
Afterimage  1984
N.I.B.      1970
Child in T  1970
Mistreated  1974
Highway St  1972
sqlite>
sqlite> select distinct year from tracks;
year
----------
1971
1974
1969
1983
1992
1984
1970
1972
sqlite>
sqlite> /* =, !=, >, <, >=, <= */
sqlite> select year, name from tracks where year > 1972;
year        name
----------  ---------------------
1974        Song Remains the Same
1983        Zero the Hero
1992        I
1984        Afterimage
1974        Mistreated
sqlite>
sqlite> select year, name from tracks where year between 1972 and 1976;
year        name
----------  ---------------------
1974        Song Remains the Same
1974        Mistreated
1972        Highway Star
sqlite>
sqlite> select * from tracks where year in (1974, 1970) order by year desc, name asc;
id          name        year        artist_id 
----------  ----------  ----------  ----------
9           Mistreated  1974        3         
2           Song Remai  1974        1         
8           Child in T  1970        3         
7           N.I.B.      1970        2
sqlite>
sqlite> select * from tracks where artist_id is null;
id          name        year        artist_id 
----------  ----------  ----------  ----------
6           Afterimage  1984
sqlite>
sqlite> /* % wildcard matches 0+ chars, _ matches single char */
sqlite> /* like is case insensitive */
sqlite> select name from tracks where name like '%The%';
name
---------------------
Song Remains the Same
Zero the Hero
sqlite>
sqlite> select year, name from tracks order by year desc;
year        name
----------  ----------
1992        I
1984        Afterimage
1983        Zero the H
1974        Song Remai
1974        Mistreated
1972        Highway St
1971        Black Dog
1970        N.I.B.
1970        Child in T
1969        Heartbreak
sqlite>
sqlite> select year, name from tracks order by year asc limit 3;
year        name
----------  ------------
1969        Heartbreaker
1970        N.I.B.
1970        Child in Tim
sqlite>
sqlite> select year, count(*) from tracks group by year;
year        count(*)
----------  ----------
1969        1
1970        2
1971        1
1972        1
1974        2
1983        1
1984        1
1992        1
sqlite>
sqlite> update tracks set name='0 the Hero' where id=4;
sqlite> select id, name from tracks;
id          name
----------  ----------
1           Black Dog
2           Song Remai
3           Heartbreak
4           0 the Hero
5           I
6           Afterimage
7           N.I.B.
8           Child in T
9           Mistreated
10          Highway St
sqlite>
sqlite> delete from tracks where id=9;
sqlite> select id, name from tracks;
id          name
----------  ----------
1           Black Dog
2           Song Remai
3           Heartbreak
4           0 the Hero
5           I
6           Afterimage
7           N.I.B.
8           Child in T
10          Highway St
sqlite>
sqlite> select count(*) from tracks;
count(*)
----------
9
sqlite>
sqlite> /* inner join will combine rows from different tables if the join condition is true */
sqlite> select * from tracks join artists on tracks.artist_id=artists.id;
id          name        year        artist_id   id          name
----------  ----------  ----------  ----------  ----------  ------------
1           Black Dog   1971        1           1           Led Zeppelin
2           Song Remai  1974        1           1           Led Zeppelin
3           Heartbreak  1969        1           1           Led Zeppelin
4           0 the Hero  1983        2           2           Black Sabbat
5           I           1992        2           2           Black Sabbat
7           N.I.B.      1970        2           2           Black Sabbat
8           Child in T  1970        3           3           Deep Purple
10          Highway St  1972        3           3           Deep Purple
sqlite>
sqlite> /* outer joins do not require the join condition to be met to be included in results */
sqlite> select * from tracks left join artists on tracks.artist_id=artists.id;
id          name        year        artist_id   id          name
----------  ----------  ----------  ----------  ----------  ------------
1           Black Dog   1971        1           1           Led Zeppelin
2           Song Remai  1974        1           1           Led Zeppelin
3           Heartbreak  1969        1           1           Led Zeppelin
4           0 the Hero  1983        2           2           Black Sabbat
5           I           1992        2           2           Black Sabbat
6           Afterimage  1984
7           N.I.B.      1970        2           2           Black Sabbat
8           Child in T  1970        3           3           Deep Purple
10          Highway St  1972        3           3           Deep Purple
sqlite>
sqlite> select tracks.name as 'Track', tracks.year, artists.name as 'Artist' from tracks join artists on tracks.artist_id=artists.id where tracks.year > 1973;
Track                  year        Artist
---------------------  ----------  ------------
Song Remains the Same  1974        Led Zeppelin
0 the Hero             1983        Black Sabbat
I                      1992        Black Sabbat
sqlite>
sqlite> drop table tracks;
sqlite> .tables
artists
sqlite> .quit
$ rm test.db
$ sqlite3 test.db
SQLite version 3.11.0 2016-02-15 17:29:24
Enter ".help" for usage hints.
sqlite> .tables
sqlite> .read ./music.sql

sqlite> .tables
artists  tracks
sqlite> select count(*) from tracks;
10
sqlite>
```
