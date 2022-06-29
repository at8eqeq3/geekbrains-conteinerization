# Домашнее задание к уроку 2 - Docker

Напишите Dockerfile к любому приложению из директорий golang или python на ваш выбор (можно к обоим).

Образ должен собираться из официального базового образа для выбранного языка. На этапе сборки должны устанавливаться все необходимые зависимости, а так же присутствовать команда для запуска приложения.

Старайтесь следовать рекомендациям (Best Practices) из лекции при написании Dockerfile.

При запуске контейнера из образа с указанием проксирования порта (флаг -p или -P если указан EXPOSE) при обращении
на localhost:port должно быть доступно приложение в контейнере (оно отвечает Hello, World!).

Сохраните получившийся Dockerfile в любом публичном Git репозитории, например GitHub, и пришлите ссылку на репозиторий.

# Выполнение

### Python

Из нехитрого [Dockerfile](python/Dockerfile) при помощи `docker build -t gb:l2-python .`. Теперь так:

```
$ docker images gb
REPOSITORY   TAG         IMAGE ID       CREATED         SIZE
gb           l2-python   aaa922c27856   6 minutes ago   59.8MB
```

Теперь запустим `docker run --rm -p 8080:8080 gb:l2-python` и в соседнем терминале сделаем

```
$ curl http://localhost:8080
Hello, World!
```

Успех!

### Golang

Здесь в соответствии с рекомендациями собираем имидж в два этапа: [Dockerfile](golang/Dockerfile). Образов прибавилось:

```
$ docker images gb
REPOSITORY   TAG         IMAGE ID       CREATED          SIZE
gb           l2-golang   dc95582cb863   53 seconds ago   6.57MB
gb           l2-python   aaa922c27856   18 minutes ago   59.8MB
```

Аналогично запустим `docker run --rm -p 8080:8080 gb:l2-golang` и проверим curl:

```
$ curl http://localhost:8080
Hello, World!
```

Успех!