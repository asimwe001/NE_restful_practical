# Running Guide

This is the exact project to run:

- [FEMS](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS)

This guide is written to start the system with the least friction. Use **Docker Compose** if you want the cleanest startup path. Use **manual mode** only if you specifically want to run each service yourself.

## Recommended Way: Docker Compose

This is the best option because it:

- starts PostgreSQL automatically
- loads [schema.sql](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/schema.sql)
- loads [migrate.sql](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/migrate.sql)
- can also load [seed.sql](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/seed.sql) manually after startup
- starts services in dependency order
- exposes all ports consistently

## Prerequisites

Install:

- Docker Desktop

Confirm:

```powershell
docker --version
docker compose version
```

## Step 1: Go To The Project

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS
```

## Step 2: Create Root `.env`

Docker Compose reads the root `.env`, not the per-service `.env` files.

Create `FEMS\.env` with this content:

```env
JWT_SECRET=femcs_jwt_super_secret_change_in_production

SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_SECURE=false
SMTP_USER=grouphantom@gmail.com
SMTP_PASS=agmh ihko nrjs qztt
EMAIL_FROM=Fire Extinguisher System <grouphantom@gmail.com>
```

You can also copy [ .env.example ](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/.env.example) and then replace the SMTP values.

## Step 3: Start Everything

```powershell
docker compose up --build
```

If you want it in the background:

```powershell
docker compose up --build -d
```

## Step 4: Verify Startup

Open these URLs after startup:

- Frontend: `http://localhost:3000`
- API Gateway: `http://localhost:5000`
- Swagger Docs: `http://localhost:5000/api/docs`
- OpenAPI YAML: `http://localhost:5000/api/docs/swagger.yaml`
- OpenAPI JSON: `http://localhost:5000/api/docs/swagger.json`

Health endpoints:

- `http://localhost:5000/health`
- `http://localhost:5001/health`
- `http://localhost:5002/health`
- `http://localhost:5003/health`
- `http://localhost:5004/health`
- `http://localhost:5005/health`

## Default Login

Use:

- Email: `admin@femcs.rw`
- Password: `Admin@1234`

This login is loaded by [seed.sql](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/seed.sql).

## Stop The Stack

```powershell
docker compose down
```

To also remove the database volume:

```powershell
docker compose down -v
```

Use `-v` only if you want to fully reset the database.

## Manual Way

Use this only if you do not want Docker.

## Prerequisites For Manual Mode

Install:

- Node.js
- npm
- PostgreSQL

## Step 1: Use Your Existing PostgreSQL Database

This project should use the database you already created:

- database: `femcs_db`
- username: `postgres`
- password: `postgres`

From the project root, load the schema:

```powershell
$env:PGPASSWORD='postgres'
psql -U postgres -d femcs_db -f schema.sql
```

Then apply the incremental changes:

```powershell
psql -U postgres -d femcs_db -f migrate.sql
```

Then load starter relational data:

```powershell
psql -U postgres -d femcs_db -f seed.sql
```

If `psql` is not available on your terminal `PATH`, use the common Windows install path directly:

```powershell
$env:PGPASSWORD='postgres'
& 'C:\Program Files\PostgreSQL\17\bin\psql.exe' -U postgres -d femcs_db -f schema.sql
& 'C:\Program Files\PostgreSQL\17\bin\psql.exe' -U postgres -d femcs_db -f migrate.sql
& 'C:\Program Files\PostgreSQL\17\bin\psql.exe' -U postgres -d femcs_db -f seed.sql
```

Run those commands from:

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS
```

## Step 2: Install Dependencies

Install dependencies in each app:

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\api-gateway
npm install
```

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\services\auth-service
npm install
```

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\services\entry-service
npm install
```

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\services\extinguisher-service
npm install
```

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\services\notification-service
npm install
```

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\services\report-service
npm install
```

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\frontend
npm install
```

## Step 3: Make Sure Env Files Exist

These should exist already in your local workspace:

- [services/auth-service/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/auth-service/.env)
- [services/extinguisher-service/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/extinguisher-service/.env)
- [services/notification-service/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/notification-service/.env)

You should also create these if they do not exist:

- [api-gateway/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/api-gateway/.env)
- [services/entry-service/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/entry-service/.env)
- [services/report-service/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/report-service/.env)

Suggested contents:

`api-gateway/.env`

