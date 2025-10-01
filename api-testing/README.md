# API Testing Collections

This folder contains comprehensive Postman collections and documentation for testing the Therapy Management System APIs.

## 📁 Contents

### Postman Collections
- `Auth_API_Collection.postman_collection.json` - Authentication endpoints
- `Therapist_API_Collection.postman_collection.json` - Therapist management endpoints  
- `Booking_API_Collection.postman_collection.json` - Booking management endpoints
- `Slots_API_Collection.postman_collection.json` - Time slot management endpoints

### Environment Configuration
- `Therapy_Management_Environment.postman_environment.json` - Environment variables for testing

### Documentation
- `API_Testing_Documentation.md` - Comprehensive API testing guide with examples

## 🚀 Quick Start

### 1. Import to Postman
1. Open Postman
2. Click **Import** button
3. Select all `.json` files from this folder
4. Collections and environment will be imported automatically

### 2. Setup Environment
1. Select "Therapy Management System Environment" from the environment dropdown
2. Update `baseUrl` if your server runs on different port (default: `http://localhost:3000`)

### 3. Authentication Flow
1. Use **User Registration** request to create a new account
2. Copy the JWT token from the response  
3. Set the token in the `token` environment variable
4. All authenticated requests will now work

## 📋 Available Collections

### 🔐 Authentication API
- **POST** `/api/auth/register` - Register new user
- **POST** `/api/auth/login` - User login  
- **GET** `/api/auth/profile` - Get user profile
- **PUT** `/api/auth/profile` - Update profile

### 👩‍⚕️ Therapist API  
- **GET** `/api/therapists` - List all therapists
- **GET** `/api/therapists/search` - Search therapists
- **GET** `/api/therapists/:id` - Get therapist profile
- **GET** `/api/therapists/:id/slots` - Get therapist slots
- **PUT** `/api/therapists/me/profile` - Update therapist profile
- **PUT** `/api/therapists/me/availability` - Update availability

### 📅 Booking API
- **POST** `/api/bookings` - Create new booking
- **GET** `/api/bookings/my` - Get user bookings  
- **DELETE** `/api/bookings/:id` - Cancel booking

### ⏰ Slots API
- **GET** `/api/slots` - Get available slots
- **POST** `/api/slots` - Create new slot
- **GET** `/api/slots/:id` - Get specific slot
- **PUT** `/api/slots/:id` - Update slot

## 🧪 Test Scenarios

### Patient Journey
1. Register as patient → Login → Search therapists → View available slots → Create booking → View my bookings

### Therapist Journey  
1. Register as therapist → Login → Update profile → Create available slots → Update availability → View bookings

## 📊 Sample Responses

All requests include sample responses showing expected data structure and status codes.

## 🔧 Environment Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `baseUrl` | API base URL | `http://localhost:3000` |
| `token` | Patient JWT token | Set after login |
| `therapistToken` | Therapist JWT token | Set after therapist login |
| `therapistId` | Sample therapist ID | `64f8b2c3e1b2a4d5e6f7g8h1` |
| `slotId` | Sample slot ID | `64f8b2c3e1b2a4d5e6f7g8s1` |
| `bookingId` | Sample booking ID | `64f8b2c3e1b2a4d5e6f7g8b1` |

## 💡 Tips

- **Start your backend server** before testing (`npm run dev` in backend folder)
- **Use environment variables** for dynamic data like IDs and tokens
- **Check sample responses** to understand expected data format
- **Test error scenarios** by using invalid data or expired tokens
- **Follow the authentication flow** - register → login → copy token → test protected endpoints

## 🐛 Troubleshooting

### Common Issues:
- **Connection refused**: Make sure backend server is running
- **401 Unauthorized**: Check if JWT token is set and valid
- **404 Not Found**: Verify endpoint URLs and method types  
- **500 Server Error**: Check server logs for detailed error information

### Support:
If you encounter issues, check the detailed documentation in `API_Testing_Documentation.md` or review the backend server logs.