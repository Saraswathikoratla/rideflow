# rideflow
RideFlow is a backend ride-booking application inspired by Uber.
# RideFlow

**Production-Ready Ride Booking Backend using Spring Boot Microservices**

RideFlow is a backend-focused ride-booking platform inspired by real-world systems such as Uber and Ola. The project is designed to demonstrate production-grade backend architecture, microservices communication, security, scalability, caching, asynchronous messaging, and real-time event processing.

The primary goal of this project is to showcase backend engineering skills by implementing industry-standard design patterns, distributed system concepts, and clean architecture using the Spring ecosystem.

---

## Architecture

```
                        +----------------+
                        |   API Gateway  |
                        +-------+--------+
                                |
        -------------------------------------------------
        |           |             |           |          |
        |           |             |           |          |
+---------------+ +-------------+ +-----------+ +---------------+
| Auth Service  | | Rider       | | Driver    | | Ride Service  |
|               | | Service     | | Service   | |               |
+---------------+ +-------------+ +-----------+ +---------------+
        |               |              |                |
        -------------------------------------------------
                                |
                         Kafka Event Bus
                                |
                   +---------------------------+
                   | Notification Service      |
                   +---------------------------+

                 Redis
          (Driver Live Location)

                PostgreSQL
        (Application Persistent Data)
```

---

## Technology Stack

| Category                | Technology              |
| ----------------------- | ----------------------- |
| Language                | Java 21                 |
| Framework               | Spring Boot 3           |
| Security                | Spring Security, JWT    |
| Database                | PostgreSQL              |
| Cache                   | Redis                   |
| Messaging               | Apache Kafka            |
| API Documentation       | Swagger / OpenAPI       |
| Real-time Communication | WebSocket               |
| Containerization        | Docker & Docker Compose |
| Build Tool              | Maven                   |
| Testing                 | JUnit 5, Mockito        |
| Version Control         | Git & GitHub            |

---

# Features

## Authentication Service

* User Registration
* Secure Login
* JWT Authentication
* Access Token
* Refresh Token
* Role-Based Authorization
* Password Encryption using BCrypt

---

## Rider Service

* Rider Profile Management
* Ride History
* Ride Booking
* Ride Cancellation

---

## Driver Service

* Driver Registration
* Vehicle Management
* Driver Availability
* Live Driver Location
* Online / Offline Status

---

## Ride Service

Ride Lifecycle Management

```
REQUESTED
      │
      ▼
DRIVER_ASSIGNED
      │
      ▼
ACCEPTED
      │
      ▼
STARTED
      │
      ▼
COMPLETED
```

Supported operations

* Request Ride
* Assign Driver
* Accept Ride
* Start Ride
* Complete Ride
* Cancel Ride

---

## Redis Integration

Redis is used for storing driver's live location instead of continuously updating the relational database.

Benefits

* Faster reads
* Lower database load
* Better scalability
* Suitable for high-frequency location updates

---

## Kafka Event-Driven Communication

RideFlow uses Apache Kafka for asynchronous communication between services.

Published Events

* Ride Requested
* Driver Assigned
* Ride Accepted
* Ride Started
* Ride Completed
* Ride Cancelled

Consumers

* Notification Service
* Analytics (Future)
* Audit Service (Future)

This reduces service coupling and improves scalability.

---

## WebSocket Support

Real-time updates without client polling.

Examples

* Driver Accepted Ride
* Driver Current Location
* Ride Started
* Ride Completed

---

## Payment Module

Mock payment implementation supporting

* UPI
* Credit/Debit Card
* Wallet

The payment module is intentionally designed to be gateway-independent and can later integrate providers such as Razorpay or Stripe.

---

## Admin APIs

Administrative endpoints include

* Total Riders
* Total Drivers
* Active Rides
* Completed Rides
* Cancelled Rides
* Revenue Statistics

---

## Monitoring

Application monitoring using Spring Boot Actuator

* Health Endpoint
* Metrics
* Liveness Probe
* Readiness Probe

---

## API Documentation

Interactive REST API documentation using Swagger OpenAPI.

---

## Testing

* Unit Testing using JUnit 5
* Mocking using Mockito
* Service Layer Testing
* Controller Testing

---

## Docker Support

Run the complete application locally using Docker Compose.

```bash
docker compose up --build
```

---

# Project Roadmap

### Phase 1

* Authentication
* JWT
* Refresh Tokens
* Role-Based Authorization

### Phase 2

* Rider Service
* Driver Service
* Vehicle Management

### Phase 3

* Ride Booking Workflow

### Phase 4

* Redis Integration

### Phase 5

* Kafka Event Streaming

### Phase 6

* WebSocket Notifications

### Phase 7

* Payment Module

### Phase 8

* Admin Dashboard APIs

### Phase 9

* Monitoring & Health Checks

### Phase 10

* Docker Deployment

---

# Project Structure

```
rideflow
│
├── api-gateway
├── auth-service
├── rider-service
├── driver-service
├── ride-service
├── notification-service
├── common-library
├── docker-compose.yml
└── README.md
```

---

# Engineering Practices

* Clean Architecture
* Layered Design
* SOLID Principles
* DTO Pattern
* Global Exception Handling
* Centralized Configuration
* API Versioning
* Environment-based Configuration
* Meaningful Logging
* Event-Driven Communication
* RESTful API Design

---

# Future Enhancements

* Google Maps Integration
* Driver Matching Algorithm
* ETA Calculation
* Surge Pricing
* Ride Scheduling
* Multi-region Deployment
* Kubernetes Deployment
* CI/CD Pipeline using GitHub Actions
* Distributed Tracing
* Prometheus & Grafana Monitoring

---

# Learning Objectives

This project focuses on building production-oriented backend systems by applying scalable architecture, secure authentication, asynchronous messaging, distributed caching, and real-time communication using the Spring ecosystem.

---

## License

This project is created for learning, portfolio, and backend engineering demonstration purposes.
