# Java Microservices Portfolio

This portfolio demonstrates a simple **Java microservices architecture** built with Spring Boot, Spring Cloud, and Docker.  
The project currently includes:

- **User Service** – Handles user management (CRUD).  
- **Auth Service** – Handles authentication and token management (JWT).  
- **API Gateway** – Single entry point for all requests.  
- **Eureka Server** – Service discovery and registry.  
- **Docker** – Containerized services for easy deployment.

---

## Architecture Overview
Client/Postman
      |
      v
  API Gateway
   /      \
  v        v
User     Auth
 Service Service
   \      /
      v
    Eureka


---

## How It Works

1. **Client / Postman**
   - Sends HTTP requests to the API Gateway.
   - Gateway routes requests to appropriate microservices.

2. **API Gateway**
   - Serves as the single entry point.  
   - Supports routing, logging, and authentication.

3. **Microservices**
   - `User-Service`: CRUD operations for users.  
   - `Auth-Service`: User login, JWT token generation and validation.

4. **Eureka Server**
   - Acts as the service registry.  
   - Services register themselves at startup and can be discovered by other services.

5. **Docker**
   - Each service is containerized.  
   - Use `docker-compose up` to launch the full stack locally.

---

## Running the Project

```bash
# 1. Build Docker images
docker-compose build

# 2. Start all services
docker-compose up

# 3. Access API via
http://localhost:8080
