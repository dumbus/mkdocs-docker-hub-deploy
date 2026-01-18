## Публикация статического сайта с использованием Docker, Docker Hub (Отчёт)

> Дисциплина "Проектирование и развертывание веб-решений в эко-системе Python"

## Развертывание на VPS через Docker Hub

> **Примечание:** Изначально планировалось развертывание на сервисе play-with-docker, однако данный сервис в настоящее время недоступен. Поэтому инструкции и отчет описывают процесс публикации и развертывания на VPS сервере.

<!-- Место для скриншота play-with-docker недоступности -->

### Публикация Docker образа на Docker Hub

1. **Настройка секретов в GitHub:**
   - Перейдите в `Settings` → `Secrets and variables` → `Actions`
   - Добавьте секреты:
     - `DOCKER_USERNAME` - ваш логин на Docker Hub
     - `DOCKER_PASSWORD` - пароль или Personal Access Token от Docker Hub

> **Примечание:** Мой логин docker: `dumbus`, поэтому всё дальнейшее описание будет написано с учётом этого

2. **Автоматическая сборка и публикация:**
   - При каждом push в ветки `main` или `develop` автоматически запускается workflow `.github/workflows/docker-hub.yml`
   - Workflow собирает статический сайт, создает Docker образ и публикует его на Docker Hub
   - Образ публикуется с тегами: `dumbus/mkdocs-site:latest` и `dumbus/mkdocs-site:commit-sha`

### Развертывание с помощью Docker

1. **Установите Docker и Docker Compose**

2. **Загрузите файлы приложения**

```bash
git clone https://github.com/dumbus/mkdocs-docker-hub-deploy.git
cd mkdocs-docker-hub-deploy/deploy
```

3. **Запустите контейнер**

```bash
docker-compose pull
docker-compose up -d
```

5. **Проверьте статус**

```bash
docker ps
```

6. **Сайт будет доступен по адресу:** `http://your-vps-ip` или `http://your-domain.com`

> **Примечание:** В моём случае сайт доступен по адресу: `http://dumbus-web-tech.ru`