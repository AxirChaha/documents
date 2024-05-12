- `docker ps`
- `docker ps -a`
- `docker images`
- `docker run {name образа}`
- `docker container inspect {id контейнера} or {name контейнера}`
- `docker stop {id контейнера} or {name контейнера}`

---

- `docker rm {id контейнера} or {name контейнера}` - видаляємо контейнер
- `docker container prune` - видаляємо усі контейнери
- `docker rmi {id образа} or {name образа}` - видаляємо образ
> - `docker system prune -a --volumes` - чистимо все (ну майже)
- `docker volume prune` - видаляємо всі тома

---

> #### Приклад запуску сервера nginx + порти + локальна папка + name + rm
>  `docker run -d -p 80:80 -v /home/svop/html:/usr/share/nginx/html --rm --name my-web-server nginx`
>
>---

---

- `docker exec -it {id контейнера} or {name контейнера} bash` - заходимо на запущений контейнер
