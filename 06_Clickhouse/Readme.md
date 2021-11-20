# Домашнее задание по Clickhouse
<br/>
---
<br/>
Задание: <br/>
<br/>
поставить сервер clickhouse <br/>
накатить тестовые данные<br/>
покидать запросов <br/>
<br/>
---
<br/>
Решение: <br/>
<br/>
Запускается база и клиент командой <br/>
docker-compose up -d <br/>
после этого будем работать внутри одного из созданных контейнеров (чтобы по окончании командой down заодно все подчистить)<br/>
docker exec -ti 06_clickhouse_ch_client_1 bash <br/>
установим софт<br/>
apt update; apt install curl -y<br/>
скачаем тестовые данные <br/>
curl https://datasets.clickhouse.com/hits/tsv/hits_v1.tsv.xz | unxz --threads=`nproc` > hits_v1.tsv<br/>
создадим базу и таблицу из примера в ссылке дз (там куча текста, получится нечитаемый ридми) https://clickhouse.com/docs/ru/getting-started/tutorial/<br/>
пульнем пару тройку запросов посмотреть производительность базы(вывод консоли в файле console). <br/>
что ж - это прикольно, на почти 9 милллионов строк такая быстрая обработка. <br/>