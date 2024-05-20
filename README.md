# YaTube
## Описание:
API **вымышленной** социальной сети, c помощью которого можно выкладывать свои посты, комментировать посты других пользователей, удалять или редактировать свои записи. Также доступна возможность подписки и отписки на авторов соц.сети.
___

**Цель данного проекта — реализация подхода к проектированию, при котором программная часть API разрабатывается на основе уже составленной документации, выступающей в роли технического задания.**

### Используемые технологии:
![image](https://img.shields.io/badge/Python-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
![image](https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite&logoColor=white)
![image](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=green)
![image](https://img.shields.io/badge/django%20rest-ff1709?style=for-the-badge&logo=django&logoColor=white)
![image](https://img.shields.io/badge/VSCode-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white)
![image](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)

## Установка:

Если Python не установлен, скачайте и установите его с [официального сайта](https://www.python.org/downloads/).
### Системные требования

- **Версия Python**: 3.9 или выше
- **Операционная система**: Windows / macOS / Linux

Клонировать репозиторий и перейти в него в командной строке:
```python
git clone git@github.com:Apollo297/api_final_yatube.git
```
```python
cd api_final_yatube
```
Cоздать и активировать виртуальное окружение:
```python
python3 -m venv env
```
```python
source env/bin/activate
```
Установить зависимости из файла requirements.txt:
```python
python3 -m pip install --upgrade pip
```
```python
pip install -r requirements.txt
```
Выполнить миграции:
```python
python3 manage.py migrate
```
Запустить проект:
```python
python3 manage.py runserver
```
___
## Примеры:
Запросы к API проекта делятся на запросы от анонимных пользователей и от авторизованных.

***Примеры запросов для анонимных пользователей:***
  
* Получить список всех публикаций на эндпоинт http://127.0.0.1:8000/api/v1/posts/ с использованием параметров limit и offset:
```python
{
  "count": 123,
  "next": "http://api.example.org/accounts/?offset=400&limit=100",
  "previous": "http://api.example.org/accounts/?offset=200&limit=100",
  "results": [
    {
      "id": 0,
      "author": "string",
      "text": "string",
      "pub_date": "2021-10-14T20:41:29.648Z",
      "image": "string",
      "group": 0
    }
  ]
}
```
* Получение одной публикации по id на эндпоинт http://127.0.0.1:8000/api/v1/posts/{id}/:
```python
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}
```
* Получение списка доступных сообществ на эндпоинт http://127.0.0.1:8000/api/v1/groups/:
```python
[
  {
    "id": 0,
    "title": "string",
    "slug": "string",
    "description": "string"
  }
]
```
***Примеры запросов для авторизованных пользователей:***

* Частичное обновление публикации по id на эндпоинт http://127.0.0.1:8000/api/v1/posts/{id}/. Обновить публикацию может только автор публикации.

*payload:*
```python
{
  "text": "string",
  "image": "string",
  "group": 0
}
```
*response:*
```python
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}
```

  * Добавление нового комментария к публикации на эндпоинт http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/:

*payload:*
```python
{
  "text": "string"
}
```
*response:*
```python
{
  "id": 0,
  "author": "string",
  "text": "string",
  "created": "2019-08-24T14:15:22Z",
  "post": 0
}
```

  * Получение JWT-токена на эндпоинт http://127.0.0.1:8000/api/v1/jwt/create/: 

*payload:*
```python
{
  "username": "string",
  "password": "string"
}
```
*response:*
```python
{
  "refresh": "string",
  "access": "string"
}
```
