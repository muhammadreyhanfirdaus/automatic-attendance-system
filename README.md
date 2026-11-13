# Automatic Attendance System

A web-based employee attendance management system built with HTML, JavaScript, Firebase Authentication, and Cloud Firestore.

## Overview

**Automatic Attendance System** is an employee attendance and workforce administration application designed to manage daily attendance, employee master data, leave requests, schedules, holidays, and reporting through a web-based interface.

The project demonstrates the implementation of a serverless-style web application using Firebase services, with separate workflows for employees and administrators.

> **Portfolio version:** This repository has been sanitized for public portfolio use. Production-specific identifiers, credentials, employee data, recovery tools, and production security rules are intentionally excluded.

## Project Highlights

- NIK-based employee authentication and registration
- Daily check-in and check-out workflow
- Automatic attendance time tracking
- Late arrival, early departure, overtime, and working-hour calculation
- Employee master data management
- Excel/CSV employee data import
- Leave and work-from-home request workflow
- Administrative approval and attendance correction
- Holiday and work-schedule management
- Excel and PDF report generation
- Firebase Authentication and Cloud Firestore integration
- Firebase Hosting support

## Key Features

### Authentication

The application uses **Firebase Authentication** for employee and administrator login.

- Email/password authentication
- NIK-based employee registration workflow
- Administrative access
- Session-aware application workflow

For the portfolio version, organization-specific email domains have been replaced with `@demo.example`.

### Employee Management

Employee master data is stored in the `employee_registry` Firestore collection.

Supported employee information includes:

- NIK
- Name
- Position
- Work unit
- Employment status

Administrators can import employee data from:

- `.xlsx`
- `.xls`
- `.csv`

### Attendance Management

Attendance records are stored in the `attendance` Firestore collection.

The attendance workflow supports:

- Check-in
- Check-out
- Firestore server timestamps
- Working-hour calculation
- Late arrival calculation
- Early departure calculation
- Overtime calculation
- Attendance notes
- Activity notes
- Administrative attendance correction

### Leave and Work-from-Home Requests

Employees can submit requests through the `leave_requests` collection.

The workflow supports:

- Request submission
- Request status tracking
- Administrative approval
- Administrative rejection
- Approval timestamp
- Approver information

### Schedule and Holiday Management

The application includes configuration for:

- Work schedules
- Holidays
- Attendance-related settings

### Reporting

The application provides report export functionality.

#### Excel

Excel reports are generated using **SheetJS / XLSX**.

#### PDF

PDF reports are generated using:

- jsPDF
- jsPDF AutoTable

Reports can be formatted for A4 output.

## Technology Stack

| Technology | Purpose |
|---|---|
| HTML5 | Application structure and interface |
| JavaScript | Application logic and business workflow |
| Tailwind CSS | User interface styling |
| Firebase Authentication | User authentication |
| Cloud Firestore | Application database |
| Firebase Hosting | Web application hosting |
| SheetJS / XLSX | Excel/CSV processing and export |
| jsPDF | PDF report generation |
| jsPDF AutoTable | Tabular PDF reports |

## System Architecture

```text
                    ┌─────────────────────┐
                    │   Employee / Admin  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │  Web Application    │
                    │ HTML + JavaScript   │
                    └──────────┬──────────┘
                               │
              ┌────────────────┴────────────────┐
              │                                 │
              ▼                                 ▼
    ┌──────────────────┐             ┌────────────────────┐
    │ Firebase Auth    │             │ Cloud Firestore    │
    │ Login / Register │             │ Application Data   │
    └──────────────────┘             └─────────┬──────────┘
                                               │
                 ┌──────────────┬─────────────┼──────────────┐
                 ▼              ▼             ▼              ▼
          Employee Data    Attendance   Leave Requests   Settings
                 │              │             │              │
                 └──────────────┴─────────────┴──────────────┘
                                               │
                                               ▼
                                     ┌────────────────────┐
                                     │ Admin Workflow     │
                                     │ Approval / Edit    │
                                     └─────────┬──────────┘
                                               │
                                               ▼
                                     ┌────────────────────┐
                                     │ Report Generation  │
                                     │ Excel / PDF        │
                                     └────────────────────┘
```

## Firestore Data Model

| Collection | Purpose |
|---|---|
| `_system` | System-level application data |
| `employee_registry` | Employee master data |
| `users` | User/account-related application data |
| `attendance` | Daily attendance records |
| `holidays` | Holiday configuration |
| `settings` | Application and work-schedule settings |
| `leave_requests` | Leave and work-from-home requests |

A sanitized Firestore rules template is included in:

```text
firestore.rules.example
```

The example rules are intentionally restrictive and **must not be treated as production rules**.

