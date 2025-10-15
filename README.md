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

