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
<br/>
apt-get install gnupg -y <br/>
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add - <br/>
echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/5.0 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list <br/>
apt update <br/>
apt install mongodb-org -y <br/>
<br/>
2. Набиваю данными <br/>
Где то из источников, не запомнил где (потому что большая их часть бесполезная) достал архив который приложил в этой репе (zips.json)<br/>
<br/>
mongoimport -v --file zips.json <br/>
<br/>
3. Несколько запросов на выборку и обновление <br/>
<br/>
use test; <br/>
# первый пришедший на ум запрос<br/>
db.zips.find({city: { $regex: "MOS"}}).limit(10)<br/>
# что то другое<br/>
db.zips.find({state: { $regex: "NY"}}).sort({_id: -1}).limit(20)<br/>
# апдейт записи из вывода первого селекта<br/>
db.zips.update({"_id": "45153"}, {$set: {"pop": 13}})<br/>
# проверка что обновилось <br/>
db.zips.find({city: { $regex: "MOS"}}).limit(10)<br/>
<br/>
4. Создание индексов <br/>
<br/>
# Проверяю какие индексы есть <br/>
db.zips.getIndexes()<br/>
# Создаю свой<br/>
db.zips.createIndex({city: 1})<br/>
# Смотрю по чему будет искать при поиске городов (индекс)<br/>
db.zips.explain().find({city: "MOSCOW"})<br/>
# Смотрю по чему будет искать при поиске штатов (scan)<br/>
db.zips.explain().find({state: "NY"})<br/>