//LIBRERIE PYTHON
pip install prometheus_api_client
pip install prometheus_client
pip install confluent_kafka
pip install flask
pip install pandas
pip install json
pip install xlsxwriter
pip install matplotlib
pip install statsmodels
pip install openpyxl
pip install mysql-connector-python==8.0.29


//CREAZIONE DATABASE
create database datastorage

create table metadata(ID int AUTO_INCREMENT PRIMARY KEY, metric_name varchar(255), autocorrelation varchar(6000), stationarity varchar(250), seasonality varchar(6000))
create table metrics(ID int AUTO_INCREMENT PRIMARY KEY, metric_name varchar(255), max double, min double, average double, std double)
create table prediction(ID int AUTO_INCREMENT PRIMARY KEY, metric_name varchar(255), max double, min double, avg double)


create table executiontimep1 (ID int AUTO_INCREMENT PRIMARY KEY, metric_name varchar(255), execution_time varchar(255))
create table executiontimep2 (ID int AUTO_INCREMENT PRIMARY KEY, metric_name varchar(255), execution_time varchar(255))
create table executiontimep3 (ID int AUTO_INCREMENT PRIMARY KEY, metric_name varchar(255), execution_time varchar(255))

create table futureviolation(ID int AUTO_INCREMENT PRIMARY KEY, metric_name varchar(255), rangeMin double,rangeMax double, violations double)
create table pastviolation(ID int AUTO_INCREMENT PRIMARY KEY, metric_name varchar(255), rangeMin double,rangeMax double, violations double)
create table slastatus(ID int AUTO_INCREMENT PRIMARY KEY, metric_name varchar(255), violations varchar(25), execution_time varchar(255))

// SERVER PROMETHEUS CEPH
http://15.160.61.227:29090/graph

// COMANDI DOCKER E KAFKA
1)creare del docker compose
docker-compose up -d&

2) Creazione del topic kafka - stare attenti al nome del composer (dsbd_esame-kafka-1) e al nome del topic (prometheusdata)
docker exec -it dsbd_esame-kafka-1 kafka-topics --create --replication-factor 1 --partitions 1 --topic prometheusdata --bootstrap-server localhost:9092
