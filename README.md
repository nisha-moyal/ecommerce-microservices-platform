# 🛒 E-Commerce Microservices Platform

A production-grade e-commerce backend built with Spring Boot and Spring Cloud. Implemented as a set of loosely coupled microservices communicating via REST APIs and asynchronous Kafka events, with JWT-secured endpoints and dual payment gateway integration.

---

## 📦 Services

| Service | Responsibility | Repository |
|--------|----------------|------------|
| Product Catalog Service | Product CRUD (add, delete, replace), search, pagination & sorting | [Product Catalog Service](https://github.com/nisha-moyal/ecommerce-product-catalog-service) |
| User Service | User registration, login, JWT generation & validation, auth & authorization | [User Service](https://github.com/nisha-moyal/ecommerce-user-service) |
| Payment Service | Payment orchestration (Razorpay & Stripe, webhook reconciliation) | [Service Discovery](https://github.com/nisha-moyal/ecommerce-payment-service) |
| Notification Service | First-time sign-up welcome email via SMTP, triggered by Kafka events | [Notification Service](https://github.com/nisha-moyal/ecommerce-notification-service) |
| Service Discovery | Spring Cloud Netflix Eureka registry for inter-service communication | [Service Discovery](https://github.com/nisha-moyal/ecommerce-service-discovery) |

> 💡 Payment orchestration (Razorpay & Stripe, webhook reconciliation) is integrated within the platform's services.

---

## ✨ Highlights

- JWT-based authentication & authorization — protected endpoints validate tokens before writes  
- Event-driven notifications — Kafka async flow sends welcome emails on first sign-up  
- Service mesh — Eureka for discovery and client-side load balancing  
- RESTful APIs — product CRUD, search, sorting, paging; full user auth flow  
- Persistence — Spring Data JPA + Hibernate over MySQL  
- Cloud deployment — AWS (EBS, RDS) with Docker and CI/CD  

---

## 🧰 Tech Stack

Java · Spring Boot · Spring Cloud (Eureka) · Spring Data JPA · Hibernate · MySQL · Apache Kafka · JWT · Razorpay · Stripe · SMTP · Docker · Jenkins · AWS · Postman/Swagger

---

## 🏗️ Architecture

```mermaid
flowchart LR
    A[Client] --> B[API Gateway / Direct Call]
    B --> C[Product Catalog Service]
    B --> D[User Service]
    B --> E[Notification Service]
    D --> F[Kafka]
    F --> E
    C --> G[MySQL]
    D --> G
    E --> H[SMTP Server]
    C -- registers --> I[Eureka Server]
    D -- registers --> I
    E -- registers --> I