## Project Structure

```text
.
├── firebase.json
├── firestore.rules.example
├── README.md
└── public/
    └── index.html
```

The main application is contained in:

```text
public/index.html
```

Internal backups, recovery packages, administrative tools, production configuration, and sensitive data are intentionally excluded from this repository.

## Technical Challenges & Solutions

### Authentication and Employee Identity

**Challenge:** Provide an employee-friendly authentication workflow while using an organizational employee identifier.

**Solution:** The application uses NIK-based registration and maps the NIK to a Firebase Authentication email-style identity in the sanitized portfolio version.

### Attendance Timestamp Management

**Challenge:** Attendance timestamps should be consistent and should not depend only on the browser's local clock.

**Solution:** Firestore server timestamps are used for attendance events and relevant record updates.

### Attendance Calculation

**Challenge:** Attendance management requires more than simply storing check-in and check-out times.

**Solution:** The application calculates and reports:

- Late arrival
- Early departure
- Overtime
- Total working hours

### Employee Data Import

**Challenge:** Administrators may need to register or update many employees efficiently.

**Solution:** Excel/CSV import is implemented using SheetJS, with employee records written to the `employee_registry` collection.

### Administrative Workflow

**Challenge:** Attendance and leave records require administrative control.

**Solution:** The application provides administrative workflows for leave approval and attendance record correction.

### Reporting

**Challenge:** Attendance data needs to be usable outside the web application.

**Solution:** The application provides Excel and PDF export functionality for attendance reporting.

## Security & Data Sanitization

This repository has been prepared specifically for public portfolio use.

The following production-specific information is intentionally excluded:

- Firebase production project identifiers
- Production credentials and secrets
- Firebase service account credentials
- Production Firestore Security Rules
- Real employee data
- Internal organization email addresses
- Password administration tools
- Recovery packages
- Production backups
- Internal audit files

The Firebase configuration in `public/index.html` uses placeholders such as:

```javascript
YOUR_FIREBASE_API_KEY
YOUR_PROJECT_ID
YOUR_FIREBASE_APP_ID
```

The portfolio version also uses demo organization identifiers and coordinates.

> Never commit real credentials, service account keys, employee data, production backups, or private security configuration to a public repository.

## Firebase Setup

To run the application with your own Firebase project:

### 1. Create a Firebase project

Create a Firebase project and register a Web App.

### 2. Enable Authentication

Enable:

```text
Authentication
└── Sign-in method
    └── Email/Password
```

### 3. Create Firestore

Create a Cloud Firestore database.

Review and configure the required collections and security rules according to your own application requirements.

### 4. Configure Firebase

Replace the placeholder Firebase configuration in:

```text
public/index.html
```

with the configuration from your own Firebase Web App.

### 5. Install Firebase CLI

```bash
npm install -g firebase-tools
```

Authenticate:

```bash
firebase login
```

### 6. Configure the project

Create/configure your own Firebase project association before deployment.

The repository does not include the production `.firebaserc` file intentionally.

### 7. Review Security Rules

The repository includes:

```text
firestore.rules.example
```

This is a template only. Create and review your own `firestore.rules` before deploying.

### 8. Deploy

After reviewing configuration and security rules:

```bash
firebase deploy
```

## Running Locally

For a local Firebase-based test environment, configure your own Firebase project first.

The repository's Firebase configuration contains emulator settings for:

- Authentication
- Firestore
- Hosting
- Firebase Emulator UI

Start the Firebase emulators with:

```bash
firebase emulators:start
```

Do not connect a development environment to production data without reviewing authentication and Firestore security rules.

## Important Notes

This repository is a **portfolio/sanitized version** of an attendance management application.

It is intended to demonstrate:

- Front-end development
- Firebase integration
- Authentication workflow
- Firestore data management
- Attendance business logic
- Administrative workflow
- Data import and reporting
- Security-conscious source sanitization

It is not intended to be deployed directly as a production system without additional configuration, security review, testing, and operational controls.

## Future Improvements

Potential improvements for a future version include:

- Migration from a single-page HTML application to a modular front-end architecture
- Stronger role-based access control
- More granular Firestore Security Rules
- Automated testing
- Better separation between UI, business logic, and data access
- Centralized configuration management
- Improved audit logging
- Dashboard analytics
- Mobile-responsive improvements
- CI/CD deployment workflow
- Automated backup and recovery strategy

## Portfolio Note

This project demonstrates practical experience in developing and maintaining a web-based attendance management application using Firebase and JavaScript.

The repository has been intentionally sanitized so that the project can be presented publicly without exposing production-specific information.

---

**Author:** Reyhan Firdaus

**Repository:** `automatic-attendance-system`