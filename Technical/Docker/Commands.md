---
tag: Docker
---

- Create docker from image
    
    ```bash
    docker create <image-name>
    ```
    
- Run container
    
    ```bash
    docker run -a <container-id> (a: Output log from container)
    ```
    
- Create a temporary container and execute command and stop when done
    
    ```bash
     docker run -it <container-name> <command>
    ```
    
- Execute a command in running container
    
    ```bash
    docker exec -it <container-name> <command>
    ```
    
- Export mapping container port
    
    ```bash
    docker run -p 8080(1):8080(2) <image-name>
    
    - 1: Route incoming requests to outside port
    - 2: Port inside the container
    ```
    
- Logs
    
    ```bash
    docker logs <container-name>
    ```
    
- Run docker with **exported variables:**
    
    ```bash
    docker run -d -ex MYSQL_PASSWORD=test mysql:5.7
    ```
    




