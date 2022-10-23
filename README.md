```bash
# Setting root
FROM node:17-alpine  

RUN npm install -g nodemon

# Setting work dir
WORKDIR /app

# Copy package json first, so that we can cache installed packages later
COPY package.json .

# install dependencies in copied root directory
RUN npm install

# copy source from . to workDir
COPY . .




# Expose port (written in API).
EXPOSE 4000

# Run command at runtime [when containers start working]
CMD ["npm","run","dev"]



```

```bash
# For running this file use command (. means docker file is in the same folder)/
# We can add :tag to name - `docker build -t myapp:v1 .`
docker build -t myapp .


# list all used containers (add -a flag for all)
docker ps

# list all images
docker images

# Remove image.  (add -f to force deletion)
docker rm ImageName

# Remove container (we can remove multiple, by appending `docker container rm name1 name2`)
docker container rm ContainerName

# For creating/running Docker Container. (--rm means remove once not used)
# we can add -v flag for adding volumes, in order container to react on changes. Need an absolute path and app path `-v ABSOLUTE_PATH:DockerWorkDirPath`
# We need to run npm install locally before
docker run --name ContainerName -p 4000:4000 --rm ImageName:TagName 

# For starting created container
docker start ContainerName

# For stopping docker container
docker stop ContainerName


# removes all containers, all images and volumes
docker system prune -a



```

```yaml
version: "3.8"
services: 
  api:
    build:  ./api
    container_name: api_c
    ports: 
      - '4000:4000'
    volumes:  #For hot reloade
      - ./api:/app
      - ./app/node_modules  # making sure node moduels won't get deleted

```

```bash
# start & generate docker images and components
docker-compose up


# stop 
docker-compose down


```