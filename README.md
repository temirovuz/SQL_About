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

| SQL so'rovi         | So'rov tarifi                                                                                                                                                           | Misol                                                                                                                                                |
|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| **SELECT**          | Bir yoki bir nechta jadvallardan ma'lumotlarni oladi.                                                                                                                   | **SELECT** name **FROM** users;                                                                                                                      |
| **INSERT**          | Jadvalga yangi malumot qo'shadi.                                                                                                                                        | **INSERT INTO** users (name, age) **VALUES** ('Muhammad', 23);                                                                                       |
| **UPDATE**          | Jadvaldagi mavjud malumotni o'zgartiradi.                                                                                                                               | **UPDATE** users **SET** age 31 **WHERE** name = 'Muhammad';                                                                                         |
| **DELETE**          | Jadvaldan malumotni olib tashlaydi.                                                                                                                                     | **DELETE FROM** users **WHERE** name = 'Muhammad';                                                                                                   |
| **CREATE TABLE**    | Ma'lumotlar bazasida yangi jadval yaratadi.                                                                                                                             | **CREATE TABLE** users (id INT PRIMARY KEY, name VARCHAR(100), age INT);                                                                             |
| **ALTER TABLE**     | Mavjud jadval o'zgartiradi. Yangi column qoshadi yiki mavjud columni o'chiradi                                                                                          | **ALTER TABLE** users **ADD** email= 'temirov-muhammad@mail.ru';                                                                                     |
| **DROP TABLE**      | Jadvalni o'chiradi.                                                                                                                                                     | **DROP TABLE** users;                                                                                                                                |
| **CREATE DATABASE** | SQLda yangi ma'lumotlar bazasini yaratadi                                                                                                                               | **CREATE DATABASE** temirov;                                                                                                                         |
| **DROP DATABASE**   | Ma'lumotlar bazasini o'chiradi.                                                                                                                                         | **DROP DATABASE** temirov;                                                                                                                           |
| **WHERE**           | Ma'lumotlarni filtrlaydigan shartlarni belgilash uchun ishlatiladi.                                                                                                     | **SELECT** name **FROM** users **WHERE** age > 20;                                                                                                   |
| **ORDER BY**        | Ma'lumotlarni tartiblash uchun ishlatiladi.                                                                                                                             | **SELECT** name **FROM** users **ORDER BY** name ASC-DESC;                                                                                           |
| **GROUP BY**        | Maa'lumotlarni guruhlash uchun ishlatiladi. COUNT, SUM, AVG, MAX, MIN bilan birgalikda qo'llaniladi.                                                                    | **SELECT** name **COUNT(*) AS** count_users **FROM** users **GROUP BY** name;                                                                        |
| **HAVING**          | klauzasi agregat funksiyalar COUNT, SUM, AVG, MAX, MIN yordamida hisoblangan qiymatlar asosida filtr qo'yish imkonini beradi.                                           | **SELECT** name **COUNT(*) AS** count_users **FROM** users **GROUP BY** name **HAVING COUNT(*) > 1**;                                                |
| **INNER JOIN**      | Ikki jadvalni umumiy ustunlar bo'yicha birlashtiradi va faqat mos keladigan qatorlarni qaytaradi                                                                        | **SELECT** users.name, orders.amount **FROM** users **INNER JOIN** orders **ON** users.id = orders.user.id;                                          |
| **LEFT JOIN**       | Birinchi jadvaldagi barcha qatorlarni qaytaradi va ikkinchi jadvaldan mos keladigan qatorlarni qaytaradi.                                                               | **SELECT** users.name, orders.amount **FROM** users **LEFT JOIN** orders **ON** users.id = orders.user.id;                                           |
| **RIGHT JOIN**      | Ikkinchi jadvaldagi barcha qatorlarni qaytaradi va birinchi jadvaldan mos keladigan qatorlarni qaytaradi.                                                               | **SELECT** users.name, orders.amount **FROM** users **RIGHT3 JOIN** orders **ON** users.id = orders.user.id;                                         |
| **CROSS JOIN**      | Ikkala jadvaldagi har bir qator kombinatsiyasini qaytaradi (Kartezian mahsuloti).                                                                                       | **SELECT** users.name, sciences.name **FROM** users **CROSS JOIN** sciences;                                                                         |
| **FULL OUTER JOIN** | Birinchi va ikkinchi jadvallardagi barcha qatorlarni qaytaradi.                                                                                                         | **SELECT** users.name, orders.amount **FROM** users **FULL OUTER JOIN** orders **ON** users.id = orders.user.id;                                     |
| **UNION**           | Birlashtirilgan natijalar to'plamida faqat noyob (distinct) qatorlarni qaytaradi.                                                                                       | **SELECT** name, birthday **FROM** users **UNION SELECT** name, birthday **FROM** students;                                                          |
| **UNION ALL**       | Birlashtirilgan natijalar to'plamida hamma qatorlarni qaytaradi. Ikkalasidagini hammasini.                                                                              | **SELECT** name, birthday **FROM** users **UNION ALL SELECT** name, birthday **FROM** students;                                                      |
| **SUBQUERY**        | Subquery asosiy so'rov uchun kerakli ma'lumotlarni olishda yordam beradi va odatda SELECT, INSERT, UPDATE, yoki DELETE buyrug'ida qo'llaniladi.                         | **SELECT** age **FROM** users **WHERE** age = (**SELECT MAX(age)** **FROM** users);                                                                  |
| **EXISTS**          | Subquery natijalarining mavjudligini tekshirish va murakkab so'rovlarni bajarish uchun kuchli vositadir.                                                                | **SELECT** name **FROM** users s **WHERE EXISTS** (**SELECT 1** **FROM** students s **WHERE** u.student_id = s.student_id);                          |
| **ANY**             | SQLda subquery natijalari bilan mos keladigan qatorlarni tanlashda foydali va moslashuvchan vositadir                                                                   | **SELECT** name **FROM** users s **WHERE** student_id =  **AYN(SELECT student_id** **FROM** students s **WHERE** u.grades > 80);                     |
| **ALL**             | Subquerydan qaytarilgan barcha qiymatlar bilan solishtirish uchun ishlatiladi.                                                                                          | **SELECT** name **FROM** users s **WHERE** student_id =  **ALL(SELECT student_id** **FROM** students s **WHERE** u.grades > 80);                     |
| **LIKE**            | Satrlarni belgilangan shablon yoki naqshga mos kelishini tekshirish uchun ishlatiladi. Bu operator ko'pincha SELECT, UPDATE, DELETE va WHERE klauzalarida qo'llaniladi. | **SELECT** name **FROM** users **WHERE** name **LIKE** 'A%';                                                                                         |
| **IN**              | Biror ustun qiymatining biror to'plam yoki subquerydan qaytarilgan natijalar orasida mavjudligini tekshirish uchun ishlatiladi.                                         | **SELECT** name **FROM** users **WHERE** name **IN**('Muhammad', 'Temur')';                                                                          |
| **BETWEEN**         | Ikki chegaraviy qiymatlar oralig'ida (inclusive) joylashganligini tekshirish uchun ishlatiladi.                                                                         | **SELECT** name **FROM** users **WHERE** age **BETWEEN** 20 **AND** 35;                                                                              |
| **LIMIT**           | So'rov natijalaridan qaytariladigan qatorlar sonini cheklash uchun samarali vositadir.                                                                                  | **SELECT** name **FROM** users **LIMIT** 5;                                                                                                          |
| **OFFSET**          | Natija to'plamining qaysi qatorlardan boshlab olinishi kerakligini belgilaydi..                                                                                         | **SELECT** name **FROM** users **LIMIT** 5 **OFFSET** 2;                                                                                             |
| **TRUNCATE TABLE**  | Jadvaldagi barcha qatorlarni tez va samarali tarzda o'chirish uchun ishlatiladi.                                                                                        | **TRUNCATE TABLE** users;                                                                                                                            |
| **CASE**            | Shartli mantiqni amalga oshirish uchun ishlatiladi. U shartlar asosida turli natijalarni qaytarishga imkon beradi.                                                      | **SELECT** name, grades **CASE WHEN** grades = 5 **THEN** 'Excellent' **CASE WHEN** grades = 4 **THEN** 'Good' **ELSE** 'Bad' **END FROM** students; |

