# Агрегатные функции. GROUP BY, HAVING


Рассмотрим основные агрегатные функции

COUNT, AVG, MAX, MIN, SUM

Посчитаем работников с ЗП больше 1000

```sql
SELECT COUNT(*) 
FROM workers
WHERE salary >1000
```

echo $row['COUNT(*)']

Либо используем псевдонимы

```sql
SELECT COUNT(*) as cnt
FROM workers
WHERE salary >1000
```


echo $row["cnt"]


**GROUP BY**

Посчитаем количество сотрудников в каждом отделе

```sql
SELECT COUNT(id)
FROM workers
GROUP BY dep_id
```
Посчитаем количество сотрудников в каждом отделе, у которых зарплата выше тысячи

```sql
SELECT COUNT(id)
FROM workers
WHERE salary>1000
GROUP BY dep_id
```

То есть WHERE срабатывает до группировки

**HAVING**

Выведем номера отделений, у которых средняя зарплата выше тысячи

```sql
SELECT dep_id
FROM workers
GROUP BY dep_id
HAVING AVG(salary)>1000
```

**Практика:**

1.	Вывести среднюю ЗП
2.	Вывести сотрудников, у которых зарплата выше среднего
3.	Посчитать количество сотрудников в каждом отделе
4.	Вывести среднюю ЗП в каждом отделе
5.	Вывести те отделы, у которых больше двух сотрудников
ДЗ: Добавить категории в интернет магазин. У каждой категории вывести количество товаров в ней