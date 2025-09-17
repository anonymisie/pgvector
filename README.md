docker build -f Dockerfile-pgvector -t pgvec
docker run -dit -e POSTGRES_PASSWORD=1234 --name=pgvec pgvec
