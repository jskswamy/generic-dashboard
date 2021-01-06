## Dashboard

### Prerequsite

1. docker
2. docker-compose
3. influx (cli for accessing influxdb)

## Usage

clone the repo locally,

```
git clone https://github.com/jskswamy/generic-dashboard.git
```

copy `.envrc.sample` as `.envrc`

```
cp .envrc.sample .envrc
```

provide/change necessary values in the .envrc


To start grafana and influxdb, run

```bash
docker-compose up -d
```

> Note: ensure to run `source .envrc` everytime before running the above command

To access grafana dasbhoard, open `http://localhost:3000` from the browser

To configure influxdb as source in grafana, login into grafa as an admin using the password
provided in the .envrc file and set new password for the admin user

Then access `http://localhost:3000/datasources/`, and click `Add data source`, choose influxdb 
from the list and provide the following information

```
Under HTTP
url: http://influxdb:8086
```

```
Under InfluxDB Details
Database: metrics (the value you have configured in .envrc for INFLUXDB_DB)
User: metrics (the value you have configured in .envrc for INFLUXDB_USER)
```

To insert data into the influxdb, use the influx from the cli

To query data from influxdb, use the [UI](http://localhost:8080) or the cli

> Note if you are using UI, you need to add server from [settings page](http://localhost:8080/#/settings/)
