# Config Server Microservice (config-server)

## Description

The Config Server is a microservice in charge of centralized configuration management for the other microservices in the ecosystem. Provides access to external configurations stored in a remote repository (for example, GitHub). This allows you to maintain single control of configuration parameters and facilitates updating without needing to restart services.

## Pre - requisites

- **Java 20**
- **Maven**
- **Docker** (for Docker execution only)
- Red Docker compartida: `my-network`


## Initial Configuration

### Run Locally

#### Modify the file`bootstrap.yml`

Configure the active profile to use Docker:

```yaml
spring:
  profiles:
    active: local
```

#### Execute the Main Class

```yaml
mvn spring-boot:run
```
Alternatively, if using an IDE (e.g., IntelliJ IDEA, Eclipse), navigate to the ConfigServerApplication class and run it directly.

### Run Docker

#### Modify the file`bootstrap.yml`

Configure the active profile to use Docker:

```yaml
spring:
  profiles:
    active: docker
```
#### Compile and generate the Docker container
Build the Docker image with:

```yaml
docker build -t config-server:0.0.1-SNAPSHOT .
```

####  Run the microservice Docker container
Start the container with:

```yaml
docker run --name config-server --network my-network -p 8888:8888 config-server:0.0.1-SNAPSHOT
```
## Resources:
- **Resource link  - https://github.com/evalladares-t/resource-bootcamp57**
- **Link github  - https://github.com/evalladares-t**

## Notes:
- **If you need to change ports or other settings, edit the corresponding application.yml and Dockerfile files.**
- **To debug errors, check the container logs:**
    ```yaml
    docker logs config-server
    ``` 
- **Make sure that the Config Server and Registry Server are running before starting other services.**