```env
PORT=5000
AUTH_SERVICE_URL=http://localhost:5001
CUSTOMER_SERVICE_URL=http://localhost:5002
EXTINGUISHER_SERVICE_URL=http://localhost:5003
NOTIFICATION_SERVICE_URL=http://localhost:5004
REPORT_SERVICE_URL=http://localhost:5005
FRONTEND_URL=http://localhost:3000
```

If you want to be explicit for both the React app and Swagger UI, you can also use:

```env
FRONTEND_URL=http://localhost:3000,http://localhost:5000
```

`services/entry-service/.env`

```env
PORT=5002
DB_URL=postgresql://postgres:postgres@localhost:5432/femcs_db
JWT_SECRET=femcs_jwt_super_secret_change_in_production
NODE_ENV=development
```

`services/report-service/.env`

```env
PORT=5005
DB_URL=postgresql://postgres:postgres@localhost:5432/femcs_db
JWT_SECRET=femcs_jwt_super_secret_change_in_production
NODE_ENV=development
```

## Step 4: Start Services In This Order

Open a separate terminal for each service.

1. Auth service

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\services\auth-service
npm run dev
```

2. Entry service

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\services\entry-service
npm run dev
```

3. Extinguisher service

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\services\extinguisher-service
npm run dev
```

4. Notification service

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\services\notification-service
npm run dev
```

5. Report service

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\services\report-service
npm run dev
```

6. API gateway

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\api-gateway
npm run dev
```

7. Frontend

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS\frontend
npm start
```

## URLs In Manual Mode

- Frontend: `http://localhost:3000`
- API Gateway: `http://localhost:5000`
- Swagger: `http://localhost:5000/api/docs`
- OpenAPI YAML: `http://localhost:5000/api/docs/swagger.yaml`
- OpenAPI JSON: `http://localhost:5000/api/docs/swagger.json`

## If Something Fails

Check these first:

- PostgreSQL is running on `5432`
- Database name is `femcs_db`
- User is `postgres`
- Password is `postgres`
- The root Docker `.env` uses `SMTP_*`
- The local per-service `.env` files can use `MAIL_*`
- `FRONTEND_URL` can be a comma-separated allowlist such as `http://localhost:3000,http://localhost:5000`
- No other app is already using ports `3000`, `5000`, `5001`, `5002`, `5003`, `5004`, `5005`, or `5432`

## Fix For `password authentication failed for user "postgres"`

If you see:

```text
password authentication failed for user "postgres"
code: '28P01'
```

then your PostgreSQL server is running, but the local database credentials do not match this project.

This project expects:

- user: `postgres`
- password: `postgres`
- database: `femcs_db`

### Option 1: Fix The Project `.env` Files To Match Your Existing PostgreSQL

If your local PostgreSQL uses a different password, change `DB_URL` in these files:

- [services/auth-service/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/auth-service/.env)
- [services/entry-service/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/entry-service/.env)
- [services/extinguisher-service/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/extinguisher-service/.env)
- [services/notification-service/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/notification-service/.env)
- [services/report-service/.env](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/services/report-service/.env)

Use this format:

```env
DB_URL=postgresql://YOUR_USER:YOUR_PASSWORD@localhost:5432/femcs_db
```

### Option 2: Reapply Schema, Migration, And Seed Data

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS
$env:PGPASSWORD='postgres'
psql -U postgres -d femcs_db -f schema.sql
psql -U postgres -d femcs_db -f migrate.sql
psql -U postgres -d femcs_db -f seed.sql
```

### Which Option Is Better

Use Option 1 if your local PostgreSQL password is not `postgres`.

Use Option 2 if the credentials are already correct and you just need to rebuild the tables and starter data.

## Why The Frontend Showed `ECONNREFUSED`

This frontend message:

```text
Could not proxy request /favicon.ico from localhost:3000 to http://localhost:5000/ ... ECONNREFUSED
```

does not mean the frontend is broken.

It means the React dev server is running, but the API gateway on `5000` is not available yet.

That usually happens when:

- `api-gateway` is not started
- `api-gateway` is started but downstream services are failing
- database failures prevent the backend chain from starting cleanly

## Known Safe Order

If you want the shortest answer:

1. Run PostgreSQL or `docker compose`
2. Start backend services first
3. Start `api-gateway`
4. Start `frontend`
5. Open `http://localhost:3000`

## Best Choice

If your goal is to avoid startup issues, use:

```powershell
cd C:\Users\RCA\ne_prep\NE_prep\restfull\FEMS
docker compose up --build
```

That is the safest run path for this project.
