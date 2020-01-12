# spring-boot-microservices-series
Code for SpringBoot MicroServices Blog Series

## Pre-Requisites
 - Java 11
 - Docker(https://store.docker.com/editions/community/docker-ce-desktop-windows)
 - Vault(https://www.vaultproject.io/)
 - RabbitMQ (http://www.rabbitmq.com/install-windows.html)

## How to run?

### SetUp Vault in windows

Download and extract the exe file to /config folder

execute command vault server -dev

copy the root token displayed to vault-init.bat file and in new terminal run it.

If above step is not working then manually add values by visiting http://127.0.0.1:8200/ui/vault/secrets/secret/list

### Build all modules:

`spring-boot-microservices-series> ./mvnw clean package -DskipTests=true`

### Start infrastructure modules in docker:

`spring-boot-microservices-series> docker-compose up -d postgresql rabbitmq setup-vault config-server service-registry hystrix-dashboard`

**Start each microservice either in local or in docker:**

**Local:** `spring-boot-microservices-series/catalog-service> ./mvnw spring-boot:run`

**Docker:** `spring-boot-microservices-series> docker-compose up -d <service> --build --force-recreate`

Ex: `spring-boot-microservices-series> docker-compose up -d --build --force-recreate catalog-service inventory-service order-service shoppingcart-ui`

docker-compose up -d catalog-service inventory-service order-service shoppingcart-ui


* MySQL container:
     * hostname: mysqldb
     * Ports : 3306:3306 (<host_port>:<container_port>)
     * Username/Password: root/admin

* RabbitMQ:
     * hostname: rabbitmq
     * Ports: 5672:5672, 15672:15672
     * Admin UI: http://localhost:15672
     * Username/password: guest/guest

* Vault:
    * hostname: vault
    * Ports: 8200:8200
    * Root token: 934f9eae-31ff-a8ef-e1ca-4bea9e07aa09

* config-server:
    * hostname: config-server
    * Ports: 8888:8888
    * URL: http://localhost:8888/

* service-registry:
    * hostname: service-registry
    * Ports: 8761:8761
    * URL: http://localhost:8761/
    
* hystrix-dashboard:
    * hostname: hystrix-dashboard
    * Ports: 8788:8788
    * URL: http://localhost:8788/hystrix

* catalog-service:
    * hostname: catalog-service
    * Ports: 18181:8181
    * URL: http://localhost:18181
    
* inventory-service   
    * hostname: inventory-service
    * Ports: 18282:8282
    * URL: http://localhost:18282
    
* order-service  
    * hostname: order-service
    * Ports: 18383:8383
    * URL: http://localhost:18383 
    
* shoppingcart-ui    
    * hostname: shoppingcart-ui
    * Ports: 18080:8080
    * URL: http://localhost:18080