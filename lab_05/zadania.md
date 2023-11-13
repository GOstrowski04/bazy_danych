## Zadanie 1
### a)
```sql
select * from postac where rodzaj='wiking' and nazwa != 'Bjorn' order by wiek desc;
delete from postac where id_postaci in (6,7);
```
### b)
```sql
#krok 1
alter table walizka drop foreign key walizka_ibfk_1;
alter table przetwory drop foreign key przetwory_ibfk_1;
alter table przetwory drop foreign key przetwory_ibfk_2;
#krok 2 - pozbycie się atrybutu auto_increment
alter table postac modify id_postaci int;
#krok 3 - usunięcie klucza głównego
alter table postac drop primary key;
```
## Zadanie 2
### a)
```sql
alter table postac add pesel char(11) first;
select * from postac;
update postac set pesel='17763874635' where id_postaci=1;
update postac set pesel='17763874635'+ id_postaci;
alter table postac add primary key (pesel);
```
### b)
```sql
alter table postac modify rodzaj enum('wiking', 'ptak', 'kobieta', 'syrena');
```
### c)
```sql
insert into postac values('17763874635'+ id_postaci,
