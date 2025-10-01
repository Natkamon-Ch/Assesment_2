# API Testing Documentation

## 7. API Testing

### 7.1 Overview
This document provides comprehensive API testing information for the Therapy Management System backend. The system includes multiple API endpoints for authentication, therapist management, appointment booking, and slot management.

### 7.2 API Request Collections and Response for Backend Code

#### Available API Collections:

1. **Authentication API** - User registration, login, and profile management
2. **Therapist API** - Therapist profiles, search, and availability management
3. **Booking API** - Appointment booking, viewing, and cancellation
4. **Slots API** - Time slot management and availability

#### Base URL
- **Local Development**: `http://localhost:3000`
- **Production**: `https://your-production-domain.com`

#### Authentication
Most endpoints require JWT token authentication via Bearer token in the Authorization header:
```
Authorization: Bearer <your-jwt-token>
```

### 7.3 API Endpoints Summary

#### Authentication Endpoints (`/api/auth`)
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/auth/register` | Register new user | No |
| POST | `/api/auth/login` | User login | No |
| GET | `/api/auth/profile` | Get user profile | Yes |
| PUT | `/api/auth/profile` | Update user profile | Yes |

#### Therapist Endpoints (`/api/therapists`)
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/therapists` | Get all therapists | No |
| GET | `/api/therapists/search` | Search therapists | No |
| GET | `/api/therapists/:id` | Get therapist profile | No |
| GET | `/api/therapists/:id/slots` | Get therapist slots | No |
| GET | `/api/therapists/me/profile` | Get my therapist profile | Yes (Therapist) |
| PUT | `/api/therapists/me/profile` | Update therapist profile | Yes (Therapist) |
| PUT | `/api/therapists/me/availability` | Update availability | Yes (Therapist) |

#### Booking Endpoints (`/api/bookings`)
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/bookings` | Create new booking | Yes |
| GET | `/api/bookings/my` | Get user's bookings | Yes |
| DELETE | `/api/bookings/:id` | Cancel booking | Yes |

#### Slot Endpoints (`/api/slots`)
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/slots` | Get available slots | No |
| POST | `/api/slots` | Create new slot | Yes (Therapist) |
| GET | `/api/slots/:id` | Get specific slot | No |
| PUT | `/api/slots/:id` | Update slot | Yes (Therapist) |

### 7.4 Sample API Requests and Responses

#### 1. User Registration
**Request:**
```http
POST /api/auth/register
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john.doe@example.com",
  "password": "securePassword123",
  "role": "patient",
  "phone": "+1234567890",
  "dateOfBirth": "1990-05-15",
  "address": "123 Main St, City, Country"
}
```

**Response:**
```json
{
  "status": "success",
  "message": "User registered successfully",
  "data": {
    "user": {
      "id": "64f8b2c3e1b2a4d5e6f7g8h9",
      "name": "John Doe",
      "email": "john.doe@example.com",
      "role": "patient"
    },
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
  }
}
```

#### 2. Search Therapists
**Request:**
```http
GET /api/therapists/search?specialization=Anxiety&location=New York&availability=true
```

**Response:**
```json
{
  "status": "success",
  "data": [
    {
      "id": "64f8b2c3e1b2a4d5e6f7g8h1",
      "name": "Dr. Sarah Johnson",
      "specializations": ["Anxiety", "Depression", "PTSD"],
      "experience": 8,
      "rating": 4.8,
      "availability": true,
      "location": "New York, NY"
    }
  ]
}
```

#### 3. Create Booking
**Request:**
```http
POST /api/bookings
Authorization: Bearer <your-jwt-token>
Content-Type: application/json

{
  "therapistId": "64f8b2c3e1b2a4d5e6f7g8h1",
  "slotId": "64f8b2c3e1b2a4d5e6f7g8s1",
  "sessionType": "Individual",
  "notes": "First session - anxiety and stress management",
  "paymentMethod": "card"
}
```

**Response:**
```json
{
  "status": "success",
  "message": "Booking created successfully",
  "data": {
    "booking": {
      "id": "64f8b2c3e1b2a4d5e6f7g8b1",
      "patientId": "64f8b2c3e1b2a4d5e6f7g8h9",
      "therapistId": "64f8b2c3e1b2a4d5e6f7g8h1",
      "slotId": "64f8b2c3e1b2a4d5e6f7g8s1",
      "sessionType": "Individual",
      "status": "confirmed",
      "date": "2024-01-20",
      "startTime": "09:00",
      "endTime": "10:00",
      "amount": 150,
      "paymentStatus": "paid"
    },
    "confirmationNumber": "BK-20240115-001"
  }
}
```

### 7.5 Error Handling

The API uses standard HTTP status codes and returns consistent error responses:

#### Common Error Responses:

**400 Bad Request:**
```json
{
  "status": "error",
  "message": "Invalid input data",
  "errors": [
    {
      "field": "email",
      "message": "Email is required"
    }
  ]
}
```

**401 Unauthorized:**
```json
{
  "status": "error",
  "message": "Authentication required"
}
```

**403 Forbidden:**
```json
{
  "status": "error",
  "message": "Insufficient permissions"
}
```

**404 Not Found:**
```json
{
  "status": "error",
  "message": "Resource not found"
}
```

**500 Internal Server Error:**
```json
{
  "status": "error",
  "message": "Internal server error"
}
```

### 7.6 Testing Instructions

#### Prerequisites:
1. **Postman** installed on your machine
2. **Backend server** running locally on `http://localhost:3000`
3. **MongoDB** database connection established

#### Steps to Test:

1. **Import Collections:**
   - Download the Postman collection files from this repository
   - Open Postman and click "Import"
   - Select all `.json` files from the `/api-testing` folder
   - Import the environment file as well

2. **Set Environment:**
   - Select "Therapy Management System Environment" in Postman
   - Update the `baseUrl` variable if your server runs on a different port

3. **Authentication Flow:**
   - Start with user registration (`POST /api/auth/register`)
   - Copy the returned JWT token
   - Set the token in environment variables or individual requests

4. **Test Scenarios:**
   - **Patient Journey**: Register → Login → Search Therapists → View Slots → Create Booking
   - **Therapist Journey**: Register as Therapist → Login → Update Profile → Manage Slots → View Bookings

#### Test Data Examples:

**Patient Registration:**
```json
{
  "name": "Test Patient",
  "email": "patient@test.com",
  "password": "testPass123",
  "role": "patient",
  "phone": "+1234567890"
}
```

**Therapist Registration:**
```json
{
  "name": "Dr. Test Therapist",
  "email": "therapist@test.com",
  "password": "testPass123",
  "role": "therapist",
  "specializations": ["Anxiety", "Depression"],
  "experience": 5
}
```

### 7.7 Performance Testing

For load testing, consider using tools like:
- **Artillery.js** for load testing
- **Newman** (Postman CLI) for automated testing
- **Jest** for unit tests on API endpoints

### 7.8 Security Testing

Key security tests to perform:
- Authentication bypass attempts
- SQL injection testing
- XSS prevention validation
- Rate limiting verification
- Input validation testing

---

**Note**: Replace placeholder URLs and tokens with actual values when testing. Ensure your local development server is running before executing API tests.