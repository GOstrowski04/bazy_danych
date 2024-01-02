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
```
### c)
```sql
```

# ZADANIE 2
### a)
```sql
SELECT wyprawa.nazwa, count(id_uczestnika), group_concat(kreatura.nazwa SEPARATOR ', ') FROM wyprawa join uczestnicy on wyprawa.id_wyprawy = uczestnicy.id_wyprawy join kreatura on uczestnicy.id_uczestnika = kreatura.idKreatury group by wyprawa.nazwa;
```
### b)
```sql
select idEtapu, sektor.nazwa, kolejnosc, wyprawa.data_rozpoczecia, kreatura.nazwa, dziennik from etapy_wyprawy 
join wyprawa on etapy_wyprawy.idWyprawy = wyprawa.id_wyprawy 
join kreatura on wyprawa.kierownik = kreatura.idKreatury 
join sektor on etapy_wyprawy.sektor = sektor.id_sektora 
order by wyprawa.data_rozpoczecia asc, etapy_wyprawy.kolejnosc asc;
```
# Zadanie 3
### a)
```sql
select sektor.nazwa, count(etapy_wyprawy.sektor) from sektor left outer join etapy_wyprawy on sektor.id_sektora = etapy_wyprawy.sektor group by sektor.nazwa;
```
### b)
```sql
select idKreatury, kreatura.nazwa, if(count(id_wyprawy) > 0, "Brał udział w wyprawie.", "Nie brał udziału w wyprawie") from kreatura
left outer join uczestnicy on kreatura.idKreatury = uczestnicy.id_uczestnika
group by idKreatury, kreatura.nazwa;
```

# Zadanie 4
### a)
```sql
select wyprawa.nazwa, sum(length(etapy_wyprawy.dziennik)) from wyprawa
join etapy_wyprawy on wyprawa.id_wyprawy = etapy_wyprawy.idWyprawy
group by wyprawa.nazwa having (sum(length(etapy_wyprawy.dziennik)) < 400);
```
### b)
```sql
select wyprawa.nazwa, sum(zasob.waga*ekwipunek.ilosc)/count(distinct uczestnicy.id_uczestnika) as srednia from wyprawa 
join uczestnicy on wyprawa.id_wyprawy = uczestnicy.id_wyprawy 
join kreatura on uczestnicy.id_uczestnika = kreatura.idKreatury
join ekwipunek on kreatura.idKreatury = ekwipunek.idKreatury
join zasob on ekwipunek.idZasobu = zasob.idZasobu 
group by wyprawa.nazwa;
```
# Zadanie 5
### a)
```sql
select kreatura.nazwa, datediff(wyprawa.data_rozpoczecia, kreatura.dataUr) as wiek_w_dniach from kreatura 
join uczestnicy on kreatura.idKreatury = uczestnicy.id_uczestnika
join wyprawa on uczestnicy.id_wyprawy = wyprawa.id_wyprawy
join etapy_wyprawy on wyprawa.id_wyprawy = etapy_wyprawy.idWyprawy
group by kreatura.nazwa having count(etapy_wyprawy.sektor = 7) > 0;
```
