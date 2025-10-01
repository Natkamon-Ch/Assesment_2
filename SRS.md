
# SRS Documentation

## 2.1 Purpose
The purpose of this Software Requirements Specification (SRS) is to provide a comprehensive and detailed description of the Mental Health Care Management Platform. This document is intended for stakeholders including developers, project managers, testers, and academic evaluators. It aims to ensure that all functional and non-functional requirements are clearly defined, the rationale for design choices is explained, and the system’s objectives are aligned with real-world needs. The platform is designed to facilitate secure, efficient, and user-friendly interactions between patients and licensed therapists, supporting appointment scheduling, therapist discovery, and ongoing care management.

## 2.2 Problem Statement
Mental health care is a critical need, but many individuals face significant barriers when seeking support. These barriers include difficulty in finding qualified therapists, lack of transparency in therapist credentials and availability, cumbersome appointment scheduling processes, and concerns about privacy and data security. Existing solutions may be fragmented, lack robust security, or fail to provide a seamless experience for both patients and therapists. The proposed system addresses these issues by offering a centralized platform where patients can easily discover therapists, view verified profiles, book sessions within regulated business hours, and manage personal care tasks. Therapists, in turn, can efficiently manage their schedules, update their profiles, and interact securely with patients. The platform aims to reduce administrative overhead, improve access to care, and foster trust through secure, transparent operations.

## 2.3 Scope
The scope of this project encompasses the development of a full-stack web application for mental health care management. The system will include:

- **Therapist Profile Management:** Therapists can create, update, and maintain detailed profiles including qualifications, specialties, languages spoken, experience, and availability. Only verified therapists are allowed to offer sessions.
- **Patient Registration and Authentication:** Patients can register, authenticate securely, and manage their personal information. The system supports password recovery and secure session management.
- **Therapist Discovery and Search:** Patients can search for therapists using filters such as specialization, language, availability, and ratings. Search results display verified profiles and available slots.
- **Slot Management and Appointment Booking:** Therapists define their available time slots, and patients can book sessions within these slots. The system enforces business rules such as booking only within business hours and prevents double-booking.
- **Task Management for Patients:** Patients can create, view, update, and delete personal tasks related to their care, such as medication reminders or therapy goals.
- **Notifications for Booking Events:** The system sends notifications (email/SMS) for booking confirmations, cancellations, and reminders, ensuring all parties are informed of session status.
- **Secure Data Handling and Role-Based Access:** All sensitive data is encrypted, and access is controlled based on user roles (patient, therapist, admin).
- **Responsive Web Interface:** The application is accessible on both desktop and mobile devices, ensuring usability for all users.

## 2.4 User Characteristics

- **Patients:** Individuals seeking mental health support. They may vary widely in age, technical proficiency, and specific care needs. Some may be tech-savvy, while others may require a highly intuitive interface. Patients expect privacy, ease of use, and reliable access to qualified therapists.
- **Therapists:** Licensed professionals who provide mental health services. They manage their profiles, set their availability, and handle bookings. Therapists may have varying levels of comfort with technology and expect secure, efficient tools to manage their practice.
- **Administrators (optional):** Users responsible for overseeing platform operations, verifying therapist credentials, managing user accounts, and monitoring system health. Admins require advanced controls and reporting features.

## 2.5 Constraints

- **Regulatory Compliance:** The system must comply with healthcare data privacy regulations such as HIPAA (USA) and GDPR (EU). This includes secure data storage, encrypted communications, and explicit user consent for data processing.
- **Scalability:** The platform should be designed to support a growing user base, potentially scaling to thousands of concurrent users without performance degradation.
- **Verification:** Only therapists who have been verified by administrators can offer sessions. Verification includes credential checks and profile approval.
- **Business Hours Enforcement:** Bookings can only be made within defined business hours (e.g., 9 AM to 5 PM), as set by therapists and enforced by the system.
- **Device Accessibility:** The web application must be fully functional on both desktop and mobile browsers, with responsive design and accessibility features for users with disabilities.
- **Third-Party Integrations:** Any integration with external services (e.g., payment gateways, notification providers) must be secure and comply with relevant standards.

## 2.6 Functional Requirements

1. **User Registration and Authentication**
  - Patients and therapists can register using email and password.
  - Secure login and logout functionality.
  - Password reset and account recovery options.

2. **Therapist Profile Management**
  - Therapists can create and edit profiles with personal, professional, and availability information.
  - Profile pictures and documents can be uploaded securely.
  - Admins can verify and approve therapist profiles.

3. **Therapist Discovery and Search**
  - Patients can search for therapists using filters (specialization, language, availability, ratings).
  - Search results display therapist details and available slots.

4. **Slot Management and Booking**
  - Therapists define available slots for sessions.
  - Patients can view open slots and book appointments.
  - System prevents double-booking and enforces business hours.
  - Patients and therapists can view, cancel, or reschedule bookings.

5. **Task Management for Patients**
  - Patients can create, update, and delete personal tasks (e.g., reminders, goals).
  - Tasks are displayed in the dashboard and can be marked as completed.

6. **Notifications**
  - Automated notifications for booking confirmations, cancellations, and reminders via email/SMS.
  - Notification preferences can be managed by users.

7. **Role-Based Access Control**
  - Access to features and data is restricted based on user roles (patient, therapist, admin).

8. **Secure File Uploads**
  - Profile pictures and documents are uploaded using secure protocols and scanned for malware.

## 2.7 Non-Functional Requirements (NFRs)

1. **Performance**
  - The system should respond to user actions (e.g., search, booking) within 2 seconds under normal load.
  - Page load times should be optimized for both desktop and mobile devices.

2. **Reliability**
  - The platform must maintain 99.9% uptime, with automated backups and disaster recovery procedures.
  - Error handling and logging should be implemented throughout the system.

3. **Security**
  - All sensitive data must be encrypted in transit (TLS/SSL) and at rest.
  - Secure authentication and authorization mechanisms (JWT, OAuth).
  - Regular security audits and vulnerability assessments.

4. **Usability**
  - The user interface should be intuitive, with clear navigation and accessible design.
  - Support for screen readers and keyboard navigation.

5. **Scalability**
  - The system architecture should support horizontal scaling (e.g., load balancing, microservices).
  - Database and API endpoints should be optimized for high concurrency.

6. **Maintainability**
  - The codebase should be modular, well-documented, and covered by automated tests.
  - Continuous integration and deployment (CI/CD) pipelines should be used for updates.

## 2.8 User Interface Mockups/Wireframes (Low Fidelity Design)

Below are textual representations of key screens. These wireframes illustrate the layout and flow of the user interface, focusing on clarity and accessibility.

```
Home Page
-------------------------------------------------
| [Logo]         [Login] [Sign Up]               |
|------------------------------------------------|
| Find Your Therapist                           |
| [Search Bar: Specialization, Language, etc.]  |
| [Therapist Card] [Therapist Card] ...         |
|------------------------------------------------|

Booking Page
-------------------------------------------------
| [Therapist Profile: Name, Specialization]      |
| [Available Slots List: Date, Time]             |
| [Book Slot Button]                             |
| [Booking Confirmation/Notification]            |
-------------------------------------------------|

Dashboard
-------------------------------------------------
| [Upcoming Bookings]                            |
| [Personal Tasks: Add/Edit/Delete/Complete]     |
| [Profile Settings]                             |
-------------------------------------------------|
```

## 2.9 Complete System Diagram

The following diagram describes the high-level architecture and data flow:

```
  +-------------------+      +-------------------+      +-------------------+
  |   Frontend (Web)  |<---->|   Backend (API)   |<---->|   Database (Mongo)|
  +-------------------+      +-------------------+      +-------------------+
        |                        |                          |
        v                        v                          v
  Patients/Therapists      Business Logic            Data Storage
  UI/UX Components         Auth, Booking, Slots       Users, Bookings, Slots
```

**Frontend (Web):**
  - Built with React, Material UI, and Bootstrap.
  - Provides user interfaces for patients, therapists, and admins.
  - Handles user input, displays data, and communicates with the backend via REST APIs.

**Backend (API):**
  - Built with Node.js and Express.
  - Implements business logic, authentication, booking management, notifications, and data validation.
  - Exposes RESTful endpoints for frontend consumption.

**Database (MongoDB):**
  - Stores user profiles, therapist data, slots, bookings, and tasks.
  - Ensures data integrity and supports complex queries for search and reporting.

## 2.10 Safety Considerations

Safety is paramount in healthcare applications. The following measures are implemented to protect users and data:

- **Data Encryption:** All sensitive information (personal details, health data, credentials) is encrypted both in transit (using TLS/SSL) and at rest in the database.
- **Input Validation:** All user inputs are validated and sanitized to prevent injection attacks, cross-site scripting (XSS), and other vulnerabilities.
- **Dependency Management:** Third-party libraries and dependencies are regularly updated to patch known security vulnerabilities.
- **Privacy Policies and Consent:** Users are presented with clear privacy policies and must provide explicit consent for data collection and processing. Data access is logged and monitored.
- **Session Management:** Secure session handling prevents unauthorized access and session hijacking.

## 2.11 Risk Management

Effective risk management ensures the platform remains secure, reliable, and compliant:

- **Data Breach:** Mitigated through strong encryption, access controls, regular security audits, and real-time monitoring. Incident response plans are in place to address breaches.
- **System Downtime:** Cloud infrastructure with automated backups, failover strategies, and disaster recovery plans minimize downtime and data loss.
- **User Misuse:** Verification processes, role-based permissions, and activity logging prevent unauthorized actions and misuse of the platform.
- **Regulatory Compliance:** Regular audits, legal reviews, and updates to policies ensure ongoing compliance with healthcare regulations. All changes are documented and communicated to users.
