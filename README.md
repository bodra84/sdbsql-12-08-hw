# "Домашнее задание к занятию «Резервное копирование баз данных»" - Файзиев Давлат.

### Задание 1

### Кейс

Финансовая компания решила увеличить надёжность работы баз данных и их резервного копирования. 

Необходимо описать, какие варианты резервного копирования подходят в случаях: 

1.1. Необходимо восстанавливать данные в полном объёме за предыдущий день.

1.2. Необходимо восстанавливать данные за час до предполагаемой поломки.

1.3.* Возможен ли кейс, когда при поломке базы происходило моментальное переключение на работающую или починенную базу данных.

*Приведите ответ в свободной форме.*

### Решение 1

Следующие варианты резервного копирования подходят в случаях:
1.1. Полное резервное копирования;
1.2. Дифференциальное резервное копирование (полное - каждые 12 часов, инкрементное - каждый час); 
1.3. Да, такой кейс возможен при применении репликации БД.

---
### Задание 2. PostgreSQL

2.1. С помощью официальной документации приведите пример команды резервирования данных и восстановления БД (pgdump/pgrestore).

2.2.* Возможно ли автоматизировать этот процесс? Если да, то как?

*Приведите ответ в свободной форме.*

### Решение 2

2.1. Команды для резервирования данных PostgreSQL:
```
Команда создания резевной копии БД:
pg_dump dbname > dumpfile

Команда восстановления БД из dumpfile: 
psql dbname < dumpfile 
или
pg_restore -d dbname filename

```
2.2. Да, возможно. Необходимо написать скрипт и добавить его в crontab.

---
### Задание 3. MySQL

3.1. С помощью официальной документации приведите пример команды инкрементного резервного копирования базы данных MySQL. 

3.2.* В каких случаях использование реплики будет давать преимущество по сравнению с обычным резервным копированием?

*Приведите ответ в свободной форме.*

### Решение 3

3.1. Команда инкрементного резервного копирования базы данных MySQL:
```
mysqldump -flush-logs > dump.sql

```
3.2. Применеие реплики будет давать преимущество по сравнению с обычным резервным копированием когда требуется:
- Минимальное время восстановление при сбоях основной БД;
- Доступность БД при ослуживании и сбоях основоной БД;
- Масштабируемость. Снижение нагрузки на основную БД;
- Географическая избыточность;
- Тестирование и разработка.

---

Задания, помеченные звёздочкой, — дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.
