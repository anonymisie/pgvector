```bash
# set vars and prepare env file
mv .env.example .env

#### set tag, admin pass and db

# #NOT WORKING build-date based
# TAG=$(date +%Y%m%d%H%M%S)

### build image
docker build -f Dockerfile-CUSTOM -t pgvector:$TAG
### run container 
docker run -dit -e POSTGRES_PASSWORD=1234 --name=pgvector pgvec:$TAG

### alternatively to build and run use docker compose file (or no build if image exists)
docker-compose up -d .
docker-compose up -d . --no-build 


## testing pgvector
docker exec -it pgvector bash
psql -h localhost -U postgres -d postgres -c '\dx'


## access adminer in browser
## in adminer use host.containers.internal (podman) or host.docker.internal (docker) as db host
## !!!!!! be aware of unencrypted http and sensitive info in url
http://localhost:8088/?pgsql=host.containers.internal&username=admin&db=initdb&ns=public


```
