# query-palestra
Importo le query mostrate a lezione effettuate nel mio database 'palestra'.



show tables;
+--------------------+
| Tables_in_palestra |
+--------------------+
| esercizio          |
| Persona            |
| svolge             |
+--------------------+
3 rows in set (0,001 sec)

select * from Persona;
+------------+---------+-----+-----------------+
| id_persona | Nome    | Eta | Massa_muscolare |
+------------+---------+-----+-----------------+
|       2244 | Verdi   |  28 |              78 |
|       3355 | Galli   |  31 |              82 |
|       4076 | Mori    |  45 |              90 |
|       4466 | Costa   |  39 |              70 |
|       5577 | Romani  |  36 |              65 |
|       5698 | Bruni   |  43 |              72 |
|       5998 | Bianchi |  37 |              69 |
|       7309 | Rossi   |  34 |              85 |
|       8123 | Lupi    |  46 |              60 |
|       9553 | Neri    |  42 |              75 |
+------------+---------+-----+-----------------+
10 rows in set (0,001 sec)

select * from esercizio;
+----------------+------------------+--------------+
| nome           | gruppo_muscolare | ID_esercizio |
+----------------+------------------+--------------+
| Push up        | petto            |         1001 |
| Leg press      | gambe            |         1002 |
| Squat          | gambe            |         1003 |
| Bicep curl     | braccia          |         1004 |
| Shoulder press | spalle           |         1005 |
| Plank          | addome           |         1006 |
| Deadlift       | schiena          |         1007 |
| Tricep dip     | braccia          |         1008 |
| Lat pull-down  | schiena          |         1009 |
| Lunge          | gambe            |         1010 |
+----------------+------------------+--------------+
10 rows in set (0,001 sec)

select * from svolge;
Empty set (0,002 sec)

 INSERT INTO svolge (id_persona, id_esercizio, Peso_usato, Ripetizioni, Data) VALUES
     (7309, 1001, 0, 20, '2026-01-25'),     -- Rossi fa Push up
     (5998, 1002, 120, 12, '2026-01-25'),   -- Bianchi fa Leg press
     (9553, 1003, 80, 15, '2026-01-26'),    -- Neri fa Squat
     (5698, 1004, 25, 12, '2026-01-26'),    -- Bruni fa Bicep curl
     (4076, 1005, 20, 10, '2026-01-27'),    -- Mori fa Shoulder press
     (8123, 1006, 0, 60, '2026-01-27'),     -- Lupi fa Plank
     (2244, 1007, 90, 8, '2026-01-28'),     -- Verdi fa Deadlift
     (3355, 1008, 15, 12, '2026-01-28'),    -- Galli fa Tricep dip
     (4466, 1009, 60, 10, '2026-01-29'),    -- Costa fa Lat pull-down
     (5577, 1010, 50, 12, '2026-01-29');
Query OK, 10 rows affected (0,002 sec)
Records: 10  Duplicates: 0  Warnings: 0

select*from svolge;
+-----------+------------+--------------+------------+-------------+------------+
| id_svolge | id_persona | id_esercizio | Peso_usato | Ripetizioni | Data       |
+-----------+------------+--------------+------------+-------------+------------+
|         1 |       7309 |         1001 |       0.00 |          20 | 2026-01-25 |
|         2 |       5998 |         1002 |     120.00 |          12 | 2026-01-25 |
|         3 |       9553 |         1003 |      80.00 |          15 | 2026-01-26 |
|         4 |       5698 |         1004 |      25.00 |          12 | 2026-01-26 |
|         5 |       4076 |         1005 |      20.00 |          10 | 2026-01-27 |
|         6 |       8123 |         1006 |       0.00 |          60 | 2026-01-27 |
|         7 |       2244 |         1007 |      90.00 |           8 | 2026-01-28 |
|         8 |       3355 |         1008 |      15.00 |          12 | 2026-01-28 |
|         9 |       4466 |         1009 |      60.00 |          10 | 2026-01-29 |
|        10 |       5577 |         1010 |      50.00 |          12 | 2026-01-29 |
+-----------+------------+--------------+------------+-------------+------------+
10 rows in set (0,001 sec)


SELECT Peso_usato, COUNT(*) FROM svolge
     group by Peso_usato;
+------------+----------+
| Peso_usato | COUNT(*) |
+------------+----------+
|       0.00 |        2 |
|     120.00 |        1 |
|      80.00 |        1 |
|      25.00 |        1 |
|      20.00 |        1 |
|      90.00 |        1 |
|      15.00 |        1 |
|      60.00 |        1 |
|      50.00 |        1 |
+------------+----------+
9 rows in set (0,001 sec)

SELECT * FROM svolge
    order by Ripetizioni desc;
+-----------+------------+--------------+------------+-------------+------------+
| id_svolge | id_persona | id_esercizio | Peso_usato | Ripetizioni | Data       |
+-----------+------------+--------------+------------+-------------+------------+
|         6 |       8123 |         1006 |       0.00 |          60 | 2026-01-27 |
|         1 |       7309 |         1001 |       0.00 |          20 | 2026-01-25 |
|         3 |       9553 |         1003 |      80.00 |          15 | 2026-01-26 |
|         2 |       5998 |         1002 |     120.00 |          12 | 2026-01-25 |
|         4 |       5698 |         1004 |      25.00 |          12 | 2026-01-26 |
|         8 |       3355 |         1008 |      15.00 |          12 | 2026-01-28 |
|        10 |       5577 |         1010 |      50.00 |          12 | 2026-01-29 |
|         5 |       4076 |         1005 |      20.00 |          10 | 2026-01-27 |
|         9 |       4466 |         1009 |      60.00 |          10 | 2026-01-29 |
|         7 |       2244 |         1007 |      90.00 |           8 | 2026-01-28 |
+-----------+------------+--------------+------------+-------------+------------+
10 rows in set (0,001 sec)

