```bash
#set vars and prepare env file
mv .env.example .env

#harcoded
TAG=1.0.0

#build-date based
TAG=$(date +%Y%m%d%H%M%S)

#build image
docker build -f Dockerfile-CUSTOM -t pgvec:$TAG

# run container 
docker run -dit -e POSTGRES_PASSWORD=1234 --name=pgvec pgvec
# alternatively use docker compose file
docker-compose up -d .



## testing pgvector
docker exec -it pgvec bash

psql -h localhost -U postgres -d postgres -c '\dx'

```
