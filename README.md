# QuizCraft

This project is a microservices-based quiz application comprising four main components: Quiz Service, Question Service, API Gateway, and Service Registry. The architecture leverages various Spring Boot technologies to build a scalable, maintainable, and flexible system.

## Overview

The application consists of the following microservices:

1. **Quiz Service**: Manages quizzes, including creating, updating, retrieving, and deleting quizzes.
   - Repository link: https://github.com/shakib522/QuizService
2. **Question Service**: Handles the management of questions related to quizzes, including CRUD operations on questions.Calculate Score.
   - Repository link: https://github.com/shakib522/Question-Service
3. **API Gateway**: Serves as the single entry point for all client requests, routing them to the appropriate microservices.
   - Repository link: https://github.com/shakib522/Api-Getway
4. **Service Registry (Eureka Server)**: Acts as a service discovery mechanism, allowing microservices to register themselves and discover other services within the system.
   - Repository link: https://github.com/shakib522/Service-Registry


## Postman API Collection
[Quiz Craft.postman_collection.json](https://github.com/user-attachments/files/16823586/Quiz.Craft.postman_collection.json)

## Technologies Used

- **Spring Boot**: Provides a robust framework for building microservices.
- **Eureka Server (Service Registry)**: Facilitates service discovery and registration for microservices.
- **API Gateway (Spring Cloud Gateway)**: Manages routing, load balancing, and security for API requests.
- **OpenFeign**: Simplifies inter-service communication with declarative REST clients.
- **Spring Data JPA**: Streamlines database interactions using JPA with Spring.
- **PostgreSQL**: A relational database used for storing data in both Quiz and Question services.

## Prerequisites

- Java 17 or later
- Maven 3.6 or later
- PostgreSQL 13 or later
- Docker (optional, for containerization)

## Microservices Architecture

### 1. Quiz Service

- **Responsibilities**: Manages quizzes.
- **Technologies**: Spring Boot, Spring Data JPA, OpenFeign, Eureka Client, PostgreSQL.
- **API Endpoints**:
  - `GET /api/quizzes`: Retrieve all quizzes.
  - `POST /api/quizzes`: Create a new quiz.
  - And other CRUD operations.

### 2. Question Service

- **Responsibilities**: Manages questions for quizzes.
- **Technologies**: Spring Boot, Spring Data JPA, OpenFeign, Eureka Client, PostgreSQL.
- **API Endpoints**:
  - `GET /api/questions`: Retrieve all questions.
  - `POST /api/questions`: Create a new question.
  - And other CRUD operations.

### 3. API Gateway

- **Responsibilities**: Routes requests to the appropriate microservices, provides load balancing, and serves as a single entry point.
- **Technologies**: Spring Cloud Gateway, Eureka Client.
- **Configuration**:
  - Routes are defined to forward requests to `quiz-service` and `question-service` based on URL patterns.

### 4. Service Registry (Eureka Server)

- **Responsibilities**: Service discovery and registration.
- **Technologies**: Spring Boot, Eureka Server.
- **Configuration**:
  - Manages service registrations and provides a dashboard to view the status of registered services.

## Getting Started

### Clone the Repositories

Clone the main repository and any additional service-specific repositories if they are separated:

```bash
git clone <main-repository-url>
cd quiz-application
```

### Running the Services

1. **Start the Eureka Server**:

   ```bash
   cd service-registry
   mvn spring-boot:run
   ```

2. **Start the Quiz Service**:

   ```bash
   cd quiz-service
   mvn spring-boot:run
   ```

3. **Start the Question Service**:

   ```bash
   cd question-service
   mvn spring-boot:run
   ```

4. **Start the API Gateway**:

   ```bash
   cd api-gateway
   mvn spring-boot:run
   ```

### Accessing the Application

- **Eureka Dashboard**: `http://localhost:8761/`
- **API Gateway**: Routes are accessible through the gateway, e.g., `http://localhost:<gateway-port>/api/quizzes` and `http://localhost:<gateway-port>/api/questions`.

## Docker Support

Each microservice can be containerized using Docker:

1. **Build Docker Images**:

   ```bash
   docker build -t service-registry ./service-registry
   docker build -t quiz-service ./quiz-service
   docker build -t question-service ./question-service
   docker build -t api-gateway ./api-gateway
   ```

2. **Run Docker Containers**:

   ```bash
   docker run -d -p 8761:8761 --name service-registry service-registry
   docker run -d -p 8081:8081 --name quiz-service quiz-service
   docker run -d -p 8082:8082 --name question-service question-service
   docker run -d -p 8080:8080 --name api-gateway api-gateway
   ```

Ensure that all services are correctly connected to the same network or accessible by each other in Docker.

## Troubleshooting

- **Service Discovery Issues**: Verify the services are correctly registered with the Eureka Server and check the Eureka Client configurations.
- **Database Connection Issues**: Ensure PostgreSQL is running, and the correct credentials are used in the configuration files.
- **Routing Errors**: Check API Gateway routes and ensure paths match the services registered with Eureka.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For any questions or issues, please contact shakib at shakibhasann522@gmail.com
```

This README template covers the whole project setup, including configurations and instructions for running all microservices. Customize it further as needed to suit your project’s specifics!
