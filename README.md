# todo-app
ToDo-App - веб-приложение с пользовательским интерфейсом - To-Do List.

## Что реализовано?

Пользователь имеет возможность:
* Создать новый элемент To-Do
* Просмотреть список активных тудушек 
* Отметить тудушку как выполненную 
* Удалить тудушку
* Отсортировать тудушки по приоритету

Вместе с каждым действием, которое пользователь выполняет над элементом туду, отправляется http-запрос с json на сервер.

Взаимодействие клиента с сервером реализовано через AJAX запросы к API.

## 🔧 Требования:
* PHP >= 7.4
* PHP-cURL
* npm >= 7.11.1
* yarn >= 1.22.10
* Стандартные требования для [symfony](https://symfony.com/doc/current/setup.html#technical-requirements)

## ⚙️ Развертывание проекта

1. Скачайте репозиторий в любую директорию.
2. Обновите конфигурацию NGINX. (Пример конфигурации: [nginx.conf](nginx.conf)).
3. Измените [конфигурационный файл](.env).
4. Установите зависимости для бэкэнда через команду `composer i`.
5. Проведите миграцию базы данных командой `sudo php bin/console doctrine:migrations:migrate`.
6. Установите зависимости для фронтенда через команду `yarn install`.
7. Измените адрес сервера на ваш в [конфигурации js](assets/index.js) (baseAPIURL)
7. Соберите фронтенд через команду `yarn run build`.

## 📚 API
### Users
### GET /api/users/authorize
Выполняет авторизацию пользователя. Необходимые параметры:
* username - имя пользователя
* password - пароль пользователя

### POST /api/users/
Выполняет регистрацию пользователя. Необходимые параметры:
* username - имя пользователя
* password - пароль пользователя

### ToDo

### GET /api/todoes
Возвращает список задач пользователю. Принимает параметры:
* sortField - поле для сортировки
* sortMethod - метод сортировки (ASC/DESC)
* isCompleted - выполнена ли тудушка (0 или 1)

### POST /api/todoes
Создаёт тудушку. Необходимый параметр:
* name - название задачи

### GET /api/todoes/{id}
Возвращает информацию о тудушку по её id.

### PUT /api/todoes/{id}
Обновляет тудушку по её id. Необходимые параметры:
* sort - номер сортировки тудушки
* isCompleted - выполнена ли тудушка (0 или 1)

### DELETE /api/todoes/{id}
Удаляет тудушку по её id.