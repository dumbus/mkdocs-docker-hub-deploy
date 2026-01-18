## Публикация статического сайта с использованием Docker, Docker Hub (Отчёт)

> Дисциплина "Проектирование и развертывание веб-решений в эко-системе Python"

## Развертывание на VPS через Docker Hub

> **Примечание:** Изначально планировалось развертывание на сервисе play-with-docker, однако данный сервис в настоящее время недоступен. Поэтому инструкции и отчет описывают процесс публикации и развертывания на VPS сервере.

<img width="1081" height="126" alt="image" src="https://github.com/user-attachments/assets/16894672-d645-4ab4-8132-d63769ebd41a" />

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
cd mkdocs-docker-hub-deploy/docker-deploy
```

3. **Запустите контейнер**

```bash
docker compose pull
docker compose up -d
```

5. **Проверьте статус**

```bash
docker ps
```

6. **Сайт будет доступен по адресу:** `http://your-vps-ip` или `http://your-domain.com`

> **Примечание:** В моём случае сайт доступен по адресу: `http://dumbus-web-tech.ru`

## Отчёт

1. Публикация собранного сайта на Docker Hub с помощью github-actions

<img width="1912" height="745" alt="image" src="https://github.com/user-attachments/assets/a8e87a71-ee2d-497a-98d0-74aa0f2c0c34" />

2. Опубликованное на Docker Hub изображение собранного сайта

<img width="916" height="676" alt="image" src="https://github.com/user-attachments/assets/f5bfbe13-7224-4191-8449-484e49367993" />

4. Загрузка исходных файлов для разворачивания с помощью Docker образа

<img width="838" height="274" alt="image" src="https://github.com/user-attachments/assets/57646650-6de1-45de-9b99-1dc6052c1780" />

4. Разворачивание сайта с помощью docker-compose

<img width="1810" height="232" alt="image" src="https://github.com/user-attachments/assets/cd2cb946-f3ad-410d-88ec-99c05da1ff20" />

5. Развернутый с помощью docker-compose сайт

<img width="1918" height="702" alt="image" src="https://github.com/user-attachments/assets/1d460dbe-48bf-48e7-8658-ac44907c2b5e" />
