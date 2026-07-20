# 🛒 E-Commerce Microservices Project

This repository contains a Spring Boot-based e-commerce microservices sample used for learning and experimentation. It demonstrates common microservices patterns: service discovery, centralized configuration, API gateway, authentication, and inter-service communication.

## Repository Structure

- `service-registry/` — Eureka service registry
- `config-server/` — Spring Cloud Config Server + config files
- `api-gateway/` — API Gateway (routing + filters)
- `auth-service/` — Authentication (JWT) and user management
- `product-service/` — Product catalog API
- `order-service/` — Order processing service
- `payment-service/` — Payment integration (simulation)
- `notification-service/` — Notifications (email / push simulation)

## Key Features

- Service Discovery with Eureka
- Centralized configuration with Spring Cloud Config
- API Gateway for routing and cross-cutting concerns
- JWT-based authentication and authorization
- Modular service design for independent development

## Prerequisites

- Java 17 or newer installed
- Maven 3.6+ (or the Maven wrapper if provided)
- (Optional) Docker & Docker Compose for containerized runs

## Build (all modules)

From the repository root run:

```bash
mvn -T 1C clean package
```

This produces executable jars under each service's `target/` directory.

## Run services (development)

Recommended order to start services locally:

1. Service Registry (Eureka)
	- `cd service-registry && mvn spring-boot:run`
2. Config Server
	- `cd config-server && mvn spring-boot:run`
3. API Gateway
	- `cd api-gateway && mvn spring-boot:run`
4. Auth Service
	- `cd auth-service && mvn spring-boot:run`
5. Domain services (product, order, payment, notification)
	- `cd product-service && mvn spring-boot:run`
	- `cd order-service && mvn spring-boot:run`
	- `cd payment-service && mvn spring-boot:run`
	- `cd notification-service && mvn spring-boot:run`

Alternatively, run the built jars:

```bash
# example
java -jar service-registry/target/service-registry-1.0.0.jar
java -jar config-server/target/config-server-1.0.0.jar
```

Note: Service names and artifact versions may differ; adapt the jar names from each `target/` folder.

## Default Ports (check each service's `application.yml` for overrides)

- Service Registry: 8761
- Config Server: 8888
- API Gateway: 8080
- Auth Service: 8081
- Product Service: 8082
- Order Service: 8083
- Payment Service: 8084
- Notification Service: 8085

## Configuration

- Centralized configuration is stored under `config-server/config-files/` (e.g. `auth-service.yml`).
- Each service fetches its configuration from the config server at startup. To change settings, edit the appropriate file and restart the affected service.

## Docker (optional)

You can containerize services with Docker. A `docker-compose.yml` is not included by default — you can create one mapping each service to its jar and expose ports listed above.

## Testing

- Unit tests: `mvn test` inside each service module or run from the root to execute all modules.
- Integration tests: add service-specific integration tests as needed (Testcontainers recommended).

## Troubleshooting Tips

- If a service fails to fetch config, confirm the Config Server is running and reachable at port 8888.
- If a service fails to register, confirm the Service Registry is running and check service `application.yml` for correct `eureka.client.service-url`.

## Contribution

Contributions and experiments are welcome. Suggested workflow:

1. Create a feature branch off `main` (or `master`).
2. Implement and test changes in the relevant service folder.
3. Open a pull request with a summary and testing steps.

## Where to look next

- Service-specific configuration: `config-server/config-files/`
- Service entrypoints: check `src/main/java/...` under each module

---

Updated README to include overview, structure, build/run instructions, and troubleshooting. See each service's own README for module-specific details.

