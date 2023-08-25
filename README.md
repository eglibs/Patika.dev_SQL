# sql_patika
## SQL Ödev 01 | WHERE ve Karşılaştırma & Mantıksal Operatörler

 

<br>

 

1-) <strong>film </strong>tablosunda bulunan <strong>title</strong> ve <strong>description</strong>
    sütunlarındaki verileri sıralayınız.
 
```
 
SELECT title, description FROM film;

 
```

<br>

2-) <strong>film </strong> tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük <strong>VE</strong> 75 ten küçük 
    olma koşullarıyla sıralayınız. 

```

SELECT * FROM film
WHERE length >= 60 AND length <= 75;

```

<br>

3-) <strong>film </strong> tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 <strong>VE </strong> replacement_cost 12.99 <strong>VEYA </strong> 
    28.99 olma koşullarıyla sıralayınız. 

```

SELECT * FROM film
WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);

```

<br>

4-) <strong>customer </strong> tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir? 

```

SELECT * FROM customer 
WHERE first_name = 'Mary';

```

<br>

5-) <strong>film </strong> tablosundaki uzunluğu (length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN 
    verileri sıralayınız. 

```

SELECT * FROM film
WHERE NOT length > 50 AND NOT (rental_rate = 2.99 OR rental_rate = 4.99);

```


## SQL Ödev 02 | BETWEEN and IN

 
<br>

 
1-) <strong>film </strong> tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma 
    koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
 
```
 
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.98;
 
```

2-) <strong>actor</strong> tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri 
    olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

```
 
SELECT first_name, last_name FROM actor
WHERE first_name IN ('Penelope', 'Nick', 'Ed');
 
```

3-) <strong>film</strong>  tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 
    olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

```
 
SELECT * FROM film
WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);
 
```

## SQL Ödev 03 | LIKE and ILIKE
 

<br>

 
1-) <strong>country</strong> tablosunda bulunan <strong>country</strong> sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 
    'a' karakteri ile sonlananları sıralayınız.
 
```
 
SELECT country FROM country
WHERE country LIKE 'A%a';

 
```
 
2-) <strong>country</strong> tablosunda bulunan <strong>country</strong> sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 
    'n' karakteri ile sonlananları sıralayınız.

```
 
SELECT * FROM country
WHERE country LIKE '%_____n';
 
```

3-) <strong>film</strong> tablosunda bulunan <strong>title</strong> sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf 
    farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

```
 
SELECT * FROM film
WHERE title ILIKE '%t%t%t%t%';

 
```

4-) <strong>film</strong> tablosunda bulunan tüm sütunlardaki verilerden <strong>title</strong> 'C' karakteri ile başlayan ve 
    uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

```
 
SELECT * FROM film
WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;

 
```

## SQL Ödev 04 | DISTINCT and COUNT

 
<br>


1-) <strong>film</strong> tablosunda bulunan <strong>replacement_cost</strong> sütununda bulunan birbirinden farklı değerleri sıralayınız.
 
```
 
SELECT DISTINCT replacement_cost FROM film;

 
```

2-) <strong>film</strong> tablosunda bulunan <strong>replacement_cost</strong> sütununda birbirinden farklı kaç tane veri vardır?

```
 
SELECT COUNT (DISTINCT replacement_cost) FROM film;

 
```

3-) <strong>film</strong> tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

```


SELECT * FROM film
WHERE title LIKE 'T%' AND rating = 'G';

 
```

4-) <strong>country</strong> tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

```
 
SELECT * FROM country
WHERE country LIKE '_____';

 
```

5-) <strong>city</strong> tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

```
 
SELECT * FROM city
WHERE city ILIKE '%R';

 
```

## SQL Ödev 05 

 
<br>


1-) <strong>film</strong> tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
 
```

SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
 
```

2-) <strong>film</strong> tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 
    5 filmi(6,7,8,9,10) sıralayınız.
 
```

SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length ASC
OFFSET 6
LIMIT 5;
 
```