SELECT Nome, AVG(massa_muscolare) AS MEDIA FROM Persona
    group by Nome
    Having AVG(massa_muscolare)>=78;
+-------+---------+
| Nome  | MEDIA   |
+-------+---------+
| Verdi | 78.0000 |
| Galli | 82.0000 |
| Mori  | 90.0000 |
| Rossi | 85.0000 |
+-------+---------+
4 rows in set (0,001 sec)

SELECT * FROM Persona
    where nome like '%a';
+------------+-------+-----+-----------------+
| id_persona | Nome  | Eta | Massa_muscolare |
+------------+-------+-----+-----------------+
|       4466 | Costa |  39 |              70 |
+------------+-------+-----+-----------------+
1 row in set (0,001 sec)


SELECT * FROM Persona
    where nome like 'b%';
+------------+---------+-----+-----------------+
| id_persona | Nome    | Eta | Massa_muscolare |
+------------+---------+-----+-----------------+
|       5698 | Bruni   |  43 |              72 |
|       5998 | Bianchi |  37 |              69 |
+------------+---------+-----+-----------------+
2 rows in set (0,001 sec)

SELECT * FROM Persona
     where nome like '______';
+------------+--------+-----+-----------------+
| id_persona | Nome   | Eta | Massa_muscolare |
+------------+--------+-----+-----------------+
|       5577 | Romani |  36 |              65 |
+------------+--------+-----+-----------------+
1 row in set (0,001 sec)


select Eta from Persona
     ;
+-----+
| Eta |
+-----+
|  28 |
|  31 |
|  45 |
|  39 |
|  36 |
|  43 |
|  37 |
|  34 |
|  46 |
|  42 |
+-----+
10 rows in set (0,001 sec)



SELECT nome, AVG(eta) FROM Persona
       GROUP BY nome;
+---------+----------+
| nome    | AVG(eta) |
+---------+----------+
| Verdi   |  28.0000 |
| Galli   |  31.0000 |
| Mori    |  45.0000 |
| Costa   |  39.0000 |
| Romani  |  36.0000 |
| Bruni   |  43.0000 |
| Bianchi |  37.0000 |
| Rossi   |  34.0000 |
| Lupi    |  46.0000 |
| Neri    |  42.0000 |
+---------+----------+
10 rows in set (0,001 sec)


SELECT * FROM svolge
    order by Peso_usato ASC;
+-----------+------------+--------------+------------+-------------+------------+
| id_svolge | id_persona | id_esercizio | Peso_usato | Ripetizioni | Data       |
+-----------+------------+--------------+------------+-------------+------------+
|         1 |       7309 |         1001 |       0.00 |          20 | 2026-01-25 |
|         6 |       8123 |         1006 |       0.00 |          60 | 2026-01-27 |
|         8 |       3355 |         1008 |      15.00 |          12 | 2026-01-28 |
|         5 |       4076 |         1005 |      20.00 |          10 | 2026-01-27 |
|         4 |       5698 |         1004 |      25.00 |          12 | 2026-01-26 |
|        10 |       5577 |         1010 |      50.00 |          12 | 2026-01-29 |
|         9 |       4466 |         1009 |      60.00 |          10 | 2026-01-29 |
|         3 |       9553 |         1003 |      80.00 |          15 | 2026-01-26 |
|         7 |       2244 |         1007 |      90.00 |           8 | 2026-01-28 |
|         2 |       5998 |         1002 |     120.00 |          12 | 2026-01-25 |
+-----------+------------+--------------+------------+-------------+------------+
10 rows in set (0,001 sec)





 SELECT COUNT(*) AS tot_persone FROM Persona;
+-------------+
| tot_persone |
+-------------+
|          10 |
+-------------+
1 row in set (0,001 sec)



SELECT * FROM Esercizio
    here gruppo_muscolare ='gambe'
    OR gruppo_muscolare='braccia';
+------------+------------------+--------------+
| nome       | gruppo_muscolare | ID_esercizio |
+------------+------------------+--------------+
| Leg press  | gambe            |         1002 |
| Squat      | gambe            |         1003 |
| Bicep curl | braccia          |         1004 |
| Tricep dip | braccia          |         1008 |
| Lunge      | gambe            |         1010 |
+------------+------------------+--------------+
5 rows in set (0,001 sec)



x
SELECT * FROM Esercizio
    WHERE NOT gruppo_muscolare  = 'Gambe';
+----------------+------------------+--------------+
| nome           | gruppo_muscolare | ID_esercizio |
+----------------+------------------+--------------+
| Push up        | petto            |         1001 |
| Bicep curl     | braccia          |         1004 |
| Shoulder press | spalle           |         1005 |
| Plank          | addome           |         1006 |
| Deadlift       | schiena          |         1007 |
| Tricep dip     | braccia          |         1008 |
| Lat pull-down  | schiena          |         1009 |
+----------------+------------------+--------------+
7 rows in set (0,001 sec)

