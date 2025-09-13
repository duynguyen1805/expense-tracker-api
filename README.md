<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="200" alt="Nest Logo" /></a>
</p>

[circleci-image]: https://img.shields.io/circleci/build/github/nestjs/nest/master?token=abc123def456
[circleci-url]: https://circleci.com/gh/nestjs/nest

  <p align="center">A progressive <a href="http://nodejs.org" target="_blank">Node.js</a> framework for building efficient and scalable server-side applications.</p>
    <p align="center">
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/dm/@nestjs/common.svg" alt="NPM Downloads" /></a>
<a href="https://circleci.com/gh/nestjs/nest" target="_blank"><img src="https://img.shields.io/circleci/build/github/nestjs/nest/master" alt="CircleCI" /></a>
<a href="https://coveralls.io/github/nestjs/nest?branch=master" target="_blank"><img src="https://coveralls.io/repos/github/nestjs/nest/badge.svg?branch=master#9" alt="Coverage" /></a>
<a href="https://discord.gg/G7Qnnhy" target="_blank"><img src="https://img.shields.io/badge/discord-online-brightgreen.svg" alt="Discord"/></a>
<a href="https://opencollective.com/nest#backer" target="_blank"><img src="https://opencollective.com/nest/backers/badge.svg" alt="Backers on Open Collective" /></a>
<a href="https://opencollective.com/nest#sponsor" target="_blank"><img src="https://opencollective.com/nest/sponsors/badge.svg" alt="Sponsors on Open Collective" /></a>
  <a href="https://paypal.me/kamilmysliwiec" target="_blank"><img src="https://img.shields.io/badge/Donate-PayPal-ff3f59.svg"/></a>
    <a href="https://opencollective.com/nest#sponsor"  target="_blank"><img src="https://img.shields.io/badge/Support%20us-Open%20Collective-41B883.svg" alt="Support us"></a>
  <a href="https://twitter.com/nestframework" target="_blank"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow"></a>
</p>
  <!--[![Backers on Open Collective](https://opencollective.com/nest/backers/badge.svg)](https://opencollective.com/nest#backer)
  [![Sponsors on Open Collective](https://opencollective.com/nest/sponsors/badge.svg)](https://opencollective.com/nest#sponsor)-->

# Expense Tracker API

Tech stack **(NestJS, Typescript, Redis, MinIO, RabbitMQ and PostgreSQL, TypeORM)**

---

### Project Structure

The project follows a traditional **modular monolith** structure using NestJS modules.

Each feature is organized in its own module under `src/modules/`.

---

## Installation

### Prerequisites:

NodeJs version 20.x (20.18.1)

npm version 8.11.0

yarn version v1.22.22

```bash
$ npm install
```

## Running the app

Create .env.dev file with

```bash
# Application Configuration
NODE_ENV=development
PORT=4000
CLIENT_API_HOST=http://localhost:3000
APP_URL=http://localhost:4000
X_API_KEY=X_API_KEY
SERVICE_TYPE=MainService

LOGGING=all // boolean | "all" | ["query", "schema", "error", "warn", "info", "log", "migration"];

# JWT Configuration
JWT_SECRET='JWT_SECRET'

DOCKER_IMAGE_NAME=DOCKER_IMAGE_NAME
DOCKER_IMAGE_TAG=DOCKER_IMAGE_TAG

# POSTGRES LOCAL
DB_CONNECTION=postgres
DB_HOST=localhost
DB_PORT=5432
DB_USERNAME=postgres
DB_PASSWORD=123123
DB_DATABASE=personal-finance

# REDIS
REDIS_HOST=redis-server
REDIS_PORT=6379
REDIS_URL=redis://REDIS_HOST:REDIS_PORT

# EMAIL SERVICE
IS_SEND_EMAIL=true
SENDER_NAME=App Name
EMAIL_PROVIDER=GOOGLE_APP_MAIL

# SENDGRID
SENDGRID_API_KEY=test

# Google App Mail Configuration
GMAIL_USER=GMAIL_USER
GMAIL_CLIENT_ID=GMAIL_CLIENT_ID
GMAIL_CLIENT_SECRET=GMAIL_CLIENT_SECRET
GMAIL_REFRESH_TOKEN=GMAIL_REFRESH_TOKEN
GMAIL_ACCESS_TOKEN=GMAIL_ACCESS_TOKEN

# Minio Upload
STORAGE_LOCAL_ENDPOINT=minio-server
MINIO_UPLOAD_LOCAL_PORT=9000
USE_SSL=false
STORAGE_ENDPOINT=minio-server
MINIO_UPLOAD_PORT=9000
MINIO_UPLOAD_BUCKET_NAME=MINIO_UPLOAD_BUCKET_NAME
MINIO_UPLOAD_ACCESS_KEY=MINIO_UPLOAD_ACCESS_KEY
MINIO_UPLOAD_SECRET_KEY=MINIO_UPLOAD_SECRET_KEY

# RabbitMQ
RABBITMQ_USER=RABBITMQ_USER
RABBITMQ_PASSWORD=RABBITMQ_PASSWORD
RABBITMQ_HOST=rabbitmq
RABBITMQ_PORT=5772
RABBITMQ_URI=amqp://RABBITMQ_USER:RABBITMQ_PASSWORD@RABBITMQ_HOST:RABBITMQ_PORT

# Firebase Configuration (Frontend - Client-side)
NEXT_PUBLIC_FIREBASE_API_KEY=NEXT_PUBLIC_FIREBASE_API_KEY
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN
NEXT_PUBLIC_FIREBASE_PROJECT_ID=NEXT_PUBLIC_FIREBASE_PROJECT_ID
NEXT_PUBLIC_FIREBASE_APP_ID=NEXT_PUBLIC_FIREBASE_APP_ID
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET
NEXT_PUBLIC_FIREBASE_DATABASE_URL=NEXT_PUBLIC_FIREBASE_DATABASE_URL
NEXT_PUBLIC_FIREBASE_MEASUREMENT_ID=NEXT_PUBLIC_FIREBASE_MEASUREMENT_ID

# Firebase Configuration (Backend)
FIREBASE_PROJECT_ID=FIREBASE_PROJECT_ID
FIREBASE_PRIVATE_KEY_ID=FIREBASE_PRIVATE_KEY_ID
FIREBASE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\abc\n-----END PRIVATE KEY-----\n"
FIREBASE_CLIENT_EMAIL=FIREBASE_CLIENT_EMAIL
FIREBASE_CLIENT_ID=FIREBASE_CLIENT_ID
FIREBASE_AUTH_URI=https://accounts.google.com/o/oauth2/auth
FIREBASE_TOKEN_URI=https://oauth2.googleapis.com/token
FIREBASE_AUTH_PROVIDER_X509_CERT_URL=https://www.googleapis.com/oauth2/v1/certs
FIREBASE_CLIENT_X509_CERT_URL=FIREBASE_CLIENT_X509_CERT_URL
NEXT_PUBLIC_FIREBASE_DATABASE_URL=NEXT_PUBLIC_FIREBASE_DATABASE_URL

DISABLED_FEATURES=[SENTRY]
```

## 🐳 Running Required Services with Docker Compose

To run required services like **PostgreSQL**, **Redis**, **RabbitMQ**, and **MinIO**, use the included `docker-compose-test.yml`.

> 📦 Ensure you have Docker and Docker Compose installed.

---

### Step 1: Create `.env.dev` file

Make sure you have an `.env` or `.env.dev` file in your root directory:

```bash
cp .env.example .env.dev
```

Open `docker-compose.test.yml` and update the volume value as needed.

### Step 2: Start services

Run the following command to start all necessary services:

```bash
docker-compose --env-file .env.dev -f docker-compose.test.yml up --build
```

This will start the following services:

- Postgres (port: 5432)

- Redis (port: 7379)

- RabbitMQ: ( AMQP: 5772, Management UI: http://localhost:15772 )

- MinIO: ( S3 Endpoint: 9000, Console: http://localhost:9001 )

### Step 3: Run the application

In a new terminal window, start the app in development mode:

```bash
# development watch mode
$ npm run start:dev:all
```

### 📄 Swagger Documentation

Once the application is running, you can access it at:

Application: http://localhost:4000/

Check Swagger: http://localhost:4000/api/

## Support

Nest is an MIT-licensed open source project. It can grow thanks to the sponsors and support by the amazing backers. If you'd like to join them, please [read more here](https://docs.nestjs.com/support).

## Stay in touch

- Author - [Kamil Myśliwiec](https://kamilmysliwiec.com)
- Website - [https://nestjs.com](https://nestjs.com/)
- Twitter - [@nestframework](https://twitter.com/nestframework)

## License

Nest is [MIT licensed](LICENSE).
