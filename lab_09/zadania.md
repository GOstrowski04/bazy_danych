# Zadanie 1
### a)
```sql
DELIMITER //
CREATE TRIGGER kreatura_before_insert 
before insert on kreatura
FOR EACH ROW
BEGIN
  IF NEW.waga <= 0
  THEN
    SET NEW.waga = 1;
  END IF;
END
//
DELIMITER ;
```
# Zadanie 2
### a)
```sql
# INSERT -> NEW
# UPDATE -> OLD oraz NEW
# DELETE -> OLD
create table archiwum_wypraw like wyprawa;
alter table archiwum_wypraw modify kierownik varchar(100);
insert into wyprawa values (4, "Test", '1700-08-08', '1700-08-10', 1)
DELIMITER //
CREATE TRIGGER wyprawa_after_delete
after delete on wyprawa
FOR EACH ROW
BEGIN
INSERT INTO archiwum_wypraw select w.id_wyprawy, w.nazwa, w.data_rozpoczecia, w.data_zakonczenia, k.nazwa from wyprawa w inner join kreatura k on k.idKreatury = w.kierownik where id_wyprawy = old.id_wyprawy;
END
//
```
