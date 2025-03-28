# Microservices Architecture - Example

This application consists of 6 services.

## 1. [API Gateway](https://github.com/code-with-rj1399/microservice-with-sb-api-gateway)
- **Port:** `8083`
- Acts as the entry point for handling and routing requests to the **[Department Service](https://github.com/code-with-rj1399/microservice-with-sb-department-service)** and **[Employee Service](https://github.com/code-with-rj1399/microservice-with-sb-employee-service)**.
- **URL:** [http://localhost:8083](http://localhost:8083)

## 2. [Config Server](https://github.com/code-with-rj1399/microservice-with-sb-config-server)
- **Port:** `8088`
- Centralized configuration service for managing settings of all microservices.
- Services pull their configuration from this server on startup.
- **URL:** [http://localhost:8088](http://localhost:8088)

## 3. Zipkin - Distributed Tracing Service
- **Port:** `9411`
- Used for aggregating logs and tracing requests across microservices.
- **To start Zipkin:**
  ```sh
  docker run -d -p 9411:9411 openzipkin/zipkin
  ```
    - Access it at: [http://localhost:9411/zipkin/](http://localhost:9411/zipkin/)

## 4. [Department Service](https://github.com/code-with-rj1399/microservice-with-sb-department-service)
- **Port:** `8081`
- Registers with **[Eureka Service Registry](https://github.com/code-with-rj1399/microservice-with-sb-service-registry)**.
- **URL:** [http://localhost:8081](http://localhost:8081)
- **Exposed APIs:**
    - Add department: `POST /departments`
    - Get all departments: `GET /departments`
    - Get department by ID: `GET /departments/{id}`
    - Get all departments with employees: `GET /departments/with-employees`

## 5. [Employee Service](https://github.com/code-with-rj1399/microservice-with-sb-employee-service)
- **Port:** `8082`
- Registers with **[Eureka Service Registry](https://github.com/code-with-rj1399/microservice-with-sb-service-registry)**.
- **URL:** [http://localhost:8082](http://localhost:8082)
- **Exposed APIs:**
    - Add employee: `POST /employee`
    - Get all employees: `GET /employee`
    - Get employee by ID: `GET /employee/{id}`

## 6. [Service Registry (Eureka)](https://github.com/code-with-rj1399/microservice-with-sb-service-registry)
- **Port:** `8761`
- Centralized service registry for managing service discovery.
- **URL:** [http://localhost:8761](http://localhost:8761)

## How to Start the Microservices
Follow these steps to start the services in the correct order:

1. **Start [Eureka Service Registry](https://github.com/code-with-rj1399/microservice-with-sb-service-registry)**
    - Clone the repository.
    - Open the project in your IDE, navigate to the `Application` class, and run it.
    - Access it at: [http://localhost:8761](http://localhost:8761)

2. **Start Zipkin for Distributed Tracing**
   ```sh
   docker run -d -p 9411:9411 openzipkin/zipkin
   ```
    - Access it at: [http://localhost:9411/zipkin/](http://localhost:9411/zipkin/)

3. **Start [Config Server](https://github.com/code-with-rj1399/microservice-with-sb-config-server)**
    - Clone the repository.
    - Open the project in your IDE, navigate to the `Application` class, and run it.
    - Access it at: [http://localhost:8088](http://localhost:8088)

4. **Start [Department Service](https://github.com/code-with-rj1399/microservice-with-sb-department-service)**
    - Clone the repository.
    - Open the project in your IDE, navigate to the `Application` class, and run it.
    - Access it at: [http://localhost:8081](http://localhost:8081)

5. **Start [Employee Service](https://github.com/code-with-rj1399/microservice-with-sb-employee-service)**
    - Clone the repository.
    - Open the project in your IDE, navigate to the `Application` class, and run it.
    - Access it at: [http://localhost:8082](http://localhost:8082)

6. **Start [API Gateway](https://github.com/code-with-rj1399/microservice-with-sb-api-gateway)**
    - Clone the repository.
    - Open the project in your IDE, navigate to the `Application` class, and run it.
    - Access it at: [http://localhost:8083](http://localhost:8083)

Now all services should be up and running!

