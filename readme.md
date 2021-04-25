https://www.youtube.com/watch?v=gm_L69NHuHM

docker image build -t node-docker .

# read-only bi-mount

"ro"
docker container run -p 5000:5000 -v $(pwd):/app:ro -v /app/node_modules --name node-docker-con node-docker

# set env

"--env PORT=8080"
docker container run -p 8080:8080 --env PORT=8080 -v $(pwd):/app:ro -v /app/node_modules --name node-docker-con node-docker

# set env through file

"-env-file ./.env"
docker container run -p 8080:8080 --env-file ./.env -v $(pwd):/app:ro -v /app/node_modules --name node-docker-con node-docker

# docker-compose development and production

# "--build" rebuild

docker-compose -f docker-compose.yml -f docker-compose.dev.yml up --build
