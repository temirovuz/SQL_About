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

| SQL so'rovi         | So'rov tarifi                                                                                                                 | Misol                                                                                             |
|---------------------|-------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| **SELECT**          | Bir yoki bir nechta jadvallardan ma'lumotlarni oladi.                                                                         | **SELECT** name **FROM** users;                                                                   |
| **INSERT**          | Jadvalga yangi malumot qo'shadi.                                                                                              | **INSERT INTO** users (name, age) **VALUES** ('Muhammad', 23);                                    |
| **UPDATE**          | Jadvaldagi mavjud malumotni o'zgartiradi.                                                                                     | **UPDATE** users **SET** age 31 **WHERE** name = 'Muhammad';                                      |
| **DELETE**          | Jadvaldan malumotni olib tashlaydi.                                                                                           | **DELETE FROM** users **WHERE** name = 'Muhammad';                                                |
| **CREATE TABLE**    | Ma'lumotlar bazasida yangi jadval yaratadi.                                                                                   | **CREATE TABLE** users (id INT PRIMARY KEY, name VARCHAR(100), age INT);                          |
| **ALTER TABLE**     | Mavjud jadval o'zgartiradi. Yangi column qoshadi yiki mavjud columni o'chiradi                                                | **ALTER TABLE** users **ADD** email= 'temirov-muhammad@mail.ru';                                  |
| **DROP TABLE**      | Jadvalni o'chiradi.                                                                                                           | **DROP TABLE** users;                                                                             |
| **CREATE DATABASE** | SQLda yangi ma'lumotlar bazasini yaratadi                                                                                     | **CREATE DATABASE** temirov;                                                                      |
| **DROP DATABASE**   | Ma'lumotlar bazasini o'chiradi.                                                                                               | **DROP DATABASE** temirov;                                                                        |
| **WHERE**           | Ma'lumotlarni filtrlaydigan shartlarni belgilash uchun ishlatiladi.                                                           | **SELECT** name **FROM** users **WHERE** age > 20;                                                |
| **ORDER BY**        | Ma'lumotlarni tartiblash uchun ishlatiladi.                                                                                   | **SELECT** name **FROM** users **ORDER BY** name ASC-DESC;                                        |
| **GROUP BY**        | Maa'lumotlarni guruhlash uchun ishlatiladi. COUNT, SUM, AVG, MAX, MIN bilan birgalikda qo'llaniladi.                          | **SELECT** name **COUNT(*) AS** userlar **FROM** users **GROUP BY** name;                         |
| **HAVING**          | klauzasi agregat funksiyalar COUNT, SUM, AVG, MAX, MIN yordamida hisoblangan qiymatlar asosida filtr qo'yish imkonini beradi. | **SELECT** name **COUNT(*) AS** userlar **FROM** users **GROUP BY** name **HAVING COUNT(*) > 1**; |