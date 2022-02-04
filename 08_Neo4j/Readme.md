# Домашнее задание по Neo4j 

## Задание:

Поднять Neo4j.<br/>
Создать базенку окружения.<br/>
<br/>

## Решение:

База поднимается командой <br/>

##### docker run -p7474:7474 -p7687:7687 neo4j

После этого клепаем окружение такими командами: <br/>
<br/>
##### create (:human {name: 'Alina', age: '25', property: 'cat'})

<br/>

##### match (one:human {name: 'Diana'})
##### match (two:human {name: 'Natasha'})
##### create (two) -[:Friends]->(one)

<br/>

### Я положил в репу как records.json так и скрин базы (до сих пор скрин базы было шуткой =))
