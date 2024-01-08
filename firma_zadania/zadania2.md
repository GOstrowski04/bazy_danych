# Zadanie 1
Wyświetl nazwę działu i minimalną, maksymalną i średnią wartość pensji w każdym dziale.
```sql
select d.nazwa, min(p.pensja) as minimalna, max(p.pensja) as maksymalna, avg(p.pensja) as srednia from dzial d 
inner join pracownik p on p.dzial = d.id_dzialu group by d.id_dzialu;
```
# Zadanie 2
Wyświetl pełną nazwę klienta, wartość zamówienia dla 10 najwyższych wartości zamówienia.
```sql
select k.pelna_nazwa, sum(pz.cena * pz.ilosc) as wartosc from klient k 
inner join zamowienie z on k.id_klienta = z.klient
inner join pozycja_zamowienia pz on z.id_zamowienia = pz.zamowienie
group by z.id_zamowienia order by sum(pz.cena* pz.ilosc) desc limit 10;
```
# Zadanie 3
Wyświetl wartość przychodu dla każdego roku. Dane posortuj malejąco według sumy wartości zamówień.
```sql
select year(z.data_zamowienia) as rok, sum(pz.ilosc * pz.cena) as przychód from zamowienie z
inner join pozycja_zamowienia pz on z.id_zamowienia = pz.zamowienie
group by year(z.data_zamowienia)
order by sum(pz.ilosc * pz.cena) desc;
```
# Zadanie 4
Wyświetl sumę wartości wszystkich anulowanych zamówień.
```sql
select z.id_zamowienia, z.status_zamowienia, sum(pz.ilosc * pz.cena) as wartosc from zamowienie z
inner join pozycja_zamowienia pz on z.id_zamowienia = pz.zamowienie
group by z.id_zamowienia having z.status_zamowienia = 6;
```
# Zadanie 5
Wyświetl liczbę zamówień i sumę zamówień dla każdego miasta z podstawowego adresu klientów.
```sql
select a.miejscowosc, count(z.id_zamowienia) as ilosc_zamowien, sum(pz.ilosc * pz.cena) as suma_zamowien from adres_klienta a 
inner join klient k on a.klient = k.id_klienta
inner join zamowienie z on z.klient = k.id_klienta
inner join pozycja_zamowienia pz on pz.zamowienie = z.id_zamowienia
group by a.miejscowosc;
```
# Zadanie 6
Wyświetl dotychczasowy dochód firmy biorąc pod uwagę tylko zamówienia zrealizowane.
```sql
select sum(pz.ilosc * pz.cena) as przychód from zamowienie z
inner join pozycja_zamowienia pz on z.id_zamowienia = pz.zamowienie
where z.status_zamowienia = 5;
```
# Zadanie 7
Policz i wyświetl dochód (przychód z zamówień i cena zakupu towaru) w każdym roku działalności firmy.
```sql
select month(z.data_zamowienia) as miesiąc, sum((pz.ilosc * pz.cena) - (t.cena_zakupu))  as dochód from zamowienie z
inner join pozycja_zamowienia pz on z.id_zamowienia = pz.zamowienie
inner join towar t on t.id_towaru = pz.towar
group by month(z.data_zamowienia);
```
# Zadanie 8
Wyświetl wartość aktualnego stanu magazynowego z podziałem na kategorię produktów.
```sql
select k.nazwa_kategori, sum(t.cena_zakupu*sm.ilosc) as wartosc_stanu from kategoria k
inner join towar t on k.id_kategori = t.kategoria
inner join stan_magazynowy sm on t.id_towaru = sm.towar
group by k.id_kategori;
```
# Zadanie 9
Przygotuj zapytanie, które wyświetli dane w poniższej postaci (policz ilu pracowników urodziło się w danym miesiącu - uwaga na porządek sortowania).
```sql
select monthname(p.data_urodzenia) as Miesiąc, count(p.id_pracownika) as Liczba_pracowników from pracownik p 
group by monthname(p.data_urodzenia), month(p.data_urodzenia) order by month(p.data_urodzenia);
```
# Zadanie 10
Wyświetl imię i nazwisko pracownika i koszt jaki poniósł pracodawca od momentu jego zatrudnienia.
