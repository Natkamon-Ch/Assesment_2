Online Therapy Booking — Overview

This app helps patients find a therapist and book sessions online. It has secure login, profile management, and an easy booking flow. Patients can browse therapists, see available time slots, book or cancel, and view upcoming bookings. The app also checks inputs (for example, required fields, email format, and date/time).

Features

Sign up

Log in / Log out

Update profile (name, email, etc.)

Browse therapists (rate, specialties, languages)

View available slots for each therapist

Book a session

See “My Bookings”

Cancel a booking
(Optional: reschedule, reminders, payments)

## 🧪 API Testing

### 7.2 API Request Collections and Response for Backend Code

This repository includes comprehensive Postman collections for testing all backend API endpoints. The collections provide complete request/response examples with sample data.

#### 📋 Available Collections:

1. **[Authentication API Collection](./api-testing/Auth_API_Collection.postman_collection.json)**
   - User registration and login
   - Profile management
   - JWT token authentication

2. **[Therapist API Collection](./api-testing/Therapist_API_Collection.postman_collection.json)**
   - Therapist profile management  
   - Search and filtering
   - Availability management

3. **[Booking API Collection](./api-testing/Booking_API_Collection.postman_collection.json)**
   - Create and manage appointments
   - View booking history
   - Cancellation workflow

4. **[Slots API Collection](./api-testing/Slots_API_Collection.postman_collection.json)**
   - Time slot creation and management
   - Availability queries
   - Schedule management

#### 🔗 7.2 Link to Exported API Collections

**GitHub Repository Links:**
- **Main API Testing Folder**: [/api-testing/](./api-testing/)
- **Complete Documentation**: [API Testing Documentation](./api-testing/API_Testing_Documentation.md)
- **Quick Start Guide**: [API Testing README](./api-testing/README.md)
- **Environment Setup**: [Postman Environment](./api-testing/Therapy_Management_Environment.postman_environment.json)

#### 🚀 Quick Import to Postman:

1. **Download Collections**: Clone this repository or download individual collection files
2. **Import to Postman**: 
   - Open Postman → Click "Import"
   - Select all `.json` files from the `/api-testing` folder
   - Import the environment file for variables
3. **Start Testing**: Set your base URL and begin testing endpoints

#### 📊 API Endpoints Summary:

| Endpoint Category | Count | Authentication | Description |
|-------------------|-------|----------------|-------------|
| Authentication | 4 | Mixed | Register, login, profile management |
| Therapist Management | 7 | Mixed | Profile, search, availability |
| Booking Management | 3 | Required | Create, view, cancel bookings |
| Slot Management | 4 | Mixed | Time slot CRUD operations |

**Total API Endpoints**: 18 endpoints with full request/response documentation

#### 🔧 Sample API Request/Response:

**Registration Request:**
```http
POST /api/auth/register
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john.doe@example.com", 
  "password": "securePassword123",
  "role": "patient"
}
```

**Registration Response:**
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

For complete API documentation with all request/response examples, visit: **[API Testing Documentation](./api-testing/API_Testing_Documentation.md)**