## regex
```sql
# . - dokładnie jeden znak
# regexp contains jest automatycznie
select * from postac where nazwa regexp '.a.';
# kod pocztowy '__-___'
select * from postac where nazwa regexp '[0-9]{1,2}-[0-9]{3}';
# [0-9] cyfry od 0 do 9
# [a-k] - litery od a do k
# [aoiuey] - jeden ze znaków
#{n} - dokładnie n razy
#{n,m} - co najmniej n razy, nie więcej jak m razy
#{n,} - co najmniej n razy
```
## Zadanie 1
### a) uśmierć dwóch najstarszych wikingów nie licząc Bjorna
```sql
select * from postac where rodzaj='wiking' and nazwa != 'Bjorn' order by wiek desc;
delete from postac where id_postaci in (6,7);
```
### b) usuń klucz główny z tabeli postać
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
### a) do tabeli postać dodaj pole pesel składające się z 11 znaków i ustaw to pole jako klucz główny
```sql
alter table postac add pesel char(11) first;
select * from postac;
update postac set pesel='17763874635' where id_postaci=1;
update postac set pesel='17763874635'+ id_postaci;
alter table postac add primary key (pesel);
```
### b) w tabeli postać zmień pole rodzaj tak, aby było możliwe dodanie rodzaju syrena
```sql
alter table postac modify rodzaj enum('wiking', 'ptak', 'kobieta', 'syrena');
```
### c) wstaw do tabeli postac syrenę o nazwie Gertruda Nieszczera
```sql
insert into postac values(default,7, 'Gertruda Nieszczera', 'syrena', '1000-04-15', 1000, null, null);
```
## Zadanie 3
### a) wszystkie postacie które mają w nazwie 'a' wsadź na statek bjorna
```sql
# % - dowolny ciąg znaków o dowolnej długości
update postac set statek='statek1' where nazwa LIKE '%a%';
# _ - dokładnie jeden znak
select * from postac where nazwa LIKE '_j%';
```
### b) zmniejsz ładowność o 30% statkom, które miały date  wodowanie w XX wieku
```sql
#przykład 1
select * from statek where data_wodowania >= '1901-01-01' and data_wodowania <= '2000-12-31';
#przykład 2
select * from statek where data_wodowania between '1901-01-01' and '2000-12-31';
#przykład 3
select * from statek where year(data_wodowania) between 1901 and 2000;

update statek set max_ladownosc = 0.7 * max_ladownosc where year(data_wodowania) between 1901 and 2000;
```
### c) ustaw warunek sprawdzający czy wiek jest mniejszy od 1000
```sql
alter table postac modify wiek int unsigned check (wiek < 1000);
#lub
alter table postac add check (wiek < 1000);
```
## Zadanie 4
### a) do postaci dodaj węża Loko, nie wsadzaj go na statek
```sql
alter table postac modify rodzaj enum('wiking', 'ptak', 'kobieta', 'syrena', 'wąż');
insert into postac values(default,9, 'Loko', 'wąż', '1500-01-11', 499, null, null);
```
### b) stwórz nową tabelę marynarz na podstawie tabeli postac(takie same pola), wrzuć do tej tabeli wszystkie postacie z zdefiniowanym statkiem
```sql
create table marynarz as select * from postac;
#lub
create table marynarz like postac;
select * from marynarz;
insert into marynarz select * from postac where statek is not null;
```
### c) dostosuj klucze
```sql
alter table marynarz add foreign key (statek) references statek(nazwa_statku);
```
## Zadanie 5
dokończyć
```sql
#Zadanie 5
delete from postac where nazwa = 'wiking2';
delete from statek;
drop table statek;
create table zwierz(id int primary key auto_increment, nazwa varchar(200), wiek int unsigned);
insert into zwierz select * from postac where rodzaj='ptak' or rodzaj='wąż';
```
