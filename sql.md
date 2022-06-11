# sqlite3 session

```
$ sqlite3 test.db
SQLite version 3.31.1 2020-01-27 19:55:54
Enter ".help" for usage hints.
sqlite> .tables
sqlite> CREATE TABLE artist (artistid INTEGER PRIMARY KEY, artistname TEXT);
sqlite> CREATE TABLE album (albumid INTEGER PRIMARY KEY, albumname TEXT, year INTEGER, trackartist INTEGER, FOREIGN KEY(trackartist) REFERENCES artist(artistid));
sqlite> CREATE TABLE track (trackid INTEGER PRIMARY KEY, trackname TEXT, trackartist INTEGER, trackalbum INTEGER, FOREIGN KEY(trackartist) REFERENCES artist(artistid), FOREIGN KEY(trackalbum) REFERENCES album(albumid));
sqlite> .tables
album   artist  track 
sqlite> INSERT INTO artist VALUES(1, 'Led Zeppelin');
sqlite> INSERT INTO artist VALUES(2, 'Black Sabbath');
sqlite> INSERT INTO artist(artistid, artistname) VALUES(3, 'Deep Purple');
sqlite> INSERT INTO artist(artistid, artistname) VALUES(4, 'Rush');
sqlite> INSERT INTO artist(artistid, artistname) VALUES(5, 'Pink Floyd');
sqlite> INSERT INTO album VALUES(1, 'Untitled', 1971, 1);
sqlite> INSERT INTO album VALUES(2, 'Houses of the Holy', 1974, 1);
sqlite> INSERT INTO album VALUES(3, 'II', 1969, 1);
sqlite> INSERT INTO album VALUES(4, 'Born Again', 1983, 2);
sqlite> INSERT INTO album VALUES(5, 'Dehumanizer', 1992, 2);
sqlite> INSERT INTO album VALUES(6, 'Master of Reality', 1971, 2);
sqlite> INSERT INTO album VALUES(7, 'Deep Purple in Rock', 1970, 3);
sqlite> INSERT INTO album VALUES(8, 'Burn', 1974, 3);
sqlite> INSERT INTO album VALUES(9, 'Machine Head', 1972, 3);
sqlite> INSERT INTO album VALUES(10, 'Animals', 1977, 5);
sqlite> INSERT INTO track VALUES(1, 'Black Dog', 1, 1);
sqlite> INSERT INTO track VALUES(2, 'The Song Remains the Same', 1, 2);
sqlite> INSERT INTO track VALUES(3, 'Heartbreaker', 1, 3);
sqlite> INSERT INTO track VALUES(4, 'Zero the Hero', 2, 4);
sqlite> INSERT INTO track VALUES(5, 'I', 2, 5);
sqlite> INSERT INTO track VALUES(6, 'Into the Void', 2, 6);
sqlite> INSERT INTO track VALUES(7, 'Child in Time', 3, 7);
sqlite> INSERT INTO track VALUES(8, 'Mistreated', 3, 8);
sqlite> INSERT INTO track VALUES(9, 'Highway Star', 3, 9);
sqlite> .output ./music.sql
sqlite> .dump
sqlite> .output stdout
sqlite> .mode column
sqlite> .headers on
sqlite> SELECT COUNT(*) FROM artist;
COUNT(*)  
----------
5         
sqlite> SELECT * FROM album;
albumid     albumname   year        trackartist
----------  ----------  ----------  -----------
1           Untitled    1971        1          
2           Houses of   1974        1          
3           II          1969        1          
4           Born Again  1983        2          
5           Dehumanize  1992        2          
6           Master of   1971        2          
7           Deep Purpl  1970        3          
8           Burn        1974        3          
9           Machine He  1972        3          
10          Animals     1977        5          
sqlite> SELECT album.albumname, album.year FROM album;
albumname   year      
----------  ----------
Untitled    1971      
Houses of   1974      
II          1969      
Born Again  1983      
Dehumanize  1992      
Master of   1971      
Deep Purpl  1970      
Burn        1974      
Machine He  1972      
Animals     1977      
sqlite> SELECT a.albumname, a.year FROM album a;
albumname   year      
----------  ----------
Untitled    1971      
Houses of   1974      
II          1969      
Born Again  1983      
Dehumanize  1992      
Master of   1971      
Deep Purpl  1970      
Burn        1974      
Machine He  1972      
Animals     1977      
sqlite> SELECT albumname as 'Album' FROM album;
Album     
----------
Untitled  
Houses of 
II        
Born Again
Dehumanize
Master of 
Deep Purpl
Burn      
Machine He
Animals   
sqlite> SELECT year FROM album ORDER BY year ASC;
year      
----------
1969      
1970      
1971      
1971      
1972      
1974      
1974      
1977      
1983      
1992      
sqlite> SELECT YEAR, COUNT(*) FROM album GROUP BY year;
year        COUNT(*)  
----------  ----------
1969        1         
1970        1         
1971        2         
1972        1         
1974        2         
1977        1         
1983        1         
1992        1         
sqlite> SELECT * FROM album ORDER BY year DESC LIMIT 3;
albumid     albumname    year        trackartist
----------  -----------  ----------  -----------
5           Dehumanizer  1992        2          
4           Born Again   1983        2          
10          Animals      1977        5          
sqlite> SELECT albumname, year FROM album WHERE year BETWEEN 1972 AND 1976;
albumname           year      
------------------  ----------
Houses of the Holy  1974      
Burn                1974      
Machine Head        1972      
sqlite> SELECT * FROM album WHERE year IN (1971, 1972, 1973) ORDER BY year DESC, albumname ASC;
albumid     albumname     year        trackartist
----------  ------------  ----------  -----------
9           Machine Head  1972        3          
6           Master of Re  1971        2          
1           Untitled      1971        1          
sqlite> /* =, <>, >, <, >=, <= */
sqlite> SELECT DISTINCT year FROM album WHERE year > 1972 ORDER BY year ASC;
year      
----------
1974      
1977      
1983      
1992      
sqlite> /* % wildcard matches 0+ chars, _ matches single char */
sqlite> /* like is case insensitive */
sqlite> SELECT trackname FROM track WHERE trackname LIKE '%the%';
trackname                
-------------------------
The Song Remains the Same
Zero the Hero            
Into the Void            
sqlite> SELECT trackname FROM track WHERE trackname LIKE '%t_e%';
trackname                
-------------------------
The Song Remains the Same
Zero the Hero            
Into the Void            
Mistreated               
sqlite> SELECT * FROM track WHERE trackname IS NULL;
sqlite> UPDATE track SET trackname='0 the Hero' where trackname='Zero the Hero';
sqlite> SELECT * FROM track;
trackid     trackname   trackartist  trackalbum
----------  ----------  -----------  ----------
1           Black Dog   1            1         
2           The Song R  1            2         
3           Heartbreak  1            3         
4           0 the Hero  2            4         
5           I           2            5         
6           Into the V  2            6         
7           Child in T  3            7         
8           Mistreated  3            8         
9           Highway St  3            9         
sqlite> DELETE FROM track WHERE trackname='0 the Hero';
sqlite> SELECT * FROM track;
trackid     trackname   trackartist  trackalbum
----------  ----------  -----------  ----------
1           Black Dog   1            1         
2           The Song R  1            2         
3           Heartbreak  1            3         
5           I           2            5         
6           Into the V  2            6         
7           Child in T  3            7         
8           Mistreated  3            8         
9           Highway St  3            9         
sqlite> /* inner join will combine rows from different tables if the join condition is true */
sqlite> SELECT artist.artistname, album.albumname, album.year
   ...> FROM artist
   ...> INNER JOIN album ON artist.artistid = album.trackartist
   ...> ORDER BY album.year;
artistname    albumname   year      
------------  ----------  ----------
Led Zeppelin  II          1969      
Deep Purple   Deep Purpl  1970      
Led Zeppelin  Untitled    1971      
Black Sabbat  Master of   1971      
Deep Purple   Machine He  1972      
Led Zeppelin  Houses of   1974      
Deep Purple   Burn        1974      
Pink Floyd    Animals     1977      
Black Sabbat  Born Again  1983      
Black Sabbat  Dehumanize  1992      
sqlite> SELECT artist.artistname, album.albumname, track.trackname, album.year
   ...> FROM artist
   ...> INNER JOIN album ON artist.artistid = album.trackartist
   ...> INNER JOIN track ON album.albumid = track.trackalbum
   ...> ORDER BY album.year;
artistname    albumname   trackname     year      
------------  ----------  ------------  ----------
Led Zeppelin  II          Heartbreaker  1969      
Deep Purple   Deep Purpl  Child in Tim  1970      
Led Zeppelin  Untitled    Black Dog     1971      
Black Sabbat  Master of   Into the Voi  1971      
Deep Purple   Machine He  Highway Star  1972      
Led Zeppelin  Houses of   The Song Rem  1974      
Deep Purple   Burn        Mistreated    1974      
Black Sabbat  Dehumanize  I             1992      
sqlite> /* outer joins do not require the join condition to be met to be included in results */
sqlite> SELECT artist.artistname, album.albumname, album.year
   ...> FROM artist
   ...> LEFT JOIN album ON artist.artistid = album.trackartist
   ...> ORDER BY album.year;
artistname  albumname   year      
----------  ----------  ----------
Rush                              
Led Zeppel  II          1969      
Deep Purpl  Deep Purpl  1970      
Led Zeppel  Untitled    1971      
Black Sabb  Master of   1971      
Deep Purpl  Machine He  1972      
Led Zeppel  Houses of   1974      
Deep Purpl  Burn        1974      
Pink Floyd  Animals     1977      
Black Sabb  Born Again  1983      
Black Sabb  Dehumanize  1992      
sqlite> DROP TABLE track;
sqlite> .tables
album   artist
sqlite> .quit
$ rm test.db
$ sqlite3 test.db
SQLite version 3.31.1 2020-01-27 19:55:54
Enter ".help" for usage hints.
sqlite> .tables
sqlite> .read ./music.sql
sqlite> .tables
album   artist  track 
sqlite> SELECT COUNT(*) FROM track;
9
sqlite>
```
