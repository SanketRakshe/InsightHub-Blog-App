
---

# InsightHub Blog App Backend

Welcome to the **InsightHub Blog App** backend repository! This project serves as the backend for a blogging application, utilizing a stack built with **Cloudflare Workers** as the serverless backend, **Prisma ORM** for database management, and **TypeScript**. This setup offers scalability, high performance, and efficient deployment in a serverless environment.

Deployed on:- https://backend.sanketrakshe11.workers.dev

## Table of Contents

- [Tech Stack](#tech-stack)
- [Features](#features)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [API Routes](#api-routes)
- [Cloudflare Workers and Serverless Environment](#cloudflare-workers-and-serverless-environment)
- [Contributing](#contributing)
- [License](#license)

---

## Tech Stack

- **Frontend**: React
- **Backend**: Cloudflare Workers (Hono framework)
- **Validation**: Zod
- **Language**: TypeScript
- **ORM**: Prisma
- **Database**: Postgres
- **Authentication**: JWT

## Features

- User authentication (signup and signin)
- Blog CRUD operations
- API routes with secure authentication
- Modular code structure with separate route files
- Serverless deployment with Cloudflare Workers

---

## Getting Started

### Prerequisites

- **Node.js** (v14 or above)
- **npm** or **yarn** (for package management)
- **Cloudflare CLI (Wrangler)** for deployment
- **PostgreSQL** database

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/SanketRakshe/InsightHub-Blog-App.git
   cd insighthub-backend
   ```

2. **Initialize Project Backend**:
   Set up the project’s backend with Hono (Cloudflare Worker framework):
   ```bash
   mkdir blog-app
   cd blog-app
   npm create hono@latest
   ```
   - Choose `cloudflare-workers` template and install dependencies.

3. **Initialize Prisma and Database**:
   - Get a connection URL from your PostgreSQL provider.
   - Install and set up Prisma:
     ```bash
     npm install prisma
     npx prisma init
     ```
   - Update `.env` with your database connection details:
     ```plaintext
     DATABASE_URL="postgres://youruser:yourpassword@yourhost/dbname"
     ```

4. **Setup Environment Variables**:
   - Create a `wrangler.toml` file and add the `DATABASE_URL` and other necessary environment variables for Cloudflare Workers.

5. **Run Migrations**:
   ```bash
   npx prisma migrate dev --name init_schema
   ```

6. **Install Other Dependencies**:
   ```bash
   npm install @prisma/extension-accelerate zod
   ```

7. **Start Local Development**:
   To run the backend locally, use the following:
   ```bash
   npm start
   ```

8. **Deploy to Cloudflare**:
   To deploy your app:
   ```bash
   npm run deploy
   ```

---

## Environment Variables

To run this project, you’ll need to add the following environment variables to your `.env` file:

```plaintext
DATABASE_URL=postgres://your-db-connection
JWT_SECRET=your_jwt_secret_key
```

---

## API Routes

### User Routes

- `POST /api/v1/user/signup`: User signup, stores hashed password
- `POST /api/v1/user/signin`: User login, returns a JWT

### Blog Routes

- `POST /api/v1/blog`: Create a new blog post
- `PUT /api/v1/blog`: Update an existing blog post
- `GET /api/v1/blog/:id`: Get a specific blog post by ID
- `GET /api/v1/blog/bulk`: Get all blog posts

### Authentication Middleware

- The routes are protected with JWT authentication middleware, ensuring that only authenticated users can access certain endpoints (e.g., `/api/v1/blog/:id`, `/api/v1/blog`, etc.).

---

## Cloudflare Workers and Serverless Environment

The **InsightHub Blog App** backend leverages **Cloudflare Workers** as its serverless environment, enabling efficient, scalable, and globally distributed application hosting. The serverless nature of Cloudflare Workers removes the need for traditional servers, allowing the backend to automatically scale to handle any number of requests, reducing latency and cost.

For password hashing, this setup utilizes the **Web Crypto API** to securely hash user passwords. Authentication is managed using **JWT tokens**, ensuring secure and stateless communication across the backend.

> **Note:** Ensure that any sensitive credentials, such as database URLs and JWT secrets, are securely stored in environment variables and not committed to version control.

---

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/YourFeature`).
3. Make your changes.
4. Commit your changes (`git commit -m 'Add Your Feature'`).
5. Push to the branch (`git push origin feature/YourFeature`).
6. Open a pull request.

---

## License

Distributed under the MIT License. See `LICENSE` for more information.

---

## Additional Resources

- [Cloudflare Workers Documentation](https://developers.cloudflare.com/workers/)
- [Hono Documentation](https://hono.dev/)
- [Prisma Documentation](https://www.prisma.io/docs/)
- [Zod Documentation](https://zod.dev/)

---