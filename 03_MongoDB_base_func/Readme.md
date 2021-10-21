# Задание 03 Базовые возможности mongodb
---
<br/>
Задание : <br/>
    1. Поставить монгу. <br/>
    2. Набить данными. <br/>
    3. Написать несколько запросов на выборку и обновление данных. <br/>
    4. Создать индексы и сравнить производительность. <br/>
<br/>
---
1. Ставлю монгу <br/>
```
apt-get install gnupg -y 
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/5.0 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list
apt update
apt install mongodb-org -y 
```
2. Набиваю данными <br/>
Где то из источников, не запомнил где (потому что большая их часть бесполезная) достал архив который приложил в этой репе (zips.json)<br/>
```
mongoimport -v --file zips.json <br/>
```
3. Несколько запросов на выборку и обновление <br/>
```
use test; 
# первый пришедший на ум запрос
db.zips.find({city: { $regex: "MOS"}}).limit(10)
# что то другое
db.zips.find({state: { $regex: "NY"}}).sort({_id: -1}).limit(20)
# апдейт записи из вывода первого селекта
db.zips.update({"_id": "45153"}, {$set: {"pop": 13}})
# проверка что обновилось 
db.zips.find({city: { $regex: "MOS"}}).limit(10)
```
4. Создание индексов <br/>
```
# Проверяю какие индексы есть 
db.zips.getIndexes()
# Создаю свой
db.zips.createIndex({city: 1})
# Смотрю по чему будет искать при поиске городов (индекс)
db.zips.explain().find({city: "MOSCOW"})
# Смотрю по чему будет искать при поиске штатов (scan)
db.zips.explain().find({state: "NY"})
```