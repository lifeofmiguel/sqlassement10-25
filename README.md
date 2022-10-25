# sqlassement10-25
```
insert into Movies VALUES('A Nightmare on Elm Street', 91, 'Horror', 7.4, 'R');
insert into Movies VALUES('Scream 5', 114, 'Horror', 6.3, 'R');

select * from Movies;
+---------------------------+---------+-------------+-----------+--------+
| Title                     | runtime | Genre       | IMBDScore | Rating |
+---------------------------+---------+-------------+-----------+--------+
| A Nightmare on Elm Street |      91 | Horror      |      7.40 | R      |
| Howard the Duck           |     100 | Sci-Fi      |      4.60 | PG     |
| Lavalantula               |      83 | Horror      |      4.70 | TV-14  |
| Monsters Inc.             |      92 | Animation   |      8.10 | G      |
| Scream 5                  |     114 | Horror      |      6.30 | R      |
| Spaceballs                |      96 | Comedy      |      7.10 | PG     |
| Waltz with Bashir         |      90 | Documentary |      8.00 | R      |
+---------------------------+---------+-------------+-----------+--------+

select * from Movies WHERE Genre = "Sci-Fi";
+-----------------+---------+--------+-----------+--------+
| Title           | runtime | Genre  | IMBDScore | Rating |
+-----------------+---------+--------+-----------+--------+
| Howard the Duck |     100 | Sci-Fi |      4.60 | PG     |
+-----------------+---------+--------+-----------+--------+

select * from Movies WHERE IMBDScore >= 6.5;
+---------------------------+---------+-------------+-----------+--------+
| Title                     | runtime | Genre       | IMBDScore | Rating |
+---------------------------+---------+-------------+-----------+--------+
| A Nightmare on Elm Street |      91 | Horror      |      7.40 | R      |
| Monsters Inc.             |      92 | Animation   |      8.10 | G      |
| Spaceballs                |      96 | Comedy      |      7.10 | PG     |
| Waltz with Bashir         |      90 | Documentary |      8.00 | R      |
+---------------------------+---------+-------------+-----------+--------+

select * from Movies WHERE runtime <= 100 AND Rating = 'G' or Rating = 'PG';
+-----------------+---------+-----------+-----------+--------+
| Title           | runtime | Genre     | IMBDScore | Rating |
+-----------------+---------+-----------+-----------+--------+
| Howard the Duck |     100 | Sci-Fi    |      4.60 | PG     |
| Monsters Inc.   |      92 | Animation |      8.10 | G      |
| Spaceballs      |      96 | Comedy    |      7.10 | PG     |
+-----------------+---------+-----------+-----------+--------+

select Genre, AVG(runtime) as AVG_runtime FROM Movies where IMBDScore <= 7.5 GROUP BY Genre;
+--------+-------------+
| Genre  | AVG_runtime |
+--------+-------------+
| Horror |     96.0000 |
| Sci-Fi |    100.0000 |
| Comedy |     96.0000 |
+--------+-------------+

UPDATE Movies set Rating = 'R' where Title = 'Starship Troopers';
+---------------------------+---------+-------------+-----------+--------+
| Title                     | runtime | Genre       | IMBDScore | Rating |
+---------------------------+---------+-------------+-----------+--------+
| A Nightmare on Elm Street |      91 | Horror      |      7.40 | R      |
| Howard the Duck           |     100 | Sci-Fi      |      4.60 | PG     |
| Lavalantula               |      83 | Horror      |      4.70 | TV-14  |
| Monsters Inc.             |      92 | Animation   |      8.10 | G      |
| Scream 5                  |     114 | Horror      |      6.30 | R      |
| Spaceballs                |      96 | Comedy      |      7.10 | PG     |
| Starship Troopers         |     129 | Sci-Fi      |      7.20 | R      |
| Waltz with Bashir         |      90 | Documentary |      8.00 | R      |
+---------------------------+---------+-------------+-----------+--------+

select ID, Rating from Movies WHERE Genre = 'Horror' or Genre = 'Documentary';
+------+--------+
| ID   | Rating |
+------+--------+
|    2 | R      |
|    3 | TV-14  |
|    5 | R      |
|    8 | R      |
+------+--------+

select max(IMBDScore) as MaxScore, avg(IMBDScore) as AvgScore, Min(IMBDScore) as MinScore from Movies;
+----------+----------+----------+
| MaxScore | AvgScore | MinScore |
+----------+----------+----------+
|     8.10 | 6.675000 |     4.60 |
+----------+----------+----------+

select max(IMBDScore) as MaxScore, avg(IMBDScore) as AvgScore, Min(IMBDScore) as MinScore from Movies group by Rating HAVING COUNT(*) > 1;
+----------+----------+----------+
| MaxScore | AvgScore | MinScore |
+----------+----------+----------+
|     8.00 | 7.225000 |     6.30 |
|     7.10 | 5.850000 |     4.60 |
+----------+----------+----------+

Delete from Movies where rating = 'R';
+-----------------+---------+-----------+-----------+--------+------+
| Title           | runtime | Genre     | IMBDScore | Rating | ID   |
+-----------------+---------+-----------+-----------+--------+------+
| Howard the Duck |     100 | Sci-Fi    |      4.60 | PG     |    1 |
| Lavalantula     |      83 | Horror    |      4.70 | TV-14  |    3 |
| Monsters Inc.   |      92 | Animation |      8.10 | G      |    4 |
| Spaceballs      |      96 | Comedy    |      7.10 | PG     |    6 |
+-----------------+---------+-----------+-----------+--------+------+
```
