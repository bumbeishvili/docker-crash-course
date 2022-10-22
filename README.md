```bash
# Setting root
FROM node:17-alpine  

# Setting work dir
WORKDIR /app

# copy source from . to workDir
COPY . .

# install dependencies in copied root directory
RUN npm install


# Expose port (written in API).
EXPOSE 4000

# Run command at runtime [when containers start working]
CMD ["node", "app.js"]



```

```bash
# For running this file use command (. means docker file is in the same folder)
docker build -t myapp .


# For starting Docker Container

# For stopping docker container
docker stop ContainerName
```
