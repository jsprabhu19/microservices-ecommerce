# 🛒 E-Commerce Microservices Project

A learning project to build scalable microservices using Spring Boot 3.x.

## 🏗️ Architecture

- **Service Registry** (Eureka) - Port 8761 ✅
- **Config Server** - Port 8888 ✅
- **API Gateway** - Port 8080
- **Auth Service** - Port 8081
- **Product Service** - Port 8082
- **Order Service** - Port 8083
- **Payment Service** - Port 8084
- **Notification Service** - Port 8085

## 🛠️ Tech Stack

- Java 17/25
- Spring Boot 3.3.5
- Spring Cloud 2023.0.3
- MySQL
- Maven
- Eureka, Config Server, API Gateway
- Kafka/RabbitMQ (coming soon)
- Docker (coming soon)

## 📅 Progress

- [x] **Day 1:** Service Registry + Config Server ✅
- [ ] **Day 2:** API Gateway + Auth Service Skeleton
- [ ] **Day 3-4:** Auth Service - JWT Implementation
- [ ] **Day 5-7:** Product Service
- [ ] ... and more

## 🚀 How to Run

1. Start Service Registry: `cd service-registry && mvn spring-boot:run`
2. Start Config Server: `cd config-server && mvn spring-boot:run`
3. Start other services similarly

## 📁 Project Structure

microservices-ecommerce/ ├── service-registry/ (Eureka Server) ├── config-server/ (Centralized Config) ├── api-gateway/ (Single Entry Point) ├── auth-service/ (Authentication & JWT) ├── product-service/ (Product Management) ├── order-service/ (Order Processing) ├── payment-service/ (Payment Handling) └── notification-service/ (Async Notifications)