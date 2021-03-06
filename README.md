# docker-k6-grafana-influxdb

> Demonstrates how to run load tests with dockerized K6, Grafana and InfluxDB

**Article**
What is K6?
* [https://ggaugain.github.io/#/techno/k6](https://ggaugain.github.io/#/techno/k6)

**Grafana Dashboard**
A dashboard for visualizing results from the k6.io load testing tool, using the InfluxDB exporter
* https://grafana.com/grafana/dashboards/2587

**Usage**

```
# Requirements
$ docker
$ docker-compose
$ git

# Clone the source repo
git clone 'https://github.com/ggaugain/docker-k6-grafana-influxdb.git'
cd docker-k6-grafana-influxdb

# Update git submodules
git submodule update --init

# Deploy influxdb and grafana containers in the background
docker-compose up -d influxdb grafana

# Run the k6 container separately so that you don't have to restart influx and grafana every time you want to run your tests
docker-compose run -v $PWD/samples:/scripts k6 run /scripts/k6test.js
```

Navigate to http://localhost:3000 to access the Grafana interface.


**Issue with influxdb:2**
There is a problem with InfluxDB v2: https://github.com/loadimpact/k6/issues/1883
Pin the image version to influxdb:1.8 it should work.