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

### 1. 🧾 API Documentation

The backend APIs are documented using the **OpenAPI standard**, providing clear, machine-readable documentation that facilitates integration and testing. Using **Django REST Framework** and **GraphQL**, the project supports both RESTful endpoints and flexible query-based data retrieval.

---

### 2. 👤 User Authentication & Management

Users can register, log in, and manage their profiles via the `/users/` endpoints. Secure authentication mechanisms ensure that user data is protected, and role-based logic (host vs. guest) is enforced where necessary.

---

### 3. 🏡 Property Management

Hosts can create, update, view, and delete property listings through the `/properties/` endpoints. This feature enables dynamic and user-generated content on the platform, supporting multiple hosts and properties.

---

### 4. 📅 Booking System

The booking system allows users to reserve available properties, manage their bookings, and view check-in/check-out information. Implemented via `/bookings/`, this feature supports a core function of the platform—connecting guests with hosts.

---

### 5. 💳 Payment Processing

Through the `/payments/` endpoint, users can securely process payments related to their bookings. This feature is essential for transaction handling, and lays the groundwork for future integration with third-party payment gateways.

---

### 6. ⭐ Review System

The review system enables users to post and manage feedback for properties they've booked. Accessible via `/reviews/`, this encourages trust and transparency among users by showcasing real experiences.

---

### 7. ⚙️ Database Optimizations

To ensure performance and scalability, the backend uses **indexing** for frequently queried fields and **caching** strategies (e.g., Redis) to reduce database load. These optimizations enhance response times and ensure smooth API performance even under load.

---
