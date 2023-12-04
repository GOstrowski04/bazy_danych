```sql
select sum(waga) from kreatura; # suma wag kreatur
select count(waga) from kreatura; # ilosc elementow, bez null
select avg(waga) from kreatura; # średnia wartość waga
select min/max(waga) from kreatura; # minimalna/maksymalna wartość
```

# Zadanie 1
### a) wyświetl średnią wagę wikingów
```sql
select avg(waga) from kreatura where rodzaj='wiking';
```
### b) wyświetl średnią wagę, oraz liczbę kreatur dla każdego rodzaju
```sql
select rodzaj, avg(waga), count(*) from kreatura group by rodzaj;
```
### c) wyświetl średni wiek dla każdego rodzaju kreatury
```sql
select rodzaj, avg(year(now()) - year(dataUr)) from kreatura group by rodzaj;
```

# Zadanie 2
### a) dla każdego rodzaju zasobu wyświetlić sumę wag tego zasobu
```sql
select rodzaj, sum(waga*ilosc) from zasob group by rodzaj;
```
### b) dla każdej nazwy zasobu wyświetlić średnią wagę, jeśli jest równa co najmniej 4, oraz jeśli ta suma wag jest większa od 10
```sql
select nazwa, avg(waga*ilosc) as sredniaWaga from zasob group by nazwa having (avg(waga*ilosc) >= 4 and sum(waga*ilosc) > 10);
```
### c) wyświetlić ile jest różnych nazw dla każdego rodzaju zasobu, jeśli minimalna liczba zasobu jest większa od 1
```sql
select rodzaj, count(nazwa) as ileNazw from zasob group by rodzaj having min(ilosc) > 1;
```

# Zadanie 3
### a) wyświetlić dla każdej kreatury ilości zasobów jakie niesie
```sql
select Nazwa, sum(ekwipunek.ilosc) as iloscNiesionychZasobow from kreatura join ekwipunek on kreatura.idKreatury = ekwipunek.idKreatury group by Nazwa;
```
### b) wyświetlić dla każdej kreatury nazwy zasobów jakie posiada
```sql
select kreatura.*, zasob.nazwa from kreatura join ekwipunek on kreatura.idKreatury = ekwipunek.idKreatury join zasob on ekwipunek.idZasobu = zasob.idZasobu;
```
### c) wyświetlić kreatury, które nie posiadają żadnego ekwipunku
```sql
select kreatura.* from kreatura left join ekwipunek on kreatura.idKreatury = ekwipunek.idKreatury where ekwipunek.idKreatury is null;
# lub
select idKreatury from kreatura where idKreatury not in (select idKreatury from ekwipunek where idKreatury is not null)
```

# Zadanie 4
### a) wyświetlić nazwy wikingów, którzy urodzili się w latach 70-tych XVII wieku oraz nazwy zasobów, które posiadają (użyj natural joina jeśli się da)
```sql
select kreatura.*, zasob.nazwa from kreatura natural join ekwipunek join zasob on ekwipunek.idZasobu = zasob.idZasobu having (year(dataUr) between 1670 and 1679) and kreatura.rodzaj = 'wiking';
```
### b) wyświetlić nazwy 5 najmłodszych kreatur, które w ekwipunku posiadają jedzenie
```sql
select distinct kreatura.nazwa from kreatura join ekwipunek on ekwipunek.idKreatury = kreatura.idKreatury join zasob on ekwipunek.idZasobu = zasob.idZasobu where zasob.rodzaj = 'jedzenie' order by kreatura.dataUr asc limit 5;
```
### c) wypisz obok siebie nazwy kreatur, których numer idKreatury różni się o 5 (np. Bjorn - Astrid, Brutal - Ibra itd.)
```sql
select concat(k2.nazwa, ' - ', k1.nazwa) from kreatura k1 join kreatura k2 on k1.idKreatury = k2.idKreatury + 5;
```
