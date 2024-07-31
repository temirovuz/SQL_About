> **SQL (Structured Query Language)** - bu ma'lumotlar bazasi bilan ishlash uchun mo'ljanlangan dasturlash tili.
> SQL yordamida ma'lumotla bazasida ma'lumotlarni yaratish o'zgargartirish qidirish va o'chirish mumkin.

__________

> **Ma'lumotlar bazasi (Database)** - bu ma'lumotlarni tizimli ravishda saqlash boshqarish va ulardan foydalanish uchun
> mo'ljallangan tuzilma. Ma'lumotlar bazasi yordamida katta hajmli ma'lumotlarni samarali saqlash qidirish va ulardan
> foydalanish imkoniyatini yaratadi.

____

> **SQL va MyAQL o'rtasidagi farq**
> * **SQL** — bu ma'lumotlar bazasi bilan ishlash uchun til.
> * **MySQL** — bu SQL tilini qo'llab-quvvatlaydigan ma'lumotlar bazasini boshqarish tizimi.

### SQL quidagicha asosiy buyruqlarni o'z ichiga oladi.

| SQL so'rovi         | So'rov tarifi                                                                                                                                                           | Misol                                                                                                                            |
|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| **SELECT**          | Bir yoki bir nechta jadvallardan ma'lumotlarni oladi.                                                                                                                   | **SELECT** name **FROM** users;                                                                                                  |
| **INSERT**          | Jadvalga yangi malumot qo'shadi.                                                                                                                                        | **INSERT INTO** users (name, age) **VALUES** ('Muhammad', 23);                                                                   |
| **UPDATE**          | Jadvaldagi mavjud malumotni o'zgartiradi.                                                                                                                               | **UPDATE** users **SET** age 31 **WHERE** name = 'Muhammad';                                                                     |
| **DELETE**          | Jadvaldan malumotni olib tashlaydi.                                                                                                                                     | **DELETE FROM** users **WHERE** name = 'Muhammad';                                                                               |
| **CREATE TABLE**    | Ma'lumotlar bazasida yangi jadval yaratadi.                                                                                                                             | **CREATE TABLE** users (id INT PRIMARY KEY, name VARCHAR(100), age INT);                                                         |
| **ALTER TABLE**     | Mavjud jadval o'zgartiradi. Yangi column qoshadi yiki mavjud columni o'chiradi                                                                                          | **ALTER TABLE** users **ADD** email= 'temirov-muhammad@mail.ru';                                                                 |
| **DROP TABLE**      | Jadvalni o'chiradi.                                                                                                                                                     | **DROP TABLE** users;                                                                                                            |
| **CREATE DATABASE** | SQLda yangi ma'lumotlar bazasini yaratadi                                                                                                                               | **CREATE DATABASE** temirov;                                                                                                     |
| **DROP DATABASE**   | Ma'lumotlar bazasini o'chiradi.                                                                                                                                         | **DROP DATABASE** temirov;                                                                                                       |
| **WHERE**           | Ma'lumotlarni filtrlaydigan shartlarni belgilash uchun ishlatiladi.                                                                                                     | **SELECT** name **FROM** users **WHERE** age > 20;                                                                               |
| **ORDER BY**        | Ma'lumotlarni tartiblash uchun ishlatiladi.                                                                                                                             | **SELECT** name **FROM** users **ORDER BY** name ASC-DESC;                                                                       |
| **GROUP BY**        | Maa'lumotlarni guruhlash uchun ishlatiladi. COUNT, SUM, AVG, MAX, MIN bilan birgalikda qo'llaniladi.                                                                    | **SELECT** name **COUNT(*) AS** count_users **FROM** users **GROUP BY** name;                                                    |
| **HAVING**          | klauzasi agregat funksiyalar COUNT, SUM, AVG, MAX, MIN yordamida hisoblangan qiymatlar asosida filtr qo'yish imkonini beradi.                                           | **SELECT** name **COUNT(*) AS** count_users **FROM** users **GROUP BY** name **HAVING COUNT(*) > 1**;                            |
| **INNER JOIN**      | Ikki jadvalni umumiy ustunlar bo'yicha birlashtiradi va faqat mos keladigan qatorlarni qaytaradi                                                                        | **SELECT** users.name, orders.amount **FROM** users **INNER JOIN** orders **ON** users.id = orders.user.id;                      |
| **LEFT JOIN**       | Birinchi jadvaldagi barcha qatorlarni qaytaradi va ikkinchi jadvaldan mos keladigan qatorlarni qaytaradi.                                                               | **SELECT** users.name, orders.amount **FROM** users **LEFT JOIN** orders **ON** users.id = orders.user.id;                       |
| **RIGHT JOIN**      | Ikkinchi jadvaldagi barcha qatorlarni qaytaradi va birinchi jadvaldan mos keladigan qatorlarni qaytaradi.                                                               | **SELECT** users.name, orders.amount **FROM** users **RIGHT3 JOIN** orders **ON** users.id = orders.user.id;                     |
| **CROSS JOIN**      | Ikkala jadvaldagi har bir qator kombinatsiyasini qaytaradi (Kartezian mahsuloti).                                                                                       | **SELECT** users.name, sciences.name **FROM** users **CROSS JOIN** sciences;                                                     |
| **FULL OUTER JOIN** | Birinchi va ikkinchi jadvallardagi barcha qatorlarni qaytaradi.                                                                                                         | **SELECT** users.name, orders.amount **FROM** users **FULL OUTER JOIN** orders **ON** users.id = orders.user.id;                 |
| **UNION**           | Birlashtirilgan natijalar to'plamida faqat noyob (distinct) qatorlarni qaytaradi.                                                                                       | **SELECT** name, birthday **FROM** users **UNION SELECT** name, birthday **FROM** students;                                      |
| **UNION ALL**       | Birlashtirilgan natijalar to'plamida hamma qatorlarni qaytaradi. Ikkalasidagini hammasini.                                                                              | **SELECT** name, birthday **FROM** users **UNION ALL SELECT** name, birthday **FROM** students;                                  |
| **SUBQUERY**        | Subquery asosiy so'rov uchun kerakli ma'lumotlarni olishda yordam beradi va odatda SELECT, INSERT, UPDATE, yoki DELETE buyrug'ida qo'llaniladi.                         | **SELECT** age **FROM** users **WHERE** age = (**SELECT MAX(age)** **FROM** users);                                              |
| **EXISTS**          | Subquery natijalarining mavjudligini tekshirish va murakkab so'rovlarni bajarish uchun kuchli vositadir.                                                                | **SELECT** name **FROM** users s **WHERE EXISTS** (**SELECT 1** **FROM** students s **WHERE** u.student_id = s.student_id);      |
| **ANY**             | SQLda subquery natijalari bilan mos keladigan qatorlarni tanlashda foydali va moslashuvchan vositadir                                                                   | **SELECT** name **FROM** users s **WHERE** student_id =  **AYN(SELECT student_id** **FROM** students s **WHERE** u.grades > 80); |
| **ALL**             | Subquerydan qaytarilgan barcha qiymatlar bilan solishtirish uchun ishlatiladi.                                                                                          | **SELECT** name **FROM** users s **WHERE** student_id =  **ALL(SELECT student_id** **FROM** students s **WHERE** u.grades > 80); |
| **LIKE**            | Satrlarni belgilangan shablon yoki naqshga mos kelishini tekshirish uchun ishlatiladi. Bu operator ko'pincha SELECT, UPDATE, DELETE va WHERE klauzalarida qo'llaniladi. | **SELECT** name **FROM** users **WHERE** name **LIKE** 'A%';                                                                     |
| **IN**              | Biror ustun qiymatining biror to'plam yoki subquerydan qaytarilgan natijalar orasida mavjudligini tekshirish uchun ishlatiladi.                                         | **SELECT** name **FROM** users **WHERE** name **IN**('Muhammad', 'Temur')';                                                      |
| **BETWEEN**         | Ikki chegaraviy qiymatlar oralig'ida (inclusive) joylashganligini tekshirish uchun ishlatiladi.                                                                         | **SELECT** name **FROM** users **WHERE** age **BETWEEN** 20 **AND** 35;                                                          |
| **LIMIT**           | Ikki chegaraviy qiymatlar oralig'ida (inclusive) joylashganligini tekshirish uchun ishlatiladi.                                                                         | **SELECT** name **FROM** users **WHERE** age **BETWEEN** 20 **AND** 35;                                                          |