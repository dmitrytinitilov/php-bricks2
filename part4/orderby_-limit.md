# ORDER BY, LIMIT

Отсортируем работников старше 20 по убыванию зарплаты

```sql
SELECT name, salary
FROM workers
WHERE age>20
ORDER BY salary DESC
```


Если мы хотим, чтобы таких работников было не больше 10 – добавляем LIMIT

```sql
SELECT name, salary
FROM workers
WHERE age>20
ORDER BY salary DESC
LIMIT 0,10
```

**Пагинация**

Пагинация это выведение каких-то элементов(товаров, постов и т.д.) постранично.

Для того, чтобы реализовать пагинацию попробуйте действовать поэтапно

1. Выведете элементы для второй страницы
2. Научитесь выбирать элементы с $n-й страницы
3. Получайте $n через GET-параметр
4. Посчитайте сколько у Вас будет страниц
5. Сгенерируйте ссылки с перечислением страниц 

**Практика**
1.	Отсортировать работников по зарплате
2.	Выбрать работника с максимальной зарплатой
2.	Сделать пагинацию в гостевой
2.	Сделать регистрацию
3.	Авторизацию (проверку логина пароля)
4.	Добавление, редактирование, удаление товара