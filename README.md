# AI Marketplace

***тестовое задание***

Проект состоит из двух микросервисов: StatisticService и APIGateway.
Сервисы общаются по gRPC (контракты описаны в `./protos`).

### Запуск проекта

Для быстрого запуска проекта, можно воспользоваться утилитой `make` и `Docker`:
```sh
make start
```

Скрипт сбилдит образы и поднимет контейнеры, прописанные в `docker-compose.yaml` (в том числе проведет миграцию и заполнит данными)




### Структура проекта

Два микросервиса:
1. [Сервис статистики (Statistic Service)](https://github.com/shamank/ai-marketplace-stats-service)
2. [Сервис APIGateway](https://github.com/shamank/ai-marketplace-api-gateway)


Контракты:
1. [Protobuf](https://github.com/shamank/ai-marketplace-protos)


Общая структура проекта:
```
├───api-gateway // Сервис APIGateway (второй микросервис)
│   ├───cmd
│   │   └───app
│   ├───configs
│   └───internal
│       ├───app
│       ├───clients
│       │   └───stats-service
│       │       └───grpc
│       ├───config
│       ├───delivery
│       │   └───http
│       └───domain
│           └───models
│ 
├───protos // Сгенерированные и описанные protobuf-контракты
│   ├───gen
│   │   └───go
│   │       └───stats-service
│   └───stats-service
│ 
└───stats-service // Сервис сбора и хранения статистики (первый микросервис)
    ├───cmd
    │   ├───app
    │   └───migrate
    ├───configs
    ├───internal
    │   ├───app
    │   ├───config
    │   ├───delivery
    │   │   └───grpc
    │   │       └───statistic
    │   ├───domain
    │   │   ├───errors
    │   │   └───models
    │   ├───logger
    │   ├───repository
    │   │   └───postgres
    │   └───service
    │       └───statistic
    └───migrations
```


### *Комментарий*:

Хотел бы еще (но не успел):
- Прологгировать опасные места
- Дописать тесты (unit & функциональные)
- В APIGateway сделать response.go, где описал бы типичные HTTP-ответы