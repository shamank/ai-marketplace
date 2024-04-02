Тестовое задание
Допустим, у нас есть множество AI сервисов которые могут вызывать разные пользователи. Необходимо написать два микросервиса на Go для сбора и отдачи статистики по вызываемым сервисам. Микросервисы должны общаться между собой по Grpc.

Задачи первого микросервиса:
Хранить и обновлять в базе данных информацию о количестве вызовах;
Предоставлять grpc методы для второго микросервиса.

Примерная структура бд:
1. Таблица services (id, name, description);
2. Таблица users (id, name);
3. Таблица stats (user_id, count, service_id);
   Где count - количество вызовов (целочисленное число).

Задачи второго микросервиса:
Должен иметь несколько rest api хендлеров:
POST /call - для информирования о новом вызове (на вход дается user_id и service_id);
GET /calls - получение статистики по user_id и/или service_id (должны быть фильтры и пагинация);
POST /service - для добавления нового сервиса.
При вызове хэндлеров мы должны обратиться по grpc ко второму сервису для получения или изменения информации.




Примечания:
Заполните таблицы тестовыми данными самостоятельно (или напишите скрипт для автоматизации);
База данных на выбор из списка (postgres, mysql, clickhouse);
ORM использовать нельзя;
Выбор библиотек не ограничен, но лучше использовать актуальные и поддерживаемые инструменты;
По желанию можете написать Dockerfile/Docker-compose для проекта;
Опубликовать проект надо на Github или Gitlab с публичным доступом.

Примерные критерии оценки или на что стоит обратить внимание:
Объем реализованного функционала;
Архитектура и структура проекта;
Читаемость и чистота кода.

Дополнение (реализация по желанию):
Добавить параметр для сервисов: цена вызова. Метод GET /calls должен возвращать еще и сколько суммарно заплатили за вызовы учитывая    фильтры. (То-есть если передается конкретный user_id то метод должен вернуть сколько один пользователь потратил денег на вызовы и тд).