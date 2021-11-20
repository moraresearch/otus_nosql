# Домашнее задание по couchdb
<br/>
---
<br/>
<br/>
### Задание: <br/> 
Запустить сервер couchdb <br/>
Создать базу rep1 <br/> 
Создать запись с полем name <br/>
Отредактировать скрипт в прмере и запустить проксю которая стянет данные из базы. <br/> 
Убедиться что робит. <br/>
<br/>
--- 

### Решение: <br/>
<br/>
#### Запуск в докере базы и прокси: <br/>
docker run --name nginx -p 80:80 -v /home/mora/git/otus_nosql/04_CouchDB/:/usr/share/nginx/html -d nginx <br/>
docker run -d --name couchdb --restart always -p 5984:5984 couchdb:2 <br/>
<br/>
#### Создание базы: <br/>
curl -X PUT http://localhost:5984/rep1 <br/>
<br/>
#### Создание записи: <br/>
curl -X PUT http://127.0.0.1:5984/rep1/01 -d  {"name": "mora"} <br/>
<br/>
#### Насроить базу чтобы не ругалась(включить корс):  <br/>
http://localhost:5984/_utils/#_config/nonode@nohost/cors
<br/>
Теперь можно переходить по http://localhost и нажав кнопку sync увидеть созданную запись. 
