```bash
# Setting root
FROM node:17-alpine  

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
CMD ["node", "app.js"]



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

# For starting/running Docker Container
docker run --name ContainerName -p 4000:4000 ImageName:TagName


# For stopping docker container
docker stop ContainerName


# removes all containers, all images and volumes
docker system prune -a



```
