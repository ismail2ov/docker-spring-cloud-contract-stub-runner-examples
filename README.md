# Docker Spring Cloud Contract Stub Runner examples
This is a repository with examples of how to use Docker images to run stubs created with [Spring Cloud Contract](https://cloud.spring.io/spring-cloud-contract/).  
The base image is created in project [Docker image to run stubs created with Spring Cloud Contract](https://github.com/ismail2ov/docker-spring-cloud-contract-stub-runner).  

## How to use?
  
You can use the [Dockerfile](docker-image/Dockerfile) in the [docker-images](docker-image) folder as a base.
  
For this example we will use the stubs created with the project [contract-testing-demo](https://github.com/ismail2ov/contract-testing-demo).
  
### Set the Env Vars

- `STUBS_GROUP_ID` - Project group Id, default value is `org.example`
- `STUBS_ARTIFACT_ID` - Project artifact Id, default value is `untitled`
- `STUBS_VERSION` - Artifact version, default value is `1.0-SNAPSHOT`
- `STUBS_FOLDER` - It is the folder in which the stubs will be copied, its value is the same as `STUBS_PACKAGE` replacing the points (`.`) with a slash (`/`), default value is `org/example`
- `STUBRUNNER_PORT` - The port on which the stubs will run, default is a random port
  
### Build Docker image

```bash
$ docker build --tag my-catalog-stubs .
```

### Run Spring Cloud Contract Stub Runner

```bash
$ docker run --rm  --name my-catalog-stubs -p 8080:8080 my-catalog-stubs
```

### Check the stub runner is running 

```bash
$ curl -i localhost:8080/products
```
