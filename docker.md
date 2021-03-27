# Docker

- **build a dockerfile** in the current directory (`.`): `docker build <image-name> .`

## Resources

- Create a new dockerfile: <https://docs.docker.com/engine/getstarted/step_four/#step-3-learn-about-the-build-process>

## Images

Docker images are builds from a recipe. E.g., they can be a straight ubuntu build, or include an ubuntu system setup with Kaggle's data science Python packages (<http://blog.kaggle.com/2016/02/05/how-to-get-started-with-data-science-in-containers/>)

### List

List available images:

```
docker images
```

## Delete

Delete images

```
docker rmi <image-name or hash>
```

## Containers

### List

List containers currently running (active)

```
docker ps
```

List all containers

```
docker ps -a
```

### Stop non-responsive container

```
docker rm -fv <container-id>
```


Alternatively, kill it by `pid`:
Find containers with `ps aux | grep docker`

## Delete

Delete containers:

```
docker rm <container-id or name>
```


## CLI tricks

**Login to docker**

```bash
docker_ssh() {
  docker exec -i -t $1 /bin/bash
  }
```

**Start up with custom config**
Usage: gpsdocker /path/to/dir
```bash
gpsdocker() {
    cd $1/spark/
    docker run -d -P --name pyspark -v $PWD:/home/jovyan/work jupyter/pyspark-notebook:c1b0cf6bf4d6 start-notebook.sh --NotebookApp.token=''
    echo "running pyspark on: "$(docker port pyspark)
}

```
