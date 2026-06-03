# App Walkthrough

This walkthrough explains what changed in the project and how to navigate the app after the Fire Extinguisher Management System adaptation.

## What Changed

The project was aligned to the `Fire_Extinguisher_Template/system.md` brief with these main changes:

- Roles were normalized to `admin`, `inspector`, and `user`.
- Authentication now includes:
  - registration
  - login
  - logout
  - token validation
  - profile retrieval
  - profile update
  - password change
  - forgot-password OTP reset
- Fire extinguisher registration now matches the brief more closely:
  - `serialNumber`
  - `location`
  - `type`
  - `size`
  - `installationDate`
  - `expiryDate`
  - `status`
- Inspection handling now supports scheduling:
  - extinguisher selection
  - verified inspector selection from active admin-managed inspector accounts
  - inspection date
  - inspection time
  - user scheduling-only flow
  - scheduled vs completed/failed states for inspector and admin users
  - notifying assigned personnel when a schedule is created
- Maintenance logging now includes:
  - action taken
  - issues identified
  - recommendations
- Reporting was expanded with:
  - inventory summary
  - inspection status summary
  - maintenance frequency
  - CSV export
  - PDF export
  - TZW LTD report branding and generator metadata for human-readable exports
- Mailers were updated to support `MAIL_*` environment variables while still accepting legacy `SMTP_*` names.
- The frontend was redesigned around a fire-safety visual system using charcoal, extinguisher red, and warm industrial support tones instead of the older blue-led theme.
- A dedicated UI contract now exists in `design.md` so future screens follow the same palette, typography, and component rules.

## Project Structure

Main areas in the repo:

- [api-gateway](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/api-gateway)
  Routes traffic to all backend services and serves Swagger docs.
- [services/auth-service](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/auth-service)
  Handles registration, login, logout, profile, password flows, and user admin.
- [services/entry-service](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/entry-service)
  Manages facilities/customers used as extinguisher ownership/site records.
- [services/extinguisher-service](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/extinguisher-service)
  Handles extinguisher CRUD, inspections, and maintenance.
- [services/notification-service](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/notification-service)
  Handles alerts, reminders, and escalation notifications.
- [services/report-service](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/report-service)
  Handles reporting and report export.
- [frontend](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend)
  React dashboard UI.
- [schema.sql](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/schema.sql)
  Full database schema.
- [migrate.sql](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/migrate.sql)
  Incremental schema updates.
- [seed.sql](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/seed.sql)
  Starter relational data for local use and walkthrough testing.
- [swagger.yaml](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/swagger.yaml)
  API documentation source.
- [design.md](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/design.md)
  UI design system and styling rules for future frontend work.

## Important Backend Files

- [auth.routes.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/auth-service/src/routes/auth.routes.js)
  Main auth/user API behavior.
- [extinguisher.routes.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/extinguisher-service/src/routes/extinguisher.routes.js)
  Extinguisher registration, listing, update, delete, stats.
- [inspection.routes.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/extinguisher-service/src/routes/inspection.routes.js)
  Inspection scheduling, inspection history, and inspection updates.
- [maintenance.routes.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/extinguisher-service/src/routes/maintenance.routes.js)
  Maintenance creation, listing, full record updates, and status updates.
- [report.routes.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/report-service/src/routes/report.routes.js)
  Report APIs and CSV/PDF export.

## Important Frontend Files

- [App.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/App.js)
  Route registration and protected pages.
- [Layout.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/components/Layout.js)
  Sidebar, header, notifications, password change modal.
- [DashboardPage.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/pages/DashboardPage.js)
  Summary cards and expiring extinguisher overview.
- [ExtinguishersPage.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/pages/ExtinguishersPage.js)
  Extinguisher CRUD UI.
- [InspectionsPage.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/pages/InspectionsPage.js)
  Inspection scheduling, viewing, and editing.
- [MaintenancePage.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/pages/MaintenancePage.js)
  Maintenance add, view, and edit UI.
- [CustomersPage.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/pages/CustomersPage.js)
  Customer add, view, and edit UI.
- [ReportsPage.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/pages/ReportsPage.js)
  Report generation and export UI.
- [RegisterPage.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/pages/RegisterPage.js)
  Updated user registration screen with the brief’s roles.
- [UsersPage.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/pages/UsersPage.js)
  Admin user and role management.

## How To Navigate The App

Before using the app in local manual mode, load the database in this order:

- [schema.sql](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/schema.sql)
- [migrate.sql](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/migrate.sql)
- [seed.sql](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/seed.sql)

The starter login seeded into the database is:

- email: `admin@femcs.rw`
- password: `Admin@1234`

After login, the sidebar is the main navigation.

### 1. Dashboard

Route: `/dashboard`

Use this page to see:

- total extinguishers
- active extinguishers
- expired extinguishers
- expiring soon counts
- compliance issues
- last 30 days inspection activity

### 2. Facilities

Route: `/customers`

This page still uses the older `customers` service name internally, but in the app it represents site/facility records tied to extinguishers.

Use it to:

- create a facility/site record
- view existing facility records
- update facility details
- delete a facility if it has no extinguisher dependencies

### 3. Extinguishers

Route: `/extinguishers`

Use this page to:

- register a new extinguisher
- filter by status, type, and compliance
- open extinguisher detail modal
- edit extinguisher information
- delete extinguisher records if you are an admin

Registration fields now focus on:

- serial number
- facility
- type
- size
- installation date
- expiry date
- status
- location

### 4. Inspections

Route: `/inspections`

Use this page to:

- schedule an inspection by selecting an extinguisher
- select an active verified inspector from the system
- choose inspection date
- choose inspection time
- notify the assigned inspector and admin users when the schedule is created
- track scheduled/completed/requires service/failed records
- open a full detail view for a scheduled or completed inspection
- edit an existing inspection record from the list or detail modal

Role behavior on this page:

- `user` accounts can schedule only
- `admin` and `inspector` accounts can schedule and record inspection outcomes

### 5. Maintenance

Route: `/maintenance`

Use this page to:

- log a maintenance record
- capture action taken
- capture issues identified
- capture recommendations
- track service company, technician, cost, and next service date
- open a maintenance detail view
- edit an existing maintenance record from the list or detail modal

### 6. Reports

Route: `/reports`

Admin-only.

Use this page to:

- generate expired extinguisher reports
- generate upcoming expiration reports
- generate facility reports
- generate inspection reports
- generate maintenance reports
- generate compliance reports
- export CSV
- export PDF

### 7. Escalations

Route: `/escalations`

Admin-only.

Use this page to review escalation records produced by the notification logic.

### 8. Users

Route: `/users`

Admin-only.

Use this page to:

- search users
- open a user detail view
- activate/deactivate accounts
- change user roles

## Authentication Flow

Main auth screens:

- `/register`
- `/login`
- `/forgot-password`
- `/reset-password`

Authenticated account features:

- view own profile through API
- update own profile through API
- change own password from the layout modal
- logout

## Mail Configuration

The email-enabled services use local `.env` files with:

- `MAIL_HOST`
- `MAIL_PORT`
- `MAIL_SECURE`
- `MAIL_USERNAME`
- `MAIL_PASSWORD`
- `EMAIL_FROM`

Relevant files:

- [services/auth-service/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/auth-service/.env)
- [services/extinguisher-service/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/extinguisher-service/.env)
- [services/notification-service/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/notification-service/.env)

## What Was Verified

Verified in this workspace:

- modified backend route files parse with `node --check`
- modified mailer files parse with `node --check`
- API gateway Swagger integration parses the current `swagger.yaml`
- frontend production build succeeds with `npm run build`
- `schema.sql`, `migrate.sql`, and `seed.sql` were applied to local `femcs_db`
- database connectivity was verified from auth, entry, extinguisher, notification, and report services
- seeded starter data exists for users, facilities, extinguishers, inspections, maintenance, notifications, and escalations

## What Is Still Not Fully Delivered

These are still outside the currently completed deliverables:

- ERD document
- Figma/UI mockup files
- database export artifact
- backup scripts
- a complete API test report with execution evidence
- full deployment guide
- full end-user manual separate from README and this walkthrough

## API Documentation Access

With the API gateway running, the backend documentation is available at:

- Swagger UI: `/api/docs`
- Raw OpenAPI YAML: `/api/docs/swagger.yaml`
- Raw OpenAPI JSON: `/api/docs/swagger.json`
