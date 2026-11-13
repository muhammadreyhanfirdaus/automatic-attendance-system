# Automatic Attendance System

A web-based employee attendance management system built with HTML, JavaScript, Firebase Authentication, and Cloud Firestore.

## Overview

This project provides a simple attendance workflow for employees and administrators. It was designed to demonstrate authentication, attendance management, employee master data, leave requests, reporting, and Firebase integration.

## Features

- Employee login and registration using NIK-based identity
- Firebase Authentication integration
- Employee master data management
- Excel-based employee data import
- Daily check-in and check-out
- Late arrival, early departure, overtime, and total working-hour calculation
- Activity and attendance notes
- Work schedule configuration
- Holiday management
- Leave and work-from-home requests
- Administrative approval workflow
- Attendance data management and correction
- Excel report export
- PDF report export
- Firebase Hosting support
- Firebase Firestore integration

## Technology Stack

- HTML5
- JavaScript
- Tailwind CSS
- Firebase Authentication
- Cloud Firestore
- Firebase Hosting
- SheetJS / XLSX
- jsPDF

## Project Structure

```text
.
├── firebase.json
├── firestore.rules.example
├── README.md
└── public/
    └── index.html
```

## Firebase Configuration

The Firebase configuration in `public/index.html` uses placeholder values so that production project information is not exposed in this portfolio repository.

To run the application with Firebase, create your own Firebase project and replace the placeholder configuration with your own Firebase Web App configuration.

Required Firebase services:

1. Firebase Authentication - Email/Password
2. Cloud Firestore
3. Firebase Hosting

## Firestore Collections

The application uses the following Firestore collections:

- `_system`
- `employee_registry`
- `users`
- `attendance`
- `holidays`
- `settings`
- `leave_requests`

A sanitized rules template is provided in `firestore.rules.example`. Review and customize the rules before using the application in any real environment.

## Employee Data Format

The employee import feature expects an Excel file containing columns such as:

```text
NIK | Nama | Jabatan | Unit Kerja | Status
```

Example:

```text
0000000000000000 | DEMO USER | STAFF | DEMO UNIT | Aktif
```

Do not use real employee data in a public repository.

## Running Locally

Install Firebase CLI:

```bash
npm install -g firebase-tools
```

Authenticate:

```bash
firebase login
```

Configure the project using your own Firebase project and deploy only after reviewing the Firebase configuration and Security Rules.

## Security Notes

This repository intentionally does not contain:

- Firebase production configuration
- Firebase service account credentials
- Production Firestore Security Rules
- Internal organization email addresses
- Real employee data
- Recovery packages
- Password administration tools
- Production backups

Always review authentication settings and Firestore Security Rules before deploying the application.

## Portfolio Note

This repository is a sanitized portfolio version of an attendance management application. Production-specific identifiers and configuration have been replaced with examples or placeholders.
