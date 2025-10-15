# Airbnb Clone Project

The **Airbnb Clone Project** is a full-stack web application that simulates a real-world booking platform.  
It focuses on backend systems, databases, REST APIs, and security, while teaching essential skills like teamwork, scalability, and software architecture.

Proud to be part of this collaborative and impactful journey!

---

##  Team Roles

- **Backend Developer**: Implements API endpoints, database schemas, and business logic.
- **Database Administrator**: Designs and optimizes the database schema and manages performance.
- **DevOps Engineer**: Deploys the app, manages CI/CD pipelines, and monitors backend services.
- **QA Engineer**: Writes test cases and ensures the app meets functional and performance standards.

---

##  Technology Stack

- **Django**: High-level Python web framework for backend development.
- **Django REST Framework**: Toolkit for building Web APIs.
- **PostgreSQL**: Robust, scalable relational database.
- **GraphQL**: Flexible querying language for advanced data fetching.
- **Celery**: Asynchronous task queue for background jobs (e.g., notifications, payment processing).
- **Redis**: In-memory store used for caching and session management.
- **Docker**: For containerization and consistent environments across dev/staging/prod.
- **CI/CD Pipelines**: Automates testing and deployment for reliability and speed.

---

##  Database Design

### 1. **User**
Represents a person using the platform (host or guest).

**Important Fields:**
- `id` (unique identifier)
- `name`
- `email`
- `password` (hashed)
- `is_host` (boolean flag)

**Relationships:**
- A user can **own multiple properties**.
- A user can **make multiple bookings**.
- A user can **leave multiple reviews**.

---

### 2. **Property**
Represents a place listed by a host.

**Important Fields:**
- `id`
- `title`
- `description`
- `location`
- `price_per_night`
- `owner_id` (foreign key to User)

**Relationships:**
- A property **belongs to one user** (host).
- A property can have **many bookings**.
- A property can receive **multiple reviews**.

---

### 3. **Booking**
Represents a reservation made by a guest.

**Important Fields:**
- `id`
- `user_id` (guest who booked)
- `property_id`
- `start_date`
- `end_date`
- `status` (e.g., pending, confirmed, canceled)

**Relationships:**
- A booking **belongs to one user** and **one property**.
- A booking may be linked to **a payment**.

---

### 4. **Review**
Represents feedback left by a user.

**Important Fields:**
- `id`
- `user_id` (review author)
- `property_id`
- `rating` (1–5)
- `comment`

**Relationships:**
- A review is linked to **one user** and **one property**.
- A user can leave **one review per property per booking** (based on business rules).

---

### 5. **Payment**
Represents a transaction for a booking.

**Important Fields:**
- `id`
- `booking_id`
- `amount`
- `payment_method` (e.g., card, PayPal)
- `payment_status` (e.g., completed, failed)

**Relationships:**
- A payment is linked to **one booking**.

---

##  Feature Breakdown

Below are the core features implemented in the Airbnb Clone Project, each contributing to a seamless user experience and a scalable, production-ready backend system.

---

### 1.  API Documentation

The backend APIs are documented using the **OpenAPI standard**, providing clear, machine-readable documentation that facilitates integration and testing. Using **Django REST Framework** and **GraphQL**, the project supports both RESTful endpoints and flexible query-based data retrieval.

---

### 2.  User Authentication & Management

Users can register, log in, and manage their profiles via the `/users/` endpoints. Secure authentication mechanisms ensure that user data is protected, and role-based logic (host vs. guest) is enforced where necessary.

---

### 3.  Property Management

Hosts can create, update, view, and delete property listings through the `/properties/` endpoints. This feature enables dynamic and user-generated content on the platform, supporting multiple hosts and properties.

---

### 4.  Booking System

The booking system allows users to reserve available properties, manage their bookings, and view check-in/check-out information. Implemented via `/bookings/`, this feature supports a core function of the platform—connecting guests with hosts.

---

### 5.  Payment Processing

Through the `/payments/` endpoint, users can securely process payments related to their bookings. This feature is essential for transaction handling, and lays the groundwork for future integration with third-party payment gateways.

