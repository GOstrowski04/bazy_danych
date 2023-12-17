# ZADANIE 1
### a)
```sql
create table kreatura as select * from wikingowie.kreatura;
create table uczestnicy as select * from wikingowie.uczestnicy;
create table etapy_wyprawy as select * from wikingowie.kreatura;
create table sektor as select * from wikingowie.sektor;
create table wyprawa as select * from wikingowie.wyprawa;
```
### b)
```sql
SELECT * FROM kreatura OUTER JOIN wyprawa ON kreatura.idKreatury = wyprawa.idKreatury where wyprawa.idKreatury is null;
```
### c)
```sql

```

# ZADANIE 2
### a)
```sql
SELECT nazwa, liczba_uczestnikow, group_concat(uczestnicy.nazwa SEPARATOR ', ') FROM wyprawa join uczestnicy on wyprawa.idWyprawy = uczestnicy.idWyprawy
```


# Zadanie 3
### a)
```sql
Select nazwa, ifNull(count(wyprawa.idSektoru), 0) FROM sektor outer join wyprawa on sektor.idSektoru = wyprawa.idSektoru group by nazwa;
```
### b)
```sql
Select nazwa, ifNull(count(wyprawa.idKreatury), 0) FROM kreatura outer join wyprawa on kreatura.idKreatury = wyprawa.idKreatury group by nazwa;
```

# Zadanie 4
### a)
