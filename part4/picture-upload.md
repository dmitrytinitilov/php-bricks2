# Загружаем файл на сервер


```html
<form enctype="multipart/form-data" action="script.php" method="POST">
    <!--  для отправки файла нужно обязательно указать enctype="multipart/form-data"  -->

    <!-- Поле MAX_FILE_SIZE должно быть указано до поля загрузки файла -->
    <input type="hidden" name="MAX_FILE_SIZE" value="30000" />
    <!-- Название элемента input определяет имя в массиве $_FILES -->
    Отправить этот файл: <input name="userfile" type="file" />
    <input type="submit" value="Send File" />
</form>
```

В script.php

После того как файл передан на сервер, данные о нем будут находиться в массиве $_FILES["userfile"]. Обращаю Ваше внимание, что userfile - это то имя, которое было в &lt;input type="file" name в нашей форме

$_FILES["userfile"]["name"] - хранит исходное имя файла<BR>
$_FILES["userfile"]["tmp_name"] - временное имя, под которым файл сохранился на сервере.<BR>
$_FILES["userfile"]["size"] - размер файла в байтах<BR>


```php
move_uploaded_file($_FILES['userfile']['tmp_name'],$_FILES['userfile']['name'] )
```

PHP сохраняет файлы во временное хранилище, ф-я move_uploaded_file забирает файл с временного хранилища в рабочую папку

//ключ userfile определяется атрибутом name в input’e

**Работа с базой данных**

После того как файл загружен, перейдем к работе с базой данных

Создадим таблицу для картинок. Мы не будем хранить картинки в БД, так как это существенно увеличивает ее размер и замедляет работу. При загрузке файла будем сохранять его имя в БД.


**Множественная загрузка**

```php
<form action="file-upload.php" method="post" enctype="multipart/form-data">
  Файлы:<br />
  <input name="userfile[]" type="file" multiple="true" /><br />
  <input type="submit" value="Отправить" />
</form>
```

То есть к имени файла добавляется []. Для множественной загрузки добавляем multiple=”true”.

 $_FILES['userfile']['name'] – содержит массив имен всех загруженных файлов

 $_FILES['userfile']['name'][0] – доступ к нулевому элементу


count($_FILES['userfile']['name'])  - возвращает количество загруженных файлов

**Полезное чтиво:**

1. Безопасная загрузка изображений на сервер, часть первая
https://habr.com/ru/post/44610/

2. Безопасная загрузка изображений на сервер, часть вторая
https://habr.com/ru/post/44615/

**Практика**
1.	Загружаем картинку на сервер
2.	При загрузке, выводим список ранее загруженных картинок(добавляем БД)
3.	Обеспечиваем уникальность имен файлов и «защиту от просмотров»
4.	Мультизагрузка
