# Java Microservices Portfolio

This portfolio demonstrates a simple **Java microservices architecture** built with Spring Boot, Spring Cloud, and Docker.  
The project currently includes:

- **User Service** – Handles user management (CRUD).  
- **Auth Service** – Handles authentication and token management (JWT).  
- **API Gateway** – Single entry point for all requests.  
- **Discovery Service** – Service discovery and registry.  
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

Docker Setup & Service Management Guide

Environment

- Docker Engine: v29.1.3
- Docker Desktop: v4.57.0

Make sure Docker Engine is running before executing any commands.

If Running Services Individually

- Run auth-service

      docker compose build --no-cache auth-service
      docker compose up --build auth-service
      
- Run user-service

      docker compose build --no-cache user-service
      docker compose up --build user-service

- Run api-gateway-service

      docker compose build --no-cache api-gateway
      docker compose up --build api-gateway
   

If Running All Services at Once

      docker compose up --build

Updating a Specific Service (After Code or Dependency Changes)
If you have updated the code or dependencies for a specific service:

      docker compose stop {service_name}
      docker compose build {service_name}
      docker compose up {service_name}
      
Example

      docker compose stop auth-service
      docker compose build auth-service
      docker compose up auth-service


Fixing Corrupted Data in a Specific Service
If a service encounters corrupted data:

      docker compose stop {service_name}
      docker compose rm -f {service_name}
      
Then rebuild and run it again:

      docker compose build {service_name}
      docker compose up {service_name}


Rebuilding All Services (Full Reset)

If multiple services are corrupted or you need a full clean rebuild:

      docker compose down -v
      docker compose build --no-cache
      docker compose up


