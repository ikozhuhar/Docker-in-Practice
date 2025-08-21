:white_check_mark: _**Задача:** <a name='1'>Собирать и запустить образ Docker</a>._

```ruby
# Пишем Dockerfile. Dockerfile – это текстовый файл, содержащий серию команд.
FROM node
 LABEL maintainer ian.miell@gmail.com
 RUN git clone -q https://github.com/docker-in-practice/todo.git
 WORKDIR todo
 RUN npm install > /dev/null
 EXPOSE 8000
 CMD ["npm","start"]

# Собираем образ Docker
docker build .
```

Теперь у вас есть образ Docker со своим идентификатором. 
Возможно, к нему неудобно обращаться по ID, поэтому можно присвоить ему тег для удобства.

```ruby
sudo docker tag <id_image> todoapp
```

Запускаем контейнер Docker

```ruby
# Подкоманда docker run запускает контейнер. Флаг -p перенаправляет порт контейнера 8000 в порт 8000 на хост-компьютере,
# поэтому теперь вы можете перейти в своем браузере по адресу http://localhost:8000 для просмотра приложения.
# Флаг -name присваивает контейнеру уникальное имя, к которому вы можете обратиться позже для удобства.
# Последний аргумент – это имя образа
sudo docker run -i -t -p 8000:8000 --name example1 todoapp
```
