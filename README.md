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
docker build \
    --build-arg DB_HOST=mydbhost \
    --build-arg DB_USER=mydbuser \
    --build-arg DB_PASSWORD=mydbpassword \
    --build-arg DB_NAME=mydbname \
    --no-cache \
    --build-arg ACCESS_TOKEN_SECRET=myaccesstokensecret \
    -f Dockerfile.01.original . -t 01_original && \
docker run -d -p 8080:8080 --name my_running_container 01_original

### Test
- docker ps (get CONTAINER ID)
- docker exec -it  CONTAINER ID curl http://localhost:8080