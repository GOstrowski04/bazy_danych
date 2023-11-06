# Tytuł
## Poziom 2
###### Poziom 6

Lista zadań do wykonania:
* todo 1
* todo 2
  * todo 2.1

1. Rozdział 1
2. Rozdział 2
  2.1 Rozdział 2.1

**Listing 1** -> pogrubienie  
_Listing 2_ -> kursywa  
**_Listing 3_**  
  
Blok kodu
```sql
SELECT * FROM osoba;
```
Kod umieszczany liniowo. Polecenie `SELECT` oznacza wybranie danych z bazy.

```sql
describe postac;
create table postac();
alter table walizka alter kolor set default "rozowy";
show create table walizka;
update postac set id_postaci=2 where id_postaci=3;
insert into postac() values();

create table izba (
adres_budynku varchar(100),
nazwa_izby varchar(100),
primary key(adres_budynku, nazwa_izby),
metraz int unsigned,
wlasciciel int,
foreign key (wlasciciel) references postac(id_postaci) on delete set null
);
```
