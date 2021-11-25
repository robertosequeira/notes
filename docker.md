# Docker


- List containers

  ```
  $ docker ps
  ```

- Get container logs

  ```
  $ docker logs [friendly name | container id]
  ```
 
- Inspect container

  ```
  $ docker inspect [friendly name | container id]
  ```

## Run containers

- In attached mode

  ```
  $ docker run --name redisAttached redis:latest
  ```

- In detached mode and give it a friendly name

  ``` 
  $ docker run -d --name redisHello redis:latest
  ```

- Bind \<host\>:\<container\> ports

  ```
  $ docker run -d --name redisPort -p 6379:6379 redis:latest 
  ```

- Bind \<container\> port to a random available port in the host
  
  ```
  $ docker run -d --name redisDynamicPort -p 6379 redis:latest
  ```

- Bind directories

  ```
  $ docker run -d --name redisMapped -v "$PWD/data":/data redis
  ```
- Run command in container and print output

  ```
  $ docker run ubuntu ps
  ```
