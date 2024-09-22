## Сервисы

### 1. **Service1**
Spring Boot микросервис backend
- Порт: `8081`
- Хранит данные в MongoDB и использует RabbitMQ для обработки событий.

### 2. **Service2**
Spring Boot микросервис backend
- Порт: `8082`
- Работает с MongoDB и использует RabbitMQ для взаимодействия с другими сервисами.

### 3. **Frontend**
Angular приложение, которое предоставляет интерфейс для взаимодействия с backend сервисами.
- Порт: `80` (статические файлы сервируются через Nginx).

### 4. **MongoDB**
Используется для хранения данных микросервисов.
- Данные хранятся в персистентном хранилище (10 GiB).

### 5. **RabbitMQ**
Используется как брокер сообщений между микросервисами.
- Порт для AMQP: `5672`
- Порт для панели управления: `15672`
- Данные RabbitMQ хранятся в персистентном хранилище (10 GiB).

## Развертывание

### Шаг 1: Публикация образов Docker
Убедитесь, что образы ваших микросервисов и frontend опубликованы в Google Artifact Registry:
```bash
gcloud auth configure-docker
docker push gcr.io/[PROJECT_ID]/service1
docker push gcr.io/[PROJECT_ID]/service2
docker push gcr.io/[PROJECT_ID]/frontend-app
