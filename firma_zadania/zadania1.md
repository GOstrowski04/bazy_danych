# Zadanie 1
Wyświetl imię i nazwisko każdego pracownika i jego rok urodzenia.
```sql
select imie, nazwisko, data_urodzenia from pracownik;
```
# Zadanie 2
Wyświetl imię i nazwisko pracowników oraz ich wiek w latach (bez uwzględniania miesiąca i dnia urodzenia).
```sql
select imie, nazwisko, (year(now())-year(data_urodzenia)) as wiek from pracownik;
```
# Zadanie 3
Wyświetl nazwę działu i liczbę pracowników przypisanych do każdego z nich.
```sql
select dzial.nazwa, count(pracownik.id_pracownika) as ilosc_pracownikow from dzial
inner join pracownik on dzial.id_dzialu = pracownik.dzial group by dzial.id_dzialu;
```
# Zadanie 4
Wyświetl nazwę kategorii oraz liczbę produktów w każdej z nich.
```sql
select nazwa_kategori, count(id_towaru) as ilosc_produktow from kategoria
inner join towar on kategoria.id_kategori = towar.kategoria group by id_kategori;
```
# Zadanie 5
Wyświetl nazwę kategorii i w kolejnej kolumnie listę wszystkich produktów należącej do każdej z nich.
```sql
select nazwa_kategori, group_concat(towar.nazwa_towaru SEPARATOR ', ') as ilosc_produktow from kategoria 
inner join towar on kategoria.id_kategori = towar.kategoria group by id_kategori;
```
# Zadanie 6
Wyświetl średnie zarobki pracowników za zaokrągleniem do 2 miejsc po przecinku.
```sql
select round(avg(pensja), 2) as srednia_pensja from pracownik;
```
# Zadanie 7
Wyświetl średnie zarobki pracowników, którzy pracują co najmniej od 5 lat.\
```sql
select round(avg(pensja), 2) as srednia_pensja from pracownik where (year(now()) - year(data_zatrudnienia)) >= 5;
```
# Zadanie 8
Wyświetl 10 najczęściej sprzedawanych produktów.
```sql
select nazwa_towaru, count(pozycja_zamowienia.id_pozycji) as ilosc_sprzedanych from towar 
inner join pozycja_zamowienia on towar.id_towaru = pozycja_zamowienia.towar 
group by nazwa_towaru order by count(pozycja_zamowienia.id_pozycji) DESC LIMIT 10;
```
# Zadanie 9
Wyświetl numer zamówienia, jego wartość (suma wartości wszystkich jego pozycji) zarejestrowanych w pierwszym kwartale 2017 roku.
```sql
select z.id_zamowienia, sum(pz.cena * pz.ilosc) as suma_wartosci , z.data_zamowienia from zamowienie z
inner join pozycja_zamowienia pz on z.id_zamowienia = pz.zamowienie
group by z.id_zamowienia having z.data_zamowienia between '2017-01-01' and '2017-03-31';
```
# Zadanie 10
Wyświetl imie, nazwisko i sumę wartości zamówień, które dany pracownik dodał. Posortuj malejąco po sumie.
```sql
select imie, nazwisko, sum(pz.cena * pz.ilosc) from pracownik p 
inner join zamowienie z on p.id_pracownika = z.pracownik_id_pracownika
inner join pozycja_zamowienia pz on z.id_zamowienia = pz.zamowienie group by p.id_pracownika;
```
