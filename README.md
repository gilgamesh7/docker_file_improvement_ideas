# docker_file_improvement_ideas
How to Make Your Python Docker Image 80% Smaller 

### Links
- [Arjan's Repo](https://github.com/ArjanCodes/examples/tree/main/2025/efficient-python-dockerfile)
- [Youtube video](https://www.youtube.com/watch?v=tc713anE3UY)

### Local set up
- poetry init
- poetry config virtualenvs.in-project true
- poetry add fastapi
- poetry add uvicorn

### Run locally
- uvicorn src.main:app
- [URL through Browser, no params)](http://localhost:8080/)
- [URL through Browser, pass in params (add ?name=<aname> as parameter after /)](http://localhost:8080/?name=DarkForest)

### Docker build & Run command line
#### Original image
docker build \
    --build-arg DB_HOST=mydbhost \
    --build-arg DB_USER=mydbuser \
    --build-arg DB_PASSWORD=mydbpassword \
    --build-arg DB_NAME=mydbname \
    --no-cache \
    --build-arg ACCESS_TOKEN_SECRET=myaccesstokensecret \
    -f Dockerfile.01.original . -t 01_original && \
docker run -d -p 8080:8080 --name my_running_container 01_original

#### Better image
docker build \
    --build-arg DB_HOST=mydbhost \
    --build-arg DB_USER=mydbuser \
    --build-arg DB_PASSWORD=mydbpassword \
    --build-arg DB_NAME=mydbname \
    --no-cache \
    --build-arg ACCESS_TOKEN_SECRET=myaccesstokensecret \
    -f Dockerfile.02.betterimg . -t 02_betterimg && \
docker run -d -p 8080:8080 --name my_running_container 02_betterimg

#### Tagged image
docker build \
    --build-arg DB_HOST=mydbhost \
    --build-arg DB_USER=mydbuser \
    --build-arg DB_PASSWORD=mydbpassword \
    --build-arg DB_NAME=mydbname \
    --no-cache \
    --build-arg ACCESS_TOKEN_SECRET=myaccesstokensecret \
    -f Dockerfile.03.tagged . -t 03_tagged && \
docker run -d -p 8080:8080 --name my_running_container 03_tagged

#### Limit dependencies
docker build \
    --build-arg DB_HOST=mydbhost \
    --build-arg DB_USER=mydbuser \
    --build-arg DB_PASSWORD=mydbpassword \
    --build-arg DB_NAME=mydbname \
    --no-cache \
    --build-arg ACCESS_TOKEN_SECRET=myaccesstokensecret \
    -f Dockerfile.04.limitdeps . -t 04_limitdeps && \
docker run -d -p 8080:8080 --name my_running_container 03_tagged

#### Clean up metadata
docker build \
    --build-arg DB_HOST=mydbhost \
    --build-arg DB_USER=mydbuser \
    --build-arg DB_PASSWORD=mydbpassword \
    --build-arg DB_NAME=mydbname \
    --no-cache \
    --build-arg ACCESS_TOKEN_SECRET=myaccesstokensecret \
    -f Dockerfile.05.cleandeps . -t 05_cleandeps && \
docker run -d -p 8080:8080 --name my_running_container 05_cleandeps

#### use UV
docker build \
    --build-arg DB_HOST=mydbhost \
    --build-arg DB_USER=mydbuser \
    --build-arg DB_PASSWORD=mydbpassword \
    --build-arg DB_NAME=mydbname \
    --no-cache \
    --build-arg ACCESS_TOKEN_SECRET=myaccesstokensecret \
    -f Dockerfile.06.uv . -t 06_uv && \
docker run -d -p 8080:8080 --name my_running_container 06_uv

### Test
- docker ps (get CONTAINER ID)
- docker exec -it  CONTAINER ID curl http://localhost:8080