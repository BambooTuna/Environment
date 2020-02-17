# vuecli4

## Start
```bash
$ docker-compose up --build -d
```

## Create Project
```bash
$ docker-compose exec vuecli4 vue create .
```

## Run Server
```bash
$ docker-compose exec vuecli4 npm run serve -- --port 9050 --host 0.0.0.0
or
$ docker-compose exec vuecli4 PORT=9050 HOST=0.0.0.0 npm run serve
```
Access http://localhost:9050
