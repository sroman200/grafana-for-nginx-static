#### Цель: Копирование статики grafana в отдельный образ с nginx:alpine используя  --target  параметр
##### Смотреть содержимое Dockerfile.


##### Сборка образов из Dockerfile используя --target
```
sudo docker build --target nginx_static -t grafana:static .
sudo docker build --target ubuntu -t grafana:app .
```

Запуск контейнера из образа
```
docker run -d --rm -p 8089:80 --name dkr-nginx grafana:static
docker run -d --rm -p 3000:3000 --name dkr-grafana grafana:app
```

Вход в контейнер по имени (если нужно)
```
docker exec -ti dkr-nginx sh
docker exec -ti dkr-grafana /bin/bash
```

Запуск c localhost
```
http://127.0.0.1:8089/
```
