# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a **Personal Finance API** built as a modular monolith using **NestJS**, **TypeScript**, **PostgreSQL**, **Redis**, **RabbitMQ**, and **MinIO** for file storage. The application provides comprehensive personal finance management features including expense tracking, income management, budgeting, financial goals, and notifications.

## Technology Stack

- **Framework**: NestJS (Node.js)
- **Language**: TypeScript
- **Database**: PostgreSQL with TypeORM
- **Caching**: Redis
- **Message Queue**: RabbitMQ
- **File Storage**: MinIO (S3-compatible)
- **Authentication**: Firebase Auth + JWT
- **Email**: Google App Mail / SendGrid
- **Documentation**: Swagger (available at `/api`)

## Development Commands

### Environment Setup
```bash
# Copy environment template
cp .env.example .env.dev

# Start required services (PostgreSQL, Redis, RabbitMQ, MinIO)
docker-compose --env-file .env.dev -f docker-compose.test.yml up --build
```

### Daily Development
```bash
# Install dependencies
npm install

# Development with watch mode (runs migrations automatically)
npm run start:dev

# Production development mode
npm run start:dev:prod

# Debug mode
npm run start:debug
```

### Build & Production
```bash
# Build the application (includes template copying)
npm run build

# Start production
npm run start:prod
```

### Testing
```bash
# Run unit tests
npm run test

# Run tests in watch mode
npm run test:watch

# Run tests with coverage
npm run test:cov

# Run e2e tests
npm run test:e2e

# Debug tests
npm run test:debug
```

### Database Operations
```bash
# Generate new migration
npm run typeorm:migration:generate -- MigrationName

# Create empty migration
npm run typeorm:migration:create -- MigrationName

# Run migrations
npm run typeorm:migration:run

# Revert last migration
npm run typeorm:migration:revert

# Seed database
npm run seed:run
```

### Code Quality
```bash
# Lint and fix code
npm run lint

# Format code
npm run format
```

### Testing & Setup Scripts
```bash
# Test Google OAuth setup
npm run test:google-oauth

# Test Firebase authentication
npm run test:firebase-auth

# Setup Google OAuth (get refresh token)
npm run setup:google-oauth

# Environment management
npm run env:create
npm run env:validate
npm run env:status
```

## Architecture Overview

### Module Structure
The application follows a **modular monolith** pattern where each feature is organized in its own module under `src/modules/`:

**Core Financial Modules:**
- `income/` - Income tracking and management
- `expenses/` - Expense tracking and categorization
- `budgets/` - Budget creation and monitoring
- `financial-goals/` - Financial goal setting and tracking
- `categories/` - Expense/income categorization
- `recurring-transaction/` - Recurring transaction management

**Infrastructure Modules:**
- `auth/` - Authentication (Firebase + JWT)
- `user/` - User management and profiles
- `notifications/` - Push and email notifications
- `upload-minio/` - File upload to MinIO
- `upload-firebase/` - File upload to Firebase Storage
- `rmq/` - RabbitMQ message queue integration
- `cache/` - Redis caching layer

**Supporting Modules:**
- `affiliate/` - Affiliate system (legacy)
- `transactions/` - General transaction handling
- `keep-alive/` - Health check endpoints

### Key Application Components

**Main Application (`src/main.ts`):**
- Swagger documentation setup at `/api`
- CORS configuration for multiple frontends
- Global interceptors (logging, transformation, caching)
- RabbitMQ microservice initialization
- Global validation and error handling

**App Module (`src/app.module.ts`):**
- Conditional service loading based on `SERVICE_TYPE`
- Redis cache configuration
- TypeORM database configuration
- Static file serving setup
- Module registration and dependency injection

### Database Architecture
- **TypeORM** with PostgreSQL
- Migration-based schema management
- Seeding system for initial data
- Entities distributed across feature modules

### Authentication Flow
- **Firebase Authentication** for client-side auth
- **JWT strategy** for API authentication
- User permissions and role-based access control
- Auth provider tracking (Google, Facebook, etc.)

### File Storage Strategy
- **MinIO** for primary file storage (S3-compatible)
- **Firebase Storage** as alternative
- Template file handling in `dist/` after build

### Message Queue Integration
- **RabbitMQ** for async processing
- Configurable queue consumers
- Microservice pattern for queue handling

## Environment Configuration

The application requires extensive environment configuration. Key sections include:

- **Application**: `NODE_ENV`, `PORT`, API keys
- **Database**: PostgreSQL connection details
- **Redis**: Cache server configuration
- **Firebase**: Both client and server-side config
- **Email Services**: Google App Mail or SendGrid
- **File Storage**: MinIO S3-compatible storage
- **Message Queue**: RabbitMQ connection details

## Development Notes

### Service Types
The application supports different service types via `SERVICE_TYPE` environment variable:
- `MainService` - Full application with scheduled tasks
- Other service types may have reduced functionality

### File Structure
- `src/migration/` - Database migrations
- `src/config/` - Configuration services
- `src/common/` - Shared utilities, interceptors, filters
- `scripts/` - Utility scripts for setup and testing
- `docs/` - Comprehensive documentation
- `translations/` - Internationalization files

### Docker Services
Required services run via Docker Compose:
- **PostgreSQL** (port 5432 → 6434)
- **Redis** (port 6379 → 7379)  
- **RabbitMQ** (AMQP: 5772, Management: 15772)
- **MinIO** (S3: 9000, Console: 9001)

### API Documentation
Swagger documentation is automatically generated and available at `http://localhost:4000/api/` when the application is running.