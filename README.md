# 🏥 Online Therapy Booking System

A comprehensive full-stack web application that helps patients find therapists and book therapy sessions online. The system features secure authentication, profile management, and an intuitive booking workflow with real-time availability checking.

## 🎯 Features

### For Patients:
- ✅ **User Registration & Authentication** - Secure sign-up and login system
- 👤 **Profile Management** - Update personal information, preferences
- 🔍 **Therapist Discovery** - Browse therapists by specialties, languages, ratings
- 📅 **Session Booking** - View available time slots and book appointments
- 📋 **Booking Management** - View, reschedule, and cancel appointments
- 🔒 **Secure Payment Processing** - Multiple payment method support

### For Therapists:
- 👩‍⚕️ **Professional Profiles** - Manage specialties, bio, availability
- 🗓️ **Schedule Management** - Set available time slots and working hours
- 📊 **Booking Dashboard** - View and manage patient appointments
- 💰 **Earnings Tracking** - Monitor session revenue and statistics

### System Features:
- 🛡️ **JWT Authentication** - Secure token-based authentication
- 🏗️ **Design Patterns** - Implementation of Observer, Command, Strategy, and Decorator patterns
- 📱 **Responsive Design** - Mobile-first UI with Material-UI components
- 🧪 **Comprehensive Testing** - Unit tests, integration tests, and API testing
- 🐳 **Docker Support** - Containerized MongoDB database
- 📚 **API Documentation** - Complete Postman collections with examples

## 🛠️ Technology Stack

### Backend:
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - ODM for MongoDB
- **JWT** - Authentication tokens
- **bcryptjs** - Password hashing
- **Multer** - File upload handling

### Frontend:
- **React 18** - UI library
- **Material-UI (MUI)** - Component library
- **React Router** - Client-side routing
- **Axios** - HTTP client
- **React Hook Form** - Form management
- **Bootstrap** - CSS framework

### Development & Testing:
- **Mocha & Chai** - Testing framework
- **Supertest** - API testing
- **Nodemon** - Development server
- **Concurrently** - Run multiple processes
- **Docker** - Database containerization
- **Postman** - API testing collections

## 📋 Prerequisites

Before setting up the application, ensure you have the following installed on your system:

### Required Software:
- **Node.js** (version 16.0 or higher)
  - Download from: https://nodejs.org/
  - Verify installation: `node --version` and `npm --version`

- **MongoDB** (Choose one option):
  - **Option 1**: MongoDB Atlas (Cloud) - Recommended for beginners
    - Create free account at: https://www.mongodb.com/cloud/atlas
  - **Option 2**: Local MongoDB installation
    - Download from: https://www.mongodb.com/try/download/community
  - **Option 3**: Docker (Included in this project)
    - Download Docker Desktop: https://www.docker.com/products/docker-desktop

- **Git** (for cloning the repository)
  - Download from: https://git-scm.com/downloads
  - Verify installation: `git --version`

### Optional but Recommended:
- **Postman** (for API testing)
  - Download from: https://www.postman.com/downloads/
- **VS Code** (recommended code editor)
  - Download from: https://code.visualstudio.com/

## 🚀 Installation & Setup Guide

### Step 1: Clone the Repository

```bash
# Clone the repository
git clone https://github.com/your-username/therapy-booking-system.git

# Navigate to the project directory
cd therapy-booking-system

# Or if you downloaded as ZIP, extract and navigate to the folder
```

### Step 2: Install Dependencies

We'll install all dependencies for the root, backend, and frontend simultaneously:

```bash
# Install all dependencies (root, backend, and frontend)
npm run install-all
```

**Alternative manual installation:**
```bash
# Install root dependencies
npm install

# Install backend dependencies
cd backend
npm install

# Install frontend dependencies
cd ../frontend
npm install

# Return to root directory
cd ..
```

### Step 3: Database Setup

#### Option A: Using Docker (Recommended)
```bash
# Navigate to backend directory
cd backend

# Start MongoDB using Docker Compose
docker-compose up -d

# Verify MongoDB is running
docker-compose ps
```

#### Option B: MongoDB Atlas (Cloud)
1. Create a MongoDB Atlas account at https://www.mongodb.com/cloud/atlas
2. Create a new cluster (free tier available)
3. Create a database user with read/write permissions
4. Get your connection string from the "Connect" button
5. Note down the connection string for the next step

#### Option C: Local MongoDB
```bash
# Start MongoDB service (varies by OS)
# macOS with Homebrew:
brew services start mongodb-community

# Linux (Ubuntu):
sudo systemctl start mongod

# Windows: Start MongoDB as a service from Services panel
```

### Step 4: Environment Configuration

#### Backend Environment Setup:
```bash
# Navigate to backend directory
cd backend

# Copy the environment example file
cp .env.example .env

# Edit the .env file with your configuration
nano .env  # or use any text editor
```

**Configure your `.env` file:**
```bash
# Database Configuration
MONGO_URI=mongodb://localhost:27017/therapybooking  # For local/Docker
# OR for MongoDB Atlas:
# MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/therapybooking

# JWT Configuration
JWT_SECRET=your-super-secret-jwt-key-here-make-it-long-and-random

# Server Configuration
PORT=5001
NODE_ENV=development

# Optional: File Upload Configuration
UPLOAD_PATH=./uploads
MAX_FILE_SIZE=5242880  # 5MB in bytes
```

**Generate a secure JWT secret:**
```bash
# Generate a random JWT secret (run this command and copy the output)
node -e "console.log(require('crypto').randomBytes(64).toString('hex'))"
```

### Step 5: Initialize Database with Sample Data

```bash
# Navigate to backend directory (if not already there)
cd backend

# Run the database initialization script
node mockData.js
```

This will create sample therapists, patients, and booking data for testing.

### Step 6: Start the Application

#### Option A: Start Both Frontend and Backend Simultaneously
```bash
# From the root directory
npm start
```

#### Option B: Start Services Individually
```bash
# Terminal 1: Start Backend Server
cd backend
npm run dev  # Development mode with auto-restart
# OR
npm start    # Production mode

# Terminal 2: Start Frontend Development Server
cd frontend
npm start
```

### Step 7: Verify Installation

1. **Backend API**: Open http://localhost:5001
   - You should see: `{"message": "Therapy Booking API is running!"}`

2. **Frontend Application**: Open http://localhost:3000
   - You should see the therapy booking homepage

3. **Database Connection**: Check the backend terminal for:
   ```
   Connected to MongoDB successfully
   Server is running on port 5001
   ```

## 🧪 Testing Guide

### Running Unit Tests

#### Backend Tests:
```bash
# Navigate to backend directory
cd backend

# Run all tests
npm test

# Run tests with coverage report
npm run test:coverage

# Run tests in watch mode (for development)
npm run test:watch

# Run specific test file
npm test -- --grep "auth"  # Run only authentication tests
npm test -- --grep "booking"  # Run only booking tests
```

#### Frontend Tests:
```bash
# Navigate to frontend directory
cd frontend

# Run all frontend tests
npm test

# Run tests with coverage
npm test -- --coverage

# Run tests in watch mode
npm test -- --watch
```

#### Run All Tests:
```bash
# From root directory - runs backend tests
npm test
```

### Test Coverage Information

The test suite includes:
- **Authentication Tests** (`auth.test.js`): Login, registration, JWT validation
- **Booking Tests** (`booking.test.js`): Create, read, update, delete bookings
- **Therapist Tests** (`therapist.test.js`): Therapist profile management
- **Smoke Tests** (`smoke.test.js`): Basic API connectivity tests

**Expected test results:**
- All tests should pass ✅
- Coverage should be above 80% for critical paths
- Database operations should complete successfully

## 📮 API Testing with Postman

### Step 1: Import Postman Collections

1. **Download and Install Postman**:
   - Visit https://www.postman.com/downloads/
   - Install Postman Desktop App

2. **Import Collections**:
   ```bash
   # All collection files are located in:
   ./api-testing/
   ```

   **Available Collections:**
   - `Auth_API_Collection.postman_collection.json` - Authentication endpoints
   - `Therapist_API_Collection.postman_collection.json` - Therapist management
   - `Booking_API_Collection.postman_collection.json` - Booking operations
   - `Slots_API_Collection.postman_collection.json` - Time slot management
   - `Therapy_Management_Environment.postman_environment.json` - Environment variables

3. **Import Process**:
   - Open Postman
   - Click **"Import"** button
   - Select **"Upload Files"**
   - Choose all `.json` files from `./api-testing/` folder
   - Click **"Import"**

### Step 2: Configure Environment

1. **Set Environment**:
   - In Postman, click the environment dropdown (top right)
   - Select **"Therapy Management Environment"**

2. **Update Environment Variables**:
   - Click the eye icon (👁️) next to environment name
   - Click **"Edit"**
   - Update values as needed:
     ```
     base_url: http://localhost:5001
     auth_token: (will be set automatically after login)
     user_id: (will be set automatically after login)
     ```

### Step 3: Test API Endpoints

#### Authentication Flow:
1. **Register a New User**:
   - Collection: `Auth API Collection`
   - Request: `POST Register User`
   - Run the request
   - Token will be automatically saved to environment

2. **Login**:
   - Request: `POST Login User`
   - Use registered credentials
   - Token will be automatically updated

#### Therapist Management:
1. **Get All Therapists**:
   - Collection: `Therapist API Collection`
   - Request: `GET All Therapists`

2. **Create Therapist Profile**:
   - Request: `POST Create Therapist`
   - Ensure you're logged in as a therapist

#### Booking Flow:
1. **View Available Slots**:
   - Collection: `Slots API Collection`
   - Request: `GET Available Slots`

2. **Create Booking**:
   - Collection: `Booking API Collection`
   - Request: `POST Create Booking`
   - Use valid therapist ID and slot ID

### Step 4: Automated Test Execution

```bash
# Install Newman (Postman CLI)
npm install -g newman

# Run collection via command line
newman run api-testing/Auth_API_Collection.postman_collection.json \
  -e api-testing/Therapy_Management_Environment.postman_environment.json

# Run all collections with reports
newman run api-testing/Auth_API_Collection.postman_collection.json \
  -e api-testing/Therapy_Management_Environment.postman_environment.json \
  --reporters html --reporter-html-export auth-test-report.html
```

## 🏗️ Development Guide

### Project Structure

```
therapy-booking-system/
├── 📁 api-testing/              # Postman collections & API documentation
│   ├── Auth_API_Collection.postman_collection.json
│   ├── Booking_API_Collection.postman_collection.json
│   ├── Slots_API_Collection.postman_collection.json
│   ├── Therapist_API_Collection.postman_collection.json
│   └── Therapy_Management_Environment.postman_environment.json
│
├── 📁 backend/                  # Node.js/Express API server
│   ├── 📁 config/              # Database configuration
│   ├── 📁 controllers/         # Route controllers
│   ├── 📁 middleware/          # Custom middleware
│   ├── 📁 models/              # Mongoose schemas
│   ├── 📁 patterns/            # Design pattern implementations
│   ├── 📁 repositories/        # Data access layer
│   ├── 📁 routes/              # API route definitions
│   ├── 📁 test/                # Unit and integration tests
│   ├── 📁 uploads/             # File upload directory
│   ├── .env.example           # Environment template
│   ├── docker-compose.yml     # MongoDB Docker setup
│   ├── mockData.js            # Sample data generator
│   ├── package.json           # Backend dependencies
│   └── server.js              # Application entry point
│
├── 📁 frontend/                 # React frontend application
│   ├── 📁 public/              # Static assets
│   ├── 📁 src/                 # React source code
│   │   ├── 📁 components/      # Reusable UI components
│   │   ├── 📁 context/         # React Context providers
│   │   ├── 📁 pages/           # Page components
│   │   ├── App.js              # Main App component
│   │   └── index.js            # React entry point
│   ├── package.json           # Frontend dependencies
│   └── tailwind.config.js     # Tailwind CSS configuration
│
├── README.md                   # This comprehensive guide
├── SRS.md                     # Software Requirements Specification
├── SystemArchitecture.puml   # System architecture diagram
└── package.json              # Root package for script orchestration
```

### Development Scripts

#### Root Level Scripts:
```bash
npm run install-all    # Install all dependencies (root, backend, frontend)
npm start             # Start both backend and frontend simultaneously
npm run dev           # Start backend in dev mode and frontend
npm test              # Run backend tests
```

#### Backend Scripts:
```bash
npm start             # Start production server
npm run dev           # Start development server with nodemon
npm test              # Run all tests
npm run test:watch    # Run tests in watch mode
npm run test:coverage # Run tests with coverage report
```

#### Frontend Scripts:
```bash
npm start             # Start development server (localhost:3000)
npm run build         # Create production build
npm test              # Run React tests
npm run lint          # Run ESLint
```

### Database Management

#### MongoDB Operations:
```bash
# Start MongoDB (Docker)
cd backend && docker-compose up -d

# Stop MongoDB (Docker)
cd backend && docker-compose down

# View MongoDB logs
docker-compose logs mongo

# Connect to MongoDB shell
docker exec -it backend_mongo_1 mongo therapybooking
```

#### Database Utilities:
```bash
# Reset database with fresh sample data
cd backend && node mockData.js

# View database contents (requires MongoDB shell)
mongo therapybooking
> show collections
> db.users.find().pretty()
> db.therapists.find().pretty()
> db.bookings.find().pretty()
```

## 🔧 Configuration Options

### Environment Variables Reference

#### Backend (.env):
```bash
# Database
MONGO_URI=mongodb://localhost:27017/therapybooking
MONGO_TEST_URI=mongodb://localhost:27017/therapybooking_test

# Authentication
JWT_SECRET=your-secret-key-here
JWT_EXPIRES_IN=7d

# Server
PORT=5001
NODE_ENV=development

# File Uploads
UPLOAD_PATH=./uploads
MAX_FILE_SIZE=5242880

# Email (Optional - for notifications)
EMAIL_SERVICE=gmail
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-app-password

# Payment (Optional - for payment processing)
STRIPE_SECRET_KEY=sk_test_your_stripe_key
STRIPE_WEBHOOK_SECRET=whsec_your_webhook_secret
```

### Frontend Configuration

#### API Configuration (`src/axiosConfig.jsx`):
```javascript
const baseURL = process.env.REACT_APP_API_URL || 'http://localhost:5001';
```

#### Environment Variables (`.env.local`):
```bash
REACT_APP_API_URL=http://localhost:5001
REACT_APP_ENVIRONMENT=development
```

## 🚨 Troubleshooting Guide

### Common Issues and Solutions

#### 1. MongoDB Connection Issues
**Problem**: `MongoNetworkError: failed to connect to server`

**Solutions**:
```bash
# Check if MongoDB is running
docker-compose ps  # For Docker setup

# Restart MongoDB
docker-compose down && docker-compose up -d

# Check connection string in .env file
# Ensure no typos in MONGO_URI
```

#### 2. Port Already in Use
**Problem**: `EADDRINUSE: address already in use :::5001`

**Solutions**:
```bash
# Find process using the port
lsof -i :5001

# Kill the process
kill -9 <PID>

# Or use a different port in .env
PORT=5002
```

#### 3. JWT Authentication Issues
**Problem**: `JsonWebTokenError: invalid token`

**Solutions**:
- Ensure JWT_SECRET is set in `.env`
- Check if token is properly included in request headers
- Verify token hasn't expired
- Clear browser localStorage and login again

#### 4. Frontend Build Issues
**Problem**: Module build errors or dependency conflicts

**Solutions**:
```bash
# Clear npm cache
npm cache clean --force

# Delete node_modules and reinstall
rm -rf node_modules package-lock.json
npm install

# For React-specific issues
cd frontend
rm -rf build
npm run build
```

#### 5. Test Failures
**Problem**: Tests failing due to database connection

**Solutions**:
```bash
# Ensure test database is running
cd backend
npm run test

# Check test environment variables
cat .env.test

# Clear test database
NODE_ENV=test node -e "
require('./config/db');
const mongoose = require('mongoose');
mongoose.connection.dropDatabase().then(() => process.exit());
"
```

### Performance Optimization Tips

1. **Database Indexing**:
   ```javascript
   // Add indexes for frequent queries
   db.therapists.createIndex({ "specialties": 1 });
   db.bookings.createIndex({ "therapistId": 1, "date": 1 });
   ```

2. **Frontend Optimization**:
   ```bash
   # Analyze bundle size
   cd frontend
   npm run build
   npx bundle-analyzer build/static/js/*.js
   ```

3. **API Response Caching**:
   - Implement Redis caching for frequent queries
   - Use HTTP caching headers
   - Implement request debouncing on frontend

## 📚 API Documentation

### Authentication Endpoints

#### POST `/api/auth/register`
Register a new user account.

**Request Body**:
```json
{
  "name": "John Doe",
  "email": "john.doe@example.com",
  "password": "securePassword123",
  "role": "patient"
}
```

**Response**:
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

#### POST `/api/auth/login`
Authenticate user and receive JWT token.

**Request Body**:
```json
{
  "email": "john.doe@example.com",
  "password": "securePassword123"
}
```

### Therapist Endpoints

#### GET `/api/therapists`
Get all therapists with filtering options.

**Query Parameters**:
- `specialty` - Filter by specialty
- `language` - Filter by language
- `minRating` - Minimum rating filter
- `availability` - Filter by availability

#### POST `/api/therapists`
Create a new therapist profile (requires authentication).

**Headers**:
```
Authorization: Bearer <jwt_token>
Content-Type: application/json
```

### Booking Endpoints

#### POST `/api/bookings`
Create a new booking.

**Request Body**:
```json
{
  "therapistId": "64f8b2c3e1b2a4d5e6f7g8h9",
  "slotId": "64f8b2c3e1b2a4d5e6f7g8h10",
  "date": "2025-10-15",
  "notes": "First session - anxiety counseling"
}
```

#### GET `/api/bookings/my-bookings`
Get current user's bookings (requires authentication).

### Complete API Reference
For detailed API documentation with all endpoints, request/response examples, and authentication requirements, see:
- **[API Testing Documentation](./api-testing/API_Testing_Documentation.md)**
- **Postman Collections** in `./api-testing/` folder

## 🤝 Contributing

### Development Workflow

1. **Fork the Repository**
2. **Create Feature Branch**:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make Changes and Test**:
   ```bash
   npm test  # Run backend tests
   cd frontend && npm test  # Run frontend tests
   ```
4. **Commit Changes**:
   ```bash
   git add .
   git commit -m "feat: add new feature description"
   ```
5. **Push and Create Pull Request**

### Code Style Guidelines

- **Backend**: Follow Node.js best practices, use ESLint
- **Frontend**: Follow React best practices, use JSX properly
- **Database**: Use descriptive collection and field names
- **Testing**: Maintain minimum 80% test coverage
- **Documentation**: Update README for any new features

### Design Patterns Used

This project implements several design patterns for better code organization:

1. **Repository Pattern** - Data access abstraction
2. **Observer Pattern** - Event notifications
3. **Command Pattern** - Booking operations
4. **Strategy Pattern** - Payment processing
5. **Decorator Pattern** - Authentication middleware

## 📄 License

This project is licensed under the ISC License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

### Getting Help

1. **Check this README** - Most common issues are covered above
2. **Search Issues** - Check if your problem has been reported
3. **Create an Issue** - Provide detailed information about your problem
4. **Contact Developer** - For urgent issues or collaboration

### Reporting Bugs

When reporting bugs, please include:
- Operating system and version
- Node.js and npm versions
- Complete error message
- Steps to reproduce the issue
- Expected vs actual behavior

### Feature Requests

We welcome feature requests! Please:
- Check existing issues first
- Provide clear description of the feature
- Explain the use case and benefits
- Consider implementation complexity

---

## 🎉 Quick Start Summary

For experienced developers, here's the quick setup:

```bash
# 1. Clone and install
git clone <repository-url>
cd therapy-booking-system
npm run install-all

# 2. Setup environment
cd backend
cp .env.example .env
# Edit .env with your MongoDB URI and JWT secret

# 3. Start database
docker-compose up -d

# 4. Initialize with sample data
node mockData.js

# 5. Start application
cd ..
npm start

# 6. Test everything
npm test
```

**Application URLs:**
- Frontend: http://localhost:3000
- Backend API: http://localhost:5001
- MongoDB: mongodb://localhost:27017

**Default Test Accounts:**
- Patient: `patient@example.com` / `password123`
- Therapist: `therapist@example.com` / `password123`

Happy coding! 🚀