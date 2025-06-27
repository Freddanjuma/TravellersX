# 📌 TravellersXperience.com — Requirements Specification

## 📖 Overview

TravellersXperience.com is a web platform that connects travelers to  HOTELS/TRANSPORT SERVICES and budget-friendly experiences.
This document outlines the technical and functional specifications of the platform, including API design, data validation, and performance expectations.



## 1. 👤 User Management

### Functional Requirements
- Register, login, and manage user profiles
- Support for both Travelers and Guesthouse Owners

### API Endpoints
- `POST /api/users/register`
- `POST /api/users/login`
- `GET /api/users/profile`
- `PUT /api/users/profile`
- `POST /api/users/reset-password`

### Validation Rules
- `email`: Valid, unique
- `password`: Min 8 characters
- `role`: `traveler` or `owner`

### Performance
- Response time < 300ms
- Token-based authentication (JWT)

---

## 2. 🏘️ Accommodation Listings

### Functional Requirements
- Owners can manage listings
- Travelers can search/filter listings

### API Endpoints
- `POST /api/listings`
- `GET /api/listings`
- `GET /api/listings/:id`
- `PUT /api/listings/:id`
- `DELETE /api/listings/:id`

### Validation
- `name`, `location`, `price`, `availability`, `images`
- Foreign Key: `owner_id` → Users

### Performance
- Pagination (20 per page)
- Image CDN support

---

## 3. 📅 Booking System

### Functional Requirements
- Booking requests and approvals
- Calendar-based availability tracking

### API Endpoints
- `POST /api/bookings`
- `GET /api/bookings/user/:id`
- `PUT /api/bookings/:id`
- `DELETE /api/bookings/:id`

### Validation
- Dates: future only, non-overlapping
- `status`: pending, approved, cancelled

---

## 4. 💳 Payment Integration

### Functional Requirements
- Online payments for bookings
- Admin-level revenue tracking

### API Endpoints
- `POST /api/payments/initiate`
- `POST /api/payments/webhook`
- `GET /api/payments/user/:id`
- `GET /api/payments/admin/summary`

### Validation
- `amount`, `booking_id`, `currency`
- Secure via Stripe or Paystack

---

## 5. ⭐ Reviews & Ratings

### Functional Requirements
- Travelers review guesthouses
- Display average ratings

### API Endpoints
- `POST /api/reviews`
- `GET /api/reviews/listing/:id`
- `DELETE /api/reviews/:id`

### Validation
- One review per completed booking
- Ratings: 1–5 stars, max 500 characters

---

## 6. 🔍 Search & Filter System

### Functional Requirements
- Dynamic search by location, date, price, etc.

### API Endpoint
- `GET /api/search?location=...&priceMin=...`

### Performance
- ElasticSearch or optimized queries
- Response < 400ms

---

## 7. 📊 Admin Dashboard

### Functional Requirements
- View metrics, users, and reports
- Moderate content and issues

### API Endpoints
- `GET /api/admin/stats`
- `GET /api/admin/users`
- `GET /api/admin/reports`

---

## 🔐 Security & Performance Standards

- HTTPS enforced
- Input validation and sanitation
- Bcrypt for password hashing
- JWT auth with expiration and refresh
- Error logging, throttling & API rate limits

---

## 📈 Schema Design & Normalization

- ER Diagram used for schema planning
- Database normalized to 3NF
- Each table uses foreign key constraints

---

## 🔄 Development Notes

- Built as part of ALX Software Engineering Program
- Backend: Node.js / Django REST (TBD)
- Database: PostgreSQL / MySQL (TBD)
- Deployment: Heroku, Vercel, or Netlify for frontend

---

## 📧 Contact

Fred Danjuma  
**Email:** freddanjuma247@gmail.com  
**GitHub:** [TravellersXperience Repo](https://github.com/Freddanjuma/TravellersXperience.com)  
**LinkedIn:** [Fred Danjuma](https://www.linkedin.com/in/fred-danjuma-b9180a366)
