# Task Checklist From `Fire_Extinguisher_Template/system.md`

This file turns the template brief into trackable tasks. Checked items are only those that are implemented in the current project state.

## Activity 1: Requirements Analysis and Design

- [x] Identify and define microservices
- [x] Provide Swagger/OpenAPI API documentation
- [x] Include User Management / Authentication service coverage
- [x] Include Fire Extinguisher Management service coverage
- [x] Include Inspection and Maintenance service coverage
- [x] Include Reporting service coverage
- [x] Include Notification service coverage
- [x] Provide database schema
- [x] Define table relationships
- [x] Define constraints and indexes
- [x] Provide starter relational seed data for local testing
- [ ] Provide ERD document
- [ ] Provide UI mockups in Figma or another design tool
- [ ] Provide registration mockup artifact
- [ ] Provide login mockup artifact
- [ ] Provide dashboard mockup artifact
- [ ] Provide fire extinguisher management mockup artifact
- [ ] Provide inspection scheduling mockup artifact
- [ ] Provide reports mockup artifact
- [x] Replace the generic blue-led UI theme with a fire-extinguisher-appropriate visual system
- [x] Define a reusable UI design system document for ongoing frontend work

## Activity 2: User Management Service

### Roles

- [x] Define `Admin` role
- [x] Define `Inspector` role
- [x] Define `User` role
- [x] Support role-based access in backend
- [x] Support role-based access in frontend routing

### User Registration API

- [x] Implement user registration endpoint
- [x] Accept first name
- [x] Accept last name
- [x] Accept email address
- [x] Accept password
- [x] Validate input data
- [x] Prevent duplicate registrations
- [x] Hash passwords securely

### Authentication and Authorization

- [x] Implement JWT-based authentication
- [x] Implement user login
- [x] Implement user logout
- [x] Implement token generation
- [x] Implement token validation
- [x] Implement RBAC

### User Profile Management

- [x] View profile API
- [x] Update profile API
- [x] Change password API
- [x] Recover forgotten password API

## Activity 3: Fire Extinguisher Management Service

### Register New Fire Extinguisher

- [x] Create extinguisher registration endpoint
- [x] Capture serial number
- [x] Capture location
- [x] Capture extinguisher type
- [x] Support `Water`
- [x] Support `CO2`
- [x] Support `Foam`
- [x] Support `Dry Chemical`
- [x] Capture extinguisher size
- [ ] Support `2.5 lbs.` exactly as specified in the template
- [x] Support `5 lbs.` equivalent through `5 lb`
- [x] Support `9 lbs.` equivalent through `9 lb`
- [x] Support `12 lbs.` equivalent through `12 lb`
- [x] Capture installation date
- [x] Capture expiry date
- [x] Capture status

### Fire Extinguisher CRUD

- [x] List all fire extinguishers
- [x] View extinguisher details by ID
- [x] Update extinguisher information
- [x] Delete extinguisher
- [x] Provide frontend add, view, and edit flows for major managed records

### Inspection Scheduling

- [x] Provide inspection scheduling API
- [x] Provide frontend inspection add, view, and edit flows
- [x] Select fire extinguisher
- [x] Choose inspection date
- [x] Choose inspection time
- [x] Allow users to schedule an inspection
- [x] Restrict normal users to scheduling only while admins and inspectors record outcomes
- [x] Select a verified inspector from the system instead of typing inspector name manually
- [x] Notify relevant personnel as a direct inspection-scheduling action

### Maintenance Logging

- [x] Provide maintenance logging API
- [x] Provide frontend maintenance add, view, and edit flows
- [x] Capture fire extinguisher reference
- [x] Capture action taken
- [x] Capture date of maintenance
- [x] Capture issues identified
- [x] Capture notes and recommendations

## Activity 4: Reporting Service

### Inventory Reports

- [x] Total number of fire extinguishers
- [x] Daily inventory summary
- [x] Monthly inventory summary
- [x] Yearly inventory summary

### Inspection Reports

- [x] Pending inspections
- [x] Completed inspections
- [x] Overdue inspections

### Compliance Reports

- [x] Expired fire extinguishers
- [x] Upcoming expirations
- [x] Compliance status

### Maintenance Reports

- [x] Maintenance history
- [x] Maintenance frequency
- [x] Recent maintenance activities

## Activity 5: API Testing and Deployment

### API Testing and Documentation

- [ ] Test all RESTful APIs end-to-end with recorded evidence
- [ ] Validate functionality and security with a formal test report
- [x] Document APIs using Swagger/OpenAPI
- [x] Expose Swagger UI plus raw OpenAPI YAML and JSON through the API gateway

### Database Export

- [ ] Export the database
- [ ] Provide backup scripts
- [ ] Push the project to the provided repository

### Local Database Usability

- [x] Align service DB connections to the current local PostgreSQL setup
- [x] Apply schema to the existing `femcs_db`
- [x] Apply migration updates to the existing `femcs_db`
- [x] Seed starter data into the existing `femcs_db`
- [x] Verify service-level database connectivity

### Report Export Functionality

- [x] Export reports in PDF format
- [x] Export reports in CSV format
- [x] Label report outputs under `TZW LTD` with generator details and readable structure

### Project Handover

- [x] Source code available
- [x] Swagger documentation available
- [ ] Database export available
- [ ] ERD available
- [ ] UI mockups available
- [ ] Test results document available
- [ ] Deployment guide available
- [ ] User manual available as a dedicated document
- [ ] Push completed project to the provided repository

## Current Reality Summary

Implemented well enough to use now:

- authentication and user management
- extinguisher CRUD
- inspection scheduling and recording
- maintenance logging
- notification mail configuration
- reporting and CSV/PDF export
- frontend navigation for all major workflows
- local PostgreSQL setup with starter seed data and verified service connectivity
- fire-safety UI theme with a documented design contract

Still missing as deliverable-grade artifacts:

- ERD
- UI mockups
- database export
- backup scripts
- full API test evidence
- deployment guide
- dedicated user manual
- repository push
