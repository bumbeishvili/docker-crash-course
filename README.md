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
# For running this file use command (. means docker file is in the same folder)
docker build -t myapp .


# list all used containers (add -a flag for all)
docker ps

# list all images
docker images

# For starting Docker Container

# For stopping docker container
docker stop ContainerName



```
