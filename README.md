# Microservices Architecture

This application consists of four services.

## 1. API Gateway
- **Port:** `8083`
- Acts as the entry point for handling and routing requests to the **[Department Service](https://github.com/code-with-rj1399/microservice-with-sb-department-service)** and **[Employee Service](https://github.com/code-with-rj1399/microservice-with-sb-employee-service)**.
- **URL:** [http://localhost:8083](http://localhost:8083)
- **Repository:** [API Gateway Repo](https://github.com/code-with-rj1399/microservice-with-sb-api-gateway)

## 2. Config Server
- **Port:** `8088`
- Centralized configuration service for managing settings of all microservices.
- Services pull their configuration from this server on startup.
- **URL:** [http://localhost:8088](http://localhost:8088)
- **Repository:** [Config Server Repo](https://github.com/code-with-rj1399/microservice-with-sb-config-server)

## 3. Zipkin - Distributed Tracing Service
- **Port:** `9411`
- Used for aggregating logs and tracing requests across microservices.
- **To start Zipkin:**
  ```sh
  docker run -d -p 9411:9411 openzipkin/zipkin
  ```
    - Access it at: [http://localhost:9411/zipkin/](http://localhost:9411/zipkin/)

## 4. Department Service
- **Port:** `8081`
- Registers with **[Eureka Service Registry](https://github.com/code-with-rj1399/microservice-with-sb-service-registry)**.
- **URL:** [http://localhost:8081](http://localhost:8081)
- **Exposed APIs:**
    - Add department: `POST /departments`
    - Get all departments: `GET /departments`
    - Get department by ID: `GET /departments/{id}`
    - Get all departments with employees: `GET /departments/with-employees`
- **Repository:** [Department Service Repo](https://github.com/code-with-rj1399/microservice-with-sb-department-service)

## 5. Employee Service
- **Port:** `8082`
- Registers with **[Eureka Service Registry](https://github.com/code-with-rj1399/microservice-with-sb-service-registry)**.
- **URL:** [http://localhost:8082](http://localhost:8082)
- **Exposed APIs:**
    - Add employee: `POST /employee`
    - Get all employees: `GET /employee`
    - Get employee by ID: `GET /employee/{id}`
- **Repository:** [Employee Service Repo](https://github.com/code-with-rj1399/microservice-with-sb-employee-service)

## 6. Service Registry (Eureka)
- **Port:** `8761`
- Centralized service registry for managing service discovery.
- **URL:** [http://localhost:8761](http://localhost:8761)
- **Repository:** [Service Registry Repo](https://github.com/code-with-rj1399/microservice-with-sb-service-registry)

## How to Start the Microservices
Follow these steps to start the services in the correct order:

1. **Start Eureka Service Registry**
    - Clone the repository: [Service Registry Repo](https://github.com/code-with-rj1399/microservice-with-sb-service-registry)
    - Open the project in your IDE, navigate to the `Application` class, and run it.
    - Access it at: [http://localhost:8761](http://localhost:8761)

2. **Start Zipkin for Distributed Tracing**
   ```sh
   docker run -d -p 9411:9411 openzipkin/zipkin
   ```
    - Access it at: [http://localhost:9411/zipkin/](http://localhost:9411/zipkin/)

3. **Start Config Server**
    - Clone the repository: [Config Server Repo](https://github.com/code-with-rj1399/microservice-with-sb-config-server)
    - Open the project in your IDE, navigate to the `Application` class, and run it.
    - Access it at: [http://localhost:8088](http://localhost:8088)

4. **Start Department Service**
    - Clone the repository: [Department Service Repo](https://github.com/code-with-rj1399/microservice-with-sb-department-service)
    - Open the project in your IDE, navigate to the `Application` class, and run it.
    - Access it at: [http://localhost:8081](http://localhost:8081)

5. **Start Employee Service**
    - Clone the repository: [Employee Service Repo](https://github.com/code-with-rj1399/microservice-with-sb-employee-service)
    - Open the project in your IDE, navigate to the `Application` class, and run it.
    - Access it at: [http://localhost:8082](http://localhost:8082)

6. **Start API Gateway**
    - Clone the repository: [API Gateway Repo](https://github.com/code-with-rj1399/microservice-with-sb-api-gateway)
    - Open the project in your IDE, navigate to the `Application` class, and run it.
    - Access it at: [http://localhost:8083](http://localhost:8083)

Now all services should be up and running!