> **SQLda** foydalanuvchi tomonidan aniqlangan **funksiyalar (user-defined functions, UDF)** yordamida ma'lum bir
> hisob-kitob yoki operatsiyalarni qayta-qayta bajarish uchun kod yozish mumkin. Bu funksiyalar sizga murakkab
> hisob-kitoblarni yoki ma'lumotlarni manipulyatsiya qilishni soddalashtirishga yordam beradi.
> ![Test-javobini-%-da-hisoblash](https://github.com/user-attachments/assets/7f2b788a-e58a-4a65-a97d-d2a9f9acde37)
> ![Test-javobini-%-da-hisoblash (1)](https://github.com/user-attachments/assets/dd8948b3-cdeb-48aa-a546-ee1b9b5a3942)
> ![NATIJA-github com_temirovuz](https://github.com/user-attachments/assets/128290ef-e577-437b-ad89-17db7009827f)


> **View**'lar murakkab so'rovlarni **soddalashtirish** va ulardan **qayta foydalanishni osonlashtirish** uchun
> ishlatiladi. Misol uchun, ko'p jadvalni birlashtirib yoki murakkab shartlar bilan filtrlaydigan so'rovni har safar
> yozmasdan, bitta view orqali amalga oshirish mumkin.

![View-example](https://github.com/user-attachments/assets/175faa3e-369a-4151-b4e8-840f1eaf3fc5)

> **Transaction Control Language (TCL)** SQLning bir qismi bo'lib, **transactionlarni** boshqarish uchun ishlatiladi.
> Transaction — bu bir nechta SQL buyruqlari to'plamidir, ular bitta birlik sifatida bajariladi. Transactionlar
> ma'lumotlar bazasida bir qator operatsiyalarni amalga oshiradi va ular **muvaffaqiyatli** bajarilgan taqdirda barcha
> o'zgarishlar **doimiy bo'ladi** yoki **biror xato yuz berganda** barcha o'zgarishlar **bekor** qilinadi.

![Bank-Hisoblaridan-Pul-O'tkazish (1)](https://github.com/user-attachments/assets/142e2b66-2a3e-45b6-9af9-01e729bf22ba)

> **Stored Procedure** — bu SQL buyruqlari va **mantiqiy kodlar to'plami** bo'lib, **bir marta yaratiladi** va
> keyinchalik **ko'p marta chaqirilishi** mumkin. Stored Procedurelar ma'lumotlar bazasida saqlanadi va SQL Server yoki
> boshqa DBMS (ma'lumotlar bazasi boshqarish tizimi) tomonidan bajariladi.

![Stored-Procedure-yaratishva-chaqirish-github com_temirovuz](https://github.com/user-attachments/assets/2ca299c3-f928-45f3-bbc9-842379f430af)

## [🗯TELEGRAM](https://t.me/temirov)
