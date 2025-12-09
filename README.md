## Практическое занятие №8. Колчин Степан Сергеевич, ЭФМО-02-25. Работа с MongoDB: подключение, создание коллекции, CRUD-операции

**Окружение**

- Go: go version go1.25.3

- MongoDB: запущена через Docker Compose (образ mongo:7)

- Docker: Docker Desktop (Docker version 28.5.1, build e180ab8)

- Драйвер MongoDB: go.mongodb.org/mongo-driver v1.17.6

- ОС: Windows 11 (с использованием WSL2 - MINGW64_NT-10.0-19045) или Ubuntu 22.04+

- Git: git version 2.51.0+


**Запуск проекта**

- Запустить MongoDB: 
В корне проекта  выполнить:

```bash
docker compose up -d
```

- В корне проекта `008-practice` выполнить:
```bash
go run ./cmd/api/main.go
```

**Запросы**

- `HEALTH`

```bash
curl http://localhost:8080/health
```

- `POST` создание заметки

```bash
curl -X POST http://localhost:8080/api/v1/notes \
  -H "Content-Type: application/json" \
  -d '{"title":"<название_заметки>","content":"<содержимое_заметки>"}'
```

-  `NOTES` получение всех заметок по эндпоинту

```bash
curl "http://localhost:8080/api/v1/notes"
```

- `NOTES<ID>` получение заметки по ID эндпоинту ({id} - заменить на реальный ID)

```bash
curl "http://localhost:8080/api/v1/notes/{id}"

```

- `PATCH` частичное обновление (можно обновлять либо оба поля: title/content, либо только одно)

```bash
curl -X PATCH http://localhost:8080/api/v1/notes/{id} \
  -H "Content-Type: application/json" \
  -d '{"content":"<замещающий_текст>"}'
```

- `DELETE` удаление отметки по ID

```bash
curl -X DELETE http://localhost:8080/api/v1/notes/{id}
```


**Структура**

```
├── cmd
│   └── api
│       └── main.go
├── docker-compose.yml
├── go.mod
├── go.sum
└── internal
    ├── db
    │   └── mongo.go
    └── notes
        ├── handler.go
        ├── model.go
        └── repo.go

```

**Скришноты**

`HEALTH`

<img width="806" height="58" alt="изображение" src="https://github.com/user-attachments/assets/68b4af93-16bc-4d15-98fe-baa1ac041a28" />

`POST`

<img width="806" height="229" alt="изображение" src="https://github.com/user-attachments/assets/c54b2bab-8efc-448a-841c-9e2423e95232" />

`NOTES`

<img width="806" height="96" alt="изображение" src="https://github.com/user-attachments/assets/3455cb76-2d01-4fa6-b203-1b7488c6ebc2" />

`NOTES/<ID>`

<img width="804" height="443" alt="изображение" src="https://github.com/user-attachments/assets/941d777d-9cf7-413e-84dd-d926491cfc65" />

`PATCH`

<img width="804" height="142" alt="изображение" src="https://github.com/user-attachments/assets/663410b9-b6e7-46f3-813d-7877c716e02c" />

`DELETE`

<img width="813" height="510" alt="изображение" src="https://github.com/user-attachments/assets/2e54815a-a7ad-49c7-86f5-b43557e998ea" />