3-) <strong>customer</strong> tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

```

SELECT * FROM customer
WHERE store_id = 1 
ORDER BY last_name DESC
LIMIT 4;
 
```

## SQL Ödev 06 

 
<br>


1-) <strong>film</strong> tablosunda bulunan <strong>rental_rate</strong> sütunundaki değerlerin ortalaması nedir?
 
```

SELECT AVG(rental_rate) FROM film;
 
```

2-) <strong>film</strong> tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

```

SELECT COUNT(*) FROM film
WHERE title LIKE 'C%';
 
```

3-) <strong>film</strong> tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

```

SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;

```

4-) <strong>film</strong> tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

```

SELECT DISTINCT replacement_cost FROM film
WHERE length > 150;

```

## SQL Ödev 07 

 
<br>


1-) <strong>film</strong> tablosunda bulunan filmleri <strong>rating</strong> değerlerine göre gruplayınız.
 
```

SELECT rating FROM film
GROUP BY rating;
 
```

2-) <strong>film</strong> tablosunda bulunan filmleri <strong>replacement_cost</strong> sütununa göre grupladığımızda film sayısı 50 den fazla olan 
replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
 
```

SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;
 
```

3-) <strong>customer</strong> tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 

```

SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;
 
```

4-) City tablosunda bulunan şehir verilerini <strong>country_id</strong> sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id
bilgisini ve şehir sayısını paylaşınız.

```

SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;
 
``` 

## SQL Ödev 08 

 
<br>


1-) <strong>test</strong> veritabanınızda <strong>employee</strong> isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan 
bir tablo oluşturalım.
 
```

CREATE TABLE employee (
	id INTEGER PRIMARY KEY,
	name VARCHAR(50) NOT NULL,
	birthday DATE,
	email VARCHAR(100)
);
 
```

2-) Oluşturduğumuz <strong>employee</strong> tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
 
```

insert into employee (id, name, birthday, email) values (1, 'Thekla', '1924-05-08', 'tlittledyke0@a8.net');
insert into employee (id, name, birthday, email) values (2, 'Anderea', '1953-06-04', 'adulling1@wix.com');
insert into employee (id, name, birthday, email) values (3, 'Minnie', '1938-09-19', 'mkupper2@dion.ne.jp');
insert into employee (id, name, birthday, email) values (4, 'Hyacinthie', '1958-04-04', 'hsimmings3@cisco.com');
insert into employee (id, name, birthday, email) values (5, 'Michel', '1952-11-08', 'mhankin4@unicef.org');
insert into employee (id, name, birthday, email) values (6, 'Maddy', '1931-07-11', 'mingyon5@chron.com');
insert into employee (id, name, birthday, email) values (7, 'Alexina', '1965-08-16', null);
insert into employee (id, name, birthday, email) values (8, 'Keen', '1982-04-19', null);
insert into employee (id, name, birthday, email) values (9, 'Rees', '1945-01-17', 'respina8@google.it');
insert into employee (id, name, birthday, email) values (10, 'Pauly', '1942-01-27', 'phughs9@deliciousdays.com');
insert into employee (id, name, birthday, email) values (11, 'Glad', '1991-11-07', null);
insert into employee (id, name, birthday, email) values (12, 'Lazarus', '1944-10-30', 'ljessoppb@macromedia.com');
insert into employee (id, name, birthday, email) values (13, 'Mabel', '1992-10-05', 'mostickc@tumblr.com');
insert into employee (id, name, birthday, email) values (14, 'Tobe', '1924-05-22', 'taaronsd@whitehouse.gov');
insert into employee (id, name, birthday, email) values (15, 'Linc', '1991-12-28', 'lgostykee@netlog.com');
insert into employee (id, name, birthday, email) values (16, 'Olenolin', '1951-06-28', 'oonearyf@ucoz.com');
insert into employee (id, name, birthday, email) values (17, 'Umeko', '1955-11-27', 'ubuskeg@spiegel.de');
insert into employee (id, name, birthday, email) values (18, 'Nata', '1975-04-01', 'ntutchellh@eepurl.com');
insert into employee (id, name, birthday, email) values (19, 'Byrom', '1948-03-19', 'bbalnavesi@jugem.jp');
insert into employee (id, name, birthday, email) values (20, 'Dolores', '1944-08-20', 'dscotchforthj@accuweather.com');
insert into employee (id, name, birthday, email) values (21, 'Ker', '1934-01-20', 'kpigdenk@ow.ly');
insert into employee (id, name, birthday, email) values (22, 'Kylynn', '1936-02-22', 'kbeiningl@plala.or.jp');
insert into employee (id, name, birthday, email) values (23, 'Carling', '1961-06-09', 'cblezardm@bizjournals.com');
insert into employee (id, name, birthday, email) values (24, 'Fred', '1954-10-26', 'fnesbittn@chronoengine.com');
insert into employee (id, name, birthday, email) values (25, 'Aeriela', '1966-08-26', 'amellmotho@twitpic.com');
insert into employee (id, name, birthday, email) values (26, 'Debbie', '1978-10-26', 'dcantuap@nymag.com');
insert into employee (id, name, birthday, email) values (27, 'Arlinda', '1946-05-22', 'adraycottq@epa.gov');
insert into employee (id, name, birthday, email) values (28, 'Milo', '1921-07-15', 'mrosbergr@whitehouse.gov');
insert into employee (id, name, birthday, email) values (29, 'Denyse', '1921-07-27', null);
insert into employee (id, name, birthday, email) values (30, 'Denni', '1943-12-03', 'dhulkst@tinypic.com');
insert into employee (id, name, birthday, email) values (31, 'Vince', '1963-05-09', 'vgiacomazzou@spotify.com');
insert into employee (id, name, birthday, email) values (32, 'Laurie', '1991-08-18', 'ldanyv@ehow.com');
insert into employee (id, name, birthday, email) values (33, 'Patricio', '1991-07-23', 'pvinauw@theguardian.com');
insert into employee (id, name, birthday, email) values (34, 'Jennifer', '1921-09-22', 'jgringleyx@opera.com');
insert into employee (id, name, birthday, email) values (35, 'Bancroft', '1990-05-27', 'blozanoy@boston.com');
insert into employee (id, name, birthday, email) values (36, 'Grete', '1934-06-25', 'gcrunkhornz@woothemes.com');
insert into employee (id, name, birthday, email) values (37, 'Frasco', '1990-05-16', 'fruddlesden10@github.io');
insert into employee (id, name, birthday, email) values (38, 'Jim', '1941-09-16', 'jszach11@dailymail.co.uk');
insert into employee (id, name, birthday, email) values (39, 'Nara', '1991-05-23', 'nkemmey12@gizmodo.com');
insert into employee (id, name, birthday, email) values (40, 'Marian', '1946-10-16', 'mkelberman13@vinaora.com');
insert into employee (id, name, birthday, email) values (41, 'Nathalia', '1986-02-13', 'nbradbrook14@dmoz.org');
insert into employee (id, name, birthday, email) values (42, 'Melissa', '1932-02-24', 'mrenad15@imageshack.us');
insert into employee (id, name, birthday, email) values (43, 'Rocky', '1937-01-30', 'rferreras16@businessinsider.com');
insert into employee (id, name, birthday, email) values (44, 'Anstice', '1976-08-10', 'afarrear17@bizjournals.com');
insert into employee (id, name, birthday, email) values (45, 'Natividad', '1994-06-01', 'ntunkin18@fema.gov');
insert into employee (id, name, birthday, email) values (46, 'Allyce', '1947-03-18', 'ahawtrey19@vimeo.com');
insert into employee (id, name, birthday, email) values (47, 'Kaela', '1980-10-06', 'ksidney1a@huffingtonpost.com');
insert into employee (id, name, birthday, email) values (48, 'Garrot', '1984-04-21', 'gskepper1b@newsvine.com');
insert into employee (id, name, birthday, email) values (49, 'Allys', '1971-12-12', 'awrench1c@sciencedaily.com');
insert into employee (id, name, birthday, email) values (50, 'Adelind', '1994-09-04', 'araithby1d@rambler.ru');
);
 
```

