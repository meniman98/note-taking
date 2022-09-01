# Microservice architecture
A step by step guide to make a microservices architecture

Have a look at this diagram below

![image](https://user-images.githubusercontent.com/33395236/187933464-9cf7f0eb-630b-4b1c-b7bf-d0662d90b515.png)

## Components
1. Services
2. Discovery server
3. API gateway
4. Config server
5. History dashboard

### Services
Dependencies needed:
1. JPA
2. H2
3. Lombok
4. Spring web
5. Eureka client

Your service will be your API. Build them first

### Discovery server
Dependencies needed:
1. Eureka server

The discovery server or registry will keep track of all your services

### API Gateway

Your API gateway will be the place where all calls are made

####

