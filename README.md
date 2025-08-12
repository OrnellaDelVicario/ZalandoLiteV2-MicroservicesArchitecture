# 📦 ZalandoLite+ v2: Backend Microservices E-commerce Platform

## 🚀 Executive Summary

ZalandoLite+ v2 constitutes a comprehensive backend microservices system, meticulously engineered to emulate a contemporary e-commerce platform specializing in fashion retail. This initiative is exclusively dedicated to the development of **RESTful APIs** and the management of **inter-service communication**, deliberately excluding a user interface component. The architectural design prioritizes **robustness, modularity, and security**, integrating Google OAuth2 for authentication purposes and leveraging Docker for efficient containerization.

This endeavor represents a collaborative project wherein each microservice operates as an autonomous entity, facilitating secure communication within a shared Docker network environment.

---

## ⚙️ Technical Specifications

### **Microservices Architecture**

The foundational design of this project adheres to the microservices paradigm, wherein discrete business capabilities are encapsulated within small, independently deployable services. This architectural choice significantly enhances **modularity, scalability, and system resilience**. Inter-service communication is predominantly conducted via **RESTful APIs**, routed through a dedicated network infrastructure.

### **Security Framework (Google OAuth2 & JWTs)**

* **Authentication**: User authentication is managed externally through **Google OAuth2**, a process orchestrated by the dedicated `Auth Service`.

* **Authorization**: Subsequent to successful Google authentication, the `Auth Service` is responsible for issuing **JSON Web Tokens (JWTs)**. These tokens serve as the mechanism for secure, stateless authorization across all integrated microservices.

* **Internal Token Flow**: A critical design decision dictates that JWTs are **not exposed to client-side environments or web browsers**. Instead, internal microservices retrieve user-specific JWTs via a designated internal endpoint on the `Auth Service` (`/internal/token`). Consequently, all subsequent inter-service calls necessitating user context **are mandated to forward these JWTs** within the `Authorization: Bearer <token>` HTTP header.

* **Resource Servers**: Each microservice configured to receive authenticated requests functions as a **Resource Server**. This role entails the validation of incoming JWTs utilizing shared cryptographic secrets, thereby ensuring the legitimacy and integrity of all processed requests.

### **Containerization & Orchestration**

* **Docker**: Every microservice is individually **containerized** utilizing Docker technology. This approach guarantees consistent operational environments across diverse development and deployment stages.

* **Docker Compose**: This utility is employed to **orchestrate** the multi-container application, streamlining the setup, inter-service linking, and execution procedures for the entire system.

* **Shared Network**: Inter-service communication is facilitated within a dedicated Docker network, explicitly named `zalando-backend`. This network is provisioned via the command `docker network create zalando-backend`.

---

## 📂 Project Structure

The project's organizational schema adopts a modular layout, with each distinct microservice residing within its own dedicated subdirectory.# ZalandoLiteV2-MicroservicesArchitecture

ZalandoLiteV2/
├── auth-service/
├── product-service/
├── inventory-service/
├── customer-service/
├── order-service/
├── discount-service/
├── review-service/
└── README.md

---

## 🔗 Repository Information

Each microservice component is independently maintained within its own dedicated GitHub repository.

* **Auth Service**: [https://github.com/OrnellaDelVicario/zalando-lite-v2-auth-service](https://github.com/OrnellaDelVicario/zalando-lite-v2-auth-service)
* **Product Service**: [https://github.com/OrnellaDelVicario/zalando-lite-v2-product-service](https://github.com/OrnellaDelVicario/zalando-lite-v2-product-service)
* **Inventory Service**: [https://github.com/OrnellaDelVicario/zalando-lite-v2-inventory-service](https://github.com/OrnellaDelVicario/zalando-lite-v2-inventory-service)
* **Customer Service**: [https://github.com/OrnellaDelVicario/zalando-lite-v2-customer-service](https://github.com/OrnellaDelVicario/zalando-lite-v2-customer-service)
* **Order Service**: [Link to Order Service Repo - Placeholder]
* **Discount Service**: [Link to Discount Service Repo - Placeholder]
* **Review Service**: [Link to Review Service Repo - Placeholder]





