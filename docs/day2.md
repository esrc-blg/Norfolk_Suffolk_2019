# The Application of SQL 


## SELECT Statement: with Cout

```sql
  SELECT count(DISTINCT `Overall Crime Category`)
FROM table_crimerecords
WHERE `Victim Gender` LIKE 'FEMALE' AND `Victim age band` = '20-29';
```

Output: 
```

+------------------------------------------+
| count(DISTINCT `Overall Crime Category`) |
+------------------------------------------+
|  8                                       |
+------------------------------------------+

```

