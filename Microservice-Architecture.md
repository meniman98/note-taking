# Microservice architecture
A step by step guide to make a microservices architecture

Have a look at this diagram below

![image](https://user-images.githubusercontent.com/33395236/187933464-9cf7f0eb-630b-4b1c-b7bf-d0662d90b515.png)

## Components
1. Services - these would be things like User service, Department service
2. Discovery server - where your services will exist
3. API gateway - where all your API calls go to
4. Config server - where default configuration settings are stored remotely
5. History dashboard - an insight into all the calls made, how many have been successful, how many have failed

### Services
Dependencies needed:
1. JPA
2. H2
3. Lombok
4. Spring web
5. Eureka client

Your service will be your API. Build them first. Firstly add your @EnableEurekaClient, then add this in your properties file:

```
server.error.include-message=always
server.port = 9001
spring.application.name = SHARE-SERVICE
eureka.client.register-with-eureka = true
eureka.client.fetch-registry = true
eureka.client.service-url.defaultZone: http://localhost:8761/eureka/
eureka.client.instance.hostname = localhost
```

### Discovery server
Dependencies needed:
1. Eureka server

The discovery server or registry will keep track of all your services. Add @EnableEurekaServer, then add the following in your properties file:

```
server.port = 8761
eureka.client.register-with-eureka = false
eureka.client.fetch-registry = false
logging.level.com.netflix.eureka=OFF
logging.level.com.netflix.discovery=OFF
```

### API Gateway

Dependencies needed:
1. Eureka client
2. Gateway
3. Spring Boot Actuator

Your API gateway will be the place where all calls are made

Make sure to enable eureka on the main application. Below is an example of your properties file

```
server.port = 9191
spring.application.name = API-GATEWAY

spring.cloud.gateway.routes[0].id = SHARE-SERVICE
spring.cloud.gateway.routes[0].uri = lb://SHARE-SERVICE
spring.cloud.gateway.routes[0].predicates = Path=/shares/**

spring.cloud.gateway.routes[0].filters[0].name = CircuitBreaker
spring.cloud.gateway.routes[0].filters[0].args.name = SHARE-SERVICE
spring.cloud.gateway.routes[0].filters[0].args.fallbackuri = forward:/fallback

hystrix.command.fallbackcmd.execution.isolation.thread.timeoutInMilliseconds = 4000
management.endpoints.web.exposure.include = hystrix.stream

eureka.client.register-with-eureka = true
eureka.client.fetch-registry = true
eureka.client.service-url.defaultZone: http://localhost:8761/eureka/
eureka.client.instance.hostname = localhost
eureka.instance.prefer-ip-address=true
```

####

