# Docker

- [Docker](https://www.docker.com/)
- [Docker Hub](https://hub.docker.com/)

---
## Основні команди

- `docker version`
- `docker ps -a` - список запущених та зупинених контейнерів
- `docker rm {id контейнера} or {name контейнера}` - видаляємо контейнер
- `docker container prune` - видаляємо усі контейнери
- `docker images` - показує скачані образи
- `docker rmi {id образа} or {name образа}` - видаляємо образ
- `docker pull {name образа}` - скачуємо образ
- `docker run {name образа}` - запускаємо образ
- `docker container inspect {id контейнера} or {name контейнера}` - виведе інформацію по запущеному контейнеру
- `docker stop {id контейнера} or {name контейнера}` - зупиняє контейнер
- `docker exec -it {id контейнера} or {name контейнера} bash` - виповняємо команду всередині контейнера (в даному випадку заходимо на командну строку всередину контейнера)
- `docker volume ls` - дивимось усі тома всередині docker

> Приклад запуску сервера nginx + порти + локальна папка
>
> `docker run -d -p 80:80 -v /home/svop/html:/usr/share/nginx/html --rm --name my-web-server nginx`

---

> Розбиваємо довгу команду на строки
>
>       docker run \
>           -d \
>           -p 80:80 \
>           -v /home/svop/html:/usr/share/nginx/html \
>           --rm \
>           --name my-web-server \
>           nginx 
> для зручності

### docker run

- [docker container run](https://docs.docker.com/reference/cli/docker/container/run/)

- `-i` - інтерактивний, тримає вхідний канал (STDIN) відкритим 
- `-t` - виділити псевдо-TTY (термінал, ну дуже грубо)
- `-d` - запуск контейнера у фоновому режимі
- `-p` - опублікувати порт(и) контейнера на хості - `-p 80:80`
- `-v` - монтуємо том - `-v /home/svop:/usr/share/nginx/html` або `-v ${PWD}:/usr/share/nginx/html` -  `${PWD}` абсолютний путь до поточної папки 
- `-e` - змінні середовища
- `--rm` - автоматично видаляє контейнер, коли він зупиняється
- `--name` - даємо назву контейнеру

---
## Dockerfile

Приклад `Dockerfile`

        FROM python:alpine

        WORKDIR /app

        COPY . .

        CMD [ "python", "main.py" ]

- `docker build . -t my-calendar` - створюємо новий образ
- `docker run -it my-calendar` - запускаємо створений нами образ

### Dockerfile підтримує такі інструкції:

- `ADD` - додати локальні або віддалені файли та каталоги
- `ARG` - змінні часу збирання
- `CMD` - команди за замовчуванням
- `COPY` - копіювати файли та каталоги
- `ENTRYPOINT` - виконуваний файл за замовчуванням
- `ENV` - змінні середовища
- `EXPOSE` - які порти прослуховує програма
- `FROM` - новий етап збірки з базового зображення
- `HEALTHCHECK` - перевірка працездатності контейнера під час запуску
- `LABEL` - метадані
- `MAINTAINER` - автора
- `ONBUILD` - інструкції щодо використання образа в збірці
- `RUN` - виконувати команди побудови
- `SHELL` - встановити оболонку образа за замовчуванням.
- `STOPSIGNAL` - сигнал системного виклику для виходу з контейнера
- `USER` - ідентифікатор користувача та групи
- `VOLUME` - створення об'ємних кріплень
- `WORKDIR` - робочий каталог

---
## docker-compose.yml

- `docker-compose up` - запуск
- `docker-compose up -d` - запуск у фоні
- `docker-compose down` - зупинка
- `docker-compose up -d --build` - запуск у фоні + перебілд, як що щось змінили
- `docker log {id контейнера}` - вивід логів потрібного контейнера

### docker-compose підтримує такі інструкції:

- `version: '3'` - 
- `services:`
        - `name-services`
                - `build:`
                - `image:`
                - `restart: always`
                - `ports:`
                        - `- '80:80'`
                - `environment:`
                        `змінні середовища`
                - `depends_on:`
                        - `- serviceName від котрих залежить цей сервіс`
                - `volumes:`
                        - `том:том`
- `volumes:`
        - `name_том:`
