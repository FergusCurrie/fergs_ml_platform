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