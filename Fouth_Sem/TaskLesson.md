# Задачи семинара 4

## Задание 1 (повтор из лекции)

Необходимо самостоятельно создать образ, используя Докерфайл:

```
FROM ubuntu:22.10
RUN apt-get update && \
    apt-get install -y cowsay && \
    ln -s /usr/games/cowsay /usr/bin/cowsay && \
    rm -rf /var/lib/apt/lists/*
CMD [“cowsay”]
```

**Запустить его и убедиться, что все работает**

## Задание 2

Создайте файл example.txt и положить его рядом с докерфайлом. Наполните файл простыми данными (любыми) и сохраните. 
Вот вам первый Dockerfile:
```
FROM ubuntu:22.10
RUN apt-get update && \
    apt-get install -y cowsay && \
    ln -s /usr/games/cowsay /usr/bin/cowsay && \
    rm -rf /var/lib/apt/lists/*
COPY example.txt /
CMD [“cowsay”]
```

Соберите из него образ. Запускать его не нужно. Теперь измените файл example.txt и соберите Докерфайл заново.
Операцию можно повторить дважды для понимания, что происходит.
И второй Dockerfile:

```
FROM ubuntu:22.10
COPY example.txt /
RUN apt-get update && \
    apt-get install -y cowsay && \
    ln -s /usr/games/cowsay /usr/bin/cowsay && \
    rm -rf /var/lib/apt/lists/*
CMD [“cowsay”]
```

Также необходимо собрать образ из докерфайла. После первой сборки необходимо изменить файл example.txt и повторить сборку. Также проделать несколько раз для понимания, что происходит.

## Задание 3

В этом задании нужно собрать образ по выданным докерфайлам и снова определить различия.

Собственно, первый докерфайл:
```
FROM ubuntu:22.10
COPY example.txt /
CMD sleep 600
```
И второй:
```
FROM ubuntu:22.10
COPY example.txt /
ENTRYPOINT sleep 600
```

Попытаться запустить из образа контейнер и войти в командный интерпретатор.

## Задание 4

В этом задании нужно собрать образ по выданным докерфайлам и открыть порты для доступа в контейнер извне
В данном задании демонстрируется работа инструкции EXPOSE.
Собственно, докерфайл:

```
FROM ubuntu:22.10
RUN apt-get update && \
    apt-get install -y nginx && \
    ln -s /usr/games/cowsay /usr/bin/cowsay && \
    rm -rf /var/lib/apt/lists/*
RUN echo 'Hi, I am in your container' \
        >/usr/share/nginx/html/index.html
EXPOSE 80
```

Попытаться запустить из образа контейнер и получить информацию утилитой curl.


