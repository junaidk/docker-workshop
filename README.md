## Docker Training 


### Docker installation
https://gist.github.com/junaidk/cab20d32d0e4d7ec9742022713f83dea


### Create a network

```
docker network create flask-net
```

### Postgress 

https://hub.docker.com/_/postgres

```
docker run -d \
-e POSTGRES_PASSWORD=mysecretpassword \
--net flask-net \
--name flask-postgres \
-v /my/own/datadir:/var/lib/postgresql/data \
 postgres
```

### Flask app

https://github.com/Azure-Samples/flask-postgresql-app

```
docker build -t my-flask .
```

```
docker run -it -p 5000:5000 \
-e DBHOST=flask-postgres \
-e DBPASS=mysecretpassword \
-e DBUSER=postgres \
-e DBNAME=postgres \
--net flask-net \
--name flask-app \
my-flask
```