3-) Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
 
```

UPDATE employee
SET name = 'Irvin',
    birthday = '1991-11-10'
WHERE id = 1;

UPDATE employee
SET birthday = '1989-05-05'
WHERE id = 2;

UPDATE employee
SET birthday = '1976-02-19',
    email = 'ashury3@blogs.com'
WHERE name = 'Maddy';

UPDATE employee
SET name = 'Irvin',
    email = 'ywalne4@rakuten.co.jp'
WHERE id = 10;

UPDATE employee
SET birthday = '1974-08-16',
    email = 'idunsford0@yahoo.co.jp'
WHERE id = 28;

```

4-) Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
 
```

DELETE FROM employee
WHERE name = 'Glad';

DELETE FROM employee
WHERE birthday = '1938-09-19';

DELETE FROM employee
WHERE id = 49;

DELETE FROM employee
WHERE email = 'respina8@google.it';

DELETE FROM employee
WHERE id = 25;
 
```

## SQL Ödev 09 

 
<br>


1-) <strong>city</strong> tablosu ile <strong>country</strong> tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
 
```

SELECT city, country FROM city
INNER JOIN country ON city.country_id = country.country_id;
 
```

2-) <strong>customer</strong> tablosu ile <strong>payment</strong> tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
 
```

SELECT payment_id, first_name, last_name FROM customer
INNER JOIN payment ON customer.customer_id = payment.customer_id;
 
```

3-) <strong>customer</strong> tablosu ile <strong>rental</strong> tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz 
INNER JOIN sorgusunu yazınız.
 
```

SELECT rental_id, first_name, last_name FROM customer
INNER JOIN rental ON customer.customer_id = rental.customer_id;
 
```

## SQL Ödev 10

 
<br>


1-) <strong>city</strong> tablosu ile <strong>country</strong> tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz 
LEFT JOIN sorgusunu yazınız.
 
```

SELECT city, country FROM City
LEFT JOIN Country ON city.country_id = country.country_id;
 
```

2-) <strong>customer</strong> tablosu ile <strong>payment</strong> tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz 
RIGHT JOIN sorgusunu yazınız.
 
```

SELECT payment_id, first_name, last_name FROM customer
RIGHT JOIN payment ON payment.customer_id = customer.customer_id;
 
```

3-) <strong>customer</strong> tablosu ile <strong>rental</strong> tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz 
FULL JOIN sorgusunu yazınız.
 
```

SELECT rental_id, first_name, last_name FROM customer
FULL JOIN rental ON customer.customer_id = rental.customer_id;
 
```

## SQL Ödev 11

 
<br>


1-) <strong>actor</strong> ve <strong>customer</strong> tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.

```

(
SELECT first_name  FROM actor
)
UNION 
(
SELECT first_name  FROM customer
);
 
```

2-) <strong>actor</strong> ve <strong>customer</strong> tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.

```

(
SELECT first_name  FROM actor
)
INTERSECT
(
SELECT first_name  FROM customer
);
 
```

3-) <strong>actor</strong> ve <strong>customer</strong> tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
```

(
SELECT first_name  FROM actor
)
EXCEPT
(
SELECT first_name  FROM customer
);
 
```

4-) İlk 3 sorguyu tekrar eden veriler için de yapalım.
```

(
SELECT first_name FROM actor
)
UNION ALL
(
SELECT first_name FROM customer
);

(
SELECT first_name FROM actor
)
INTERSECT ALL
(
SELECT first_name FROM customer
);

(
SELECT first_name FROM actor
)
EXCEPT ALL
(
SELECT first_name FROM customer
);
 
```