---

### 6.  Review System

The review system enables users to post and manage feedback for properties they've booked. Accessible via `/reviews/`, this encourages trust and transparency among users by showcasing real experiences.

---

### 7.  Database Optimizations

To ensure performance and scalability, the backend uses **indexing** for frequently queried fields and **caching** strategies (e.g., Redis) to reduce database load. These optimizations enhance response times and ensure smooth API performance even under load.

---

##  API Security

Security is a critical aspect of the Airbnb Clone Project to ensure the integrity, confidentiality, and availability of user data, property information, and financial transactions. Below are the key security measures implemented in the backend APIs:

---

### 1.  Authentication

**What it does:**  
Implements secure user login and token-based authentication (e.g., JWT) to verify the identity of users accessing the platform.

**Why it's important:**  
Prevents unauthorized access to user accounts, protects personal data, and ensures that only verified users can perform actions like booking properties or making payments.

---

### 2.  Authorization

**What it does:**  
Controls what authenticated users are allowed to do based on their roles (e.g., guest vs. host). Ensures users can only manage their own data.

**Why it's important:**  
Protects user integrity by preventing actions like editing another user's property, tampering with someone else's bookings, or accessing sensitive admin-level endpoints.

---

### 3.  Rate Limiting

**What it does:**  
Limits the number of API requests a user or IP address can make in a specific time frame.

**Why it's important:**  
Prevents abuse of APIs, protects against brute-force attacks (especially on login), and ensures fair use of system resources.

---

### 4.  Data Encryption

**What it does:**  
All sensitive data (e.g., passwords, payment info) is encrypted in transit using HTTPS, and passwords are stored as hashed values using secure algorithms like bcrypt or argon2.

**Why it's important:**  
Protects sensitive user information from being intercepted or compromised during transmission or storage.

---

### 5.  Input Validation & Sanitization

**What it does:**  
Validates and sanitizes all user inputs to prevent malicious code injection (e.g., SQL injection, XSS).

**Why it's important:**  
Prevents attackers from exploiting input fields to execute unauthorized commands or extract sensitive data from the database.

---

### 6.  Secure Payment Handling

**What it does:**  
Payment data is processed through secure backend logic, potentially integrated with third-party payment gateways for added compliance (e.g., PCI-DSS).

**Why it's important:**  
Ensures users' financial information is securely handled, builds user trust, and prevents fraud or payment manipulation.

---

Together, these security measures form a multi-layered defense strategy that keeps user data, financial transactions, and system integrity safe throughout the application lifecycle.

---

##  CI/CD Pipeline

### What is CI/CD?

**CI/CD** stands for **Continuous Integration** and **Continuous Deployment/Delivery**. It is a development practice that automates the process of integrating code changes, testing them, and deploying them to production environments. The goal is to ensure rapid and reliable delivery of software updates.

---

### Why CI/CD is Important

-  **Faster Development Cycles**: Automates testing and deployment, allowing for quicker releases.
-  **Improved Code Quality**: Automated testing catches bugs and issues early in the development process.
-  **Reduced Human Error**: Automating repetitive deployment tasks minimizes the chance of mistakes.
-  **Consistent Deployments**: Ensures every deployment follows the same steps, increasing stability.
-  **Team Collaboration**: Encourages better integration among team members by catching integration issues early.

---

### Tools Used

- **GitHub Actions**: Automates the CI/CD pipeline, including testing, building, and deploying the application on every code push or pull request.
- **Docker**: Provides a consistent containerized environment for development, testing, and production.
- **Docker Compose**: Manages multi-container setups (e.g., app, database, Redis) for local testing.
- **PostgreSQL**: Can be included in the pipeline as a service for integration testing.
- **Celery + Redis**: Used in testing asynchronous tasks as part of the CI process.
- **Coverage Tools (e.g., `coverage.py`)**: Measures test coverage and ensures critical parts of the codebase are tested.

---

With CI/CD in place, the Airbnb Clone Project can evolve faster, stay more stable, and deliver new features to users with confidence.
