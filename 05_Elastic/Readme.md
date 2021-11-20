# Домашнее задание по elasticsearch 
<br/>
---
<br/>
Задание:<br/>
поднять эластик<br/>
поднять для него веб морду<br/>
создать индекс <br/>
залить данные <br/>
создать поисковый запрос<br/>
<br/>
---
<br/>
Решение: <br/>
<br/>
Поднять kibana+elastic <br/>
docker-compose up -d <br/>
подождать пока оно поднимется<br/>
http://localhost:5601 <br/>
<br/>
создание индекса и наполнение данными есть в файле history<br/>
<br/>
создание индекс паттерн <br/>
http://localhost:5601/app/management/kibana/indexPatterns<br/>
тут нужно покликать. <br/>
<br/>
поисковый запрос - последняя строка файла history. <br/>
<br/>
