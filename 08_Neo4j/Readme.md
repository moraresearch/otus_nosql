# Домашнее задание по Neo4j 
<br/>
---
<br/>
### Задание:
<br/>
Поднять Neo4j.<br/>
Создать базенку окружения.<br/>
<br/>
---
<br/>
### Решение:<br/>
<br/>
База поднимается командой <br/>
docker run -p7474:7474 -p7687:7687 neo4j <br/>
После этого клепаем окружение такими командами: <br/>
<br/>
##### create (:human {name: 'Alina', age: '25', property: 'cat'}) <br/>
<br/>
##### match (one:human {name: 'Diana'})<br/>
##### match (two:human {name: 'Natasha'})<br/>
##### create (two) -[:Friends]->(one)<br/>
<br/>
---
<br/>
Я положил в репу как records.json так и скрин базы (до сих пор скрин базы было шуткой =))<br/>
<br/>
