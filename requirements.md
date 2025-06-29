# 📑 Requirement Specifications – Airbnb Clone Backend

This document outlines the technical and functional requirements for core backend features of the Airbnb Clone project.

---

## 🔐 1. User Authentication

### Functional Requirements:
- Users must be able to **register** using email and password.
- Registration must support roles: **guest** and **host**.
- Users must be able to **log in** securely.
- Enable **OAuth login** with Google and Facebook.
- Return a **JWT access token** upon login/registration.
- Users can **update their profile** (name, photo, phone, preferences).

### Technical Requirements:
- Use **bcrypt** for password hashing.
- Authenticate users via **JWT tokens** (access and refresh).
- Protect routes using JWT middleware.
- Implement **role-based access control**.
- Integrate **OAuth 2.0** providers (e.g., Passport.js).
- Use **input validation** libraries (e.g., Joi or express-validator).

---

## 🏠 2. Property Management System

### Functional Requirements:
- Hosts can:
  - Create property listings with title, description, price, location, photos, amenities.
  - Edit or delete their own listings.
- Guests can:
  - View and browse listings.
  - Filter properties by location, price, guest count, and amenities.

### Technical Requirements:
- Use **PostgreSQL** for data storage with normalized tables.
- Store property images:
  - Locally for development.
  - Via **AWS S3** or **Cloudinary** in production.
- Implement **pagination** on property listings.
- Restrict listing modifications to **owners only**.

---

## 📅 3. Booking System

### Functional Requirements:
- Guests can:
  - Book a property for specific dates.
  - Cancel bookings as per policy.
  - View their booking history.
- Hosts can:
  - View booking requests for their listings.
  - Confirm or cancel requests.
- Prevent **double bookings** for overlapping dates.

### Technical Requirements:
- Check for **date conflicts** before booking (SQL logic).
- Track **booking status**: `pending`, `confirmed`, `cancelled`, `completed`.
- Use **foreign key relationships** to link users, properties, and bookings.
- Validate booking dates:
  - Start date must precede end date.
  - No overlapping with existing bookings.
- Use **CRON jobs** or background workers to:
  - Auto-complete expired bookings.
  - Send email or in-app reminders.

---

## ✅ Summary

| Feature               | Functional Highlights                           | Technical Stack                        |
|----------------------|--------------------------------------------------|----------------------------------------|
| User Authentication  | Register, login, profile, JWT, OAuth            | JWT, bcrypt, OAuth2, Node.js/Django    |
| Property Management  | Create/edit/delete listings, search, pagination | PostgreSQL, AWS S3, RESTful API        |
| Booking System       | Validate dates, manage booking lifecycle        | SQL constraints, CRON, Transactions    |

---