# fergs_ml_platform


Tools: 
- [x] Relation db for raw tabular data 
    - postgres 
- [ ] Feature store
    - feast 
- [ ] Experiment management
    - mlflow 
- [ ] Observability 
    - 
- [ ] Orchestration? 
    - 
- [ ] CICD 
    - Local github runners 



## Docker setup 

Network create: `docker network create ml_platform`
Start swarm: `docker compose up`
Find ip for uis : `docker network inspect ml_platform`
Rebuild a single container ; `docker-compose build --no-cache feast`

https://min.io/docs/minio/kubernetes/upstream/index.html?ref=docs-redirect

## Mlflow 

- Backend storee.... 

By default, the tracking server logs runs metadata to the local filesystem under ./mlruns directory. 

Build ; `docker build -t mlflow-server-image .`
Run : `docker run --name mlflow-server-container mlflow-server-image`
removed container `docker rm mlflow-server-container`

## Postgres management: 

`docker exec -it ml_raw_data_posgres_db psql -U ${POSTGRES_USER} -d ${POSTGRES_DB}`

### Air quality data 
```
CREATE TABLE IF NOT EXISTS air_quality (
    timestamp TIMESTAMP NOT NULL,
    station_name VARCHAR(100) NOT NULL,
    aqi FLOAT,
    pm25 FLOAT,
    pm10 FLOAT,
    o3 FLOAT,
    no2 FLOAT,
    so2 FLOAT,
    co FLOAT,
    PRIMARY KEY (timestamp, station_name)
);
```

## Feast 

Refs: 
- https://redis.io/blog/feast-with-redis-tutorial-for-machine-learning/
- https://docs.feast.dev/master/getting-started/components/overview
- https://docs.feast.dev/how-to-guides/running-feast-in-production

Concepts:
- feature registry
- feast sdk
- feature server 
- offline store 
- online store 
- feature repo: stores config for features 

Getting setup: 
1. Create repo of feature definitions (this is seperate... just store in project for now!)
2. Creating a database-backed registry 

Need to build:
1. The ui 
2. The registry postgres db 
3. offline store 
4. online store
