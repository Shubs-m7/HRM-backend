# 🏢 Web Agency HRM — Backend

### Scalable REST API backend for a modern Human Resource Management System.

<p align="center">
  <strong>Authentication • Employees • Projects • Tasks • Real-Time Events • Data Management</strong>
</p>

<p align="center">
  <a href="https://hrm-backend.vercel.app/">🚀 API Server</a>
  •
  <a href="https://github.com/Shubs-m7/HRM-backend">📦 Repository</a>
  •
  <a href="https://github.com/Shubs-m7/HRM-backend/issues">🐛 Issues</a>
</p>

<p align="center">

![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=for-the-badge\&logo=node.js\&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-5-black?style=for-the-badge\&logo=express)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=for-the-badge\&logo=typescript)
![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-47A248?style=for-the-badge\&logo=mongodb\&logoColor=white)
![Socket.IO](https://img.shields.io/badge/Socket.IO-Realtime-010101?style=for-the-badge\&logo=socket.io)
![JWT](https://img.shields.io/badge/JWT-Authentication-000000?style=for-the-badge\&logo=jsonwebtokens)

</p>

---

# 📌 Overview

**Web Agency HRM Backend** is the REST API and real-time server powering the Web Agency Human Resource Management System.

It provides the backend infrastructure required to manage:

* 👥 Users & employees
* 🔐 Authentication & authorization
* 📋 Tasks
* 📁 Projects
* 📊 HR-related data
* 📡 Real-time events
* 📎 File uploads
* 🗄️ Persistent application data

The backend is built with **Node.js, Express.js, TypeScript, MongoDB, and Mongoose**, with JWT-based authentication and Socket.IO for real-time communication.

---

# 🧠 System Architecture

```text
                    ┌──────────────────────┐
                    │     HRM Frontend     │
                    │ Next.js + React + TS │
                    └──────────┬───────────┘
                               │
                               │ HTTP / REST
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Express Server    │
                    │       Node.js        │
                    └──────────┬───────────┘
                               │
             ┌─────────────────┼─────────────────┐
             │                 │                 │
             ▼                 ▼                 ▼
       ┌───────────┐     ┌────────────┐    ┌────────────┐
       │Middleware │     │Controllers │    │ Socket.IO  │
       │           │     │            │    │   Events   │
       └─────┬─────┘     └─────┬──────┘    └────────────┘
             │                 │
             └─────────────────┘
                       │
                       ▼
                ┌──────────────┐
                │   Mongoose   │
                │     ODM      │
                └──────┬───────┘
                       │
                       ▼
                ┌──────────────┐
                │   MongoDB    │
                └──────────────┘
```

---

# 🚀 Core Capabilities

## 🔐 Authentication

Secure authentication infrastructure using:

* JSON Web Tokens
* Password hashing with bcrypt
* Authentication middleware
* Protected API routes
* User identity verification

### Authentication Flow

```text
User
 │
 │ Login
 ▼
POST /api/auth/login
 │
 ▼
Validate Credentials
 │
 ▼
bcrypt Password Check
 │
 ▼
Generate JWT
 │
 ▼
Client
 │
 │ Authorization Header
 ▼
Protected API
```

---

# 👥 User Management

The backend provides APIs for managing user records and profiles.

### Supported operations

* Create users
* Retrieve users
* Update users
* Delete users
* Retrieve profile information
* Authenticated user information

The current API exposes the `/api/users` module for CRUD and profile operations.

---

# 📋 Task Management

Tasks are handled through a dedicated API module.

### Supported functionality

* Create tasks
* Retrieve tasks
* Update tasks
* Delete tasks
* Update task status
* Associate tasks with projects/users

### Endpoint

```text
/api/tasks
```

The backend provides CRUD and task-status functionality for the frontend Kanban/task-management experience.

---

# 📁 Project Management

Projects are managed through a dedicated REST API.

### Endpoint

```text
/api/projects
```

Projects can serve as the organizational layer connecting:

```text
Project
   │
   ├── Team Members
   │
   ├── Tasks
   │
   ├── Progress
   │
   └── Activity
```

---

# 📡 Real-Time Communication

The backend integrates **Socket.IO** for real-time application events.

This provides the foundation for features such as:

* Live task updates
* Real-time notifications
* Employee activity
* Project updates
* Dashboard synchronization
* Collaborative workflows

```text
Client A
   │
   │ Socket Event
   ▼
┌───────────────┐
│   Socket.IO   │
│     Server    │
└───────┬───────┘
        │
        ├──────────────► Client B
        │
        ├──────────────► Client C
        │
        └──────────────► Client D
```

---

# 📎 File Uploads

The backend uses **Multer** for handling multipart file uploads.

This provides the foundation for uploading resources such as:

* Employee documents
* Profile images
* Project files
* HR documents
* Attachments

Uploaded resources are handled through the backend upload infrastructure.

---

# 🛡️ Validation & Error Handling

The API uses multiple layers of validation.

### Validation Stack

```text
Incoming Request
       │
       ▼
Route
       │
       ▼
Validation
 ┌─────┴─────┐
 │           │
Zod     Express Validator
 │           │
 └─────┬─────┘
       ▼
Controller
       │
       ▼
Business Logic
       │
       ▼
Database
```

The repository currently uses both **Zod and express-validator** for input validation.

---

# 🧰 Tech Stack

| Technology            | Purpose                 |
| --------------------- | ----------------------- |
| **Node.js**           | JavaScript runtime      |
| **Express.js**        | REST API framework      |
| **TypeScript**        | Static typing           |
| **MongoDB**           | Database                |
| **Mongoose**          | MongoDB ODM             |
| **JWT**               | Authentication          |
| **bcrypt**            | Password hashing        |
| **Zod**               | Schema validation       |
| **Express Validator** | Request validation      |
| **Socket.IO**         | Real-time communication |
| **Multer**            | File uploads            |

These technologies are reflected in the repository's current stack.

---

# 🏗️ Project Structure

```text
HRM-backend/
│
├── api/
│
├── src/
│   │
│   ├── controllers/
│   │   └── Request handling & business logic
│   │
│   ├── middleware/
│   │   ├── Authentication
│   │   ├── Authorization
│   │   └── Error handling
│   │
│   ├── models/
│   │   └── Mongoose schemas
│   │
│   ├── routes/
│   │   └── API route definitions
│   │
│   ├── scripts/
│   │   └── Database utilities & seeding
│   │
│   └── server.ts
│       └── Application entry point
│
├── dist/
│   └── Compiled JavaScript
│
├── uploads/
│   └── Uploaded files
│
├── .gitignore
├── package.json
├── package-lock.json
├── tsconfig.json
├── vercel.json
└── README.md
```

The repository currently follows a route/controller/model/middleware separation, with `src/server.ts` acting as the entry point.

---

# 🔄 Request Lifecycle

```text
HTTP Request
     │
     ▼
┌───────────────┐
│     Route     │
└───────┬───────┘
        │
        ▼
┌───────────────┐
│  Middleware   │
│               │
│ • Auth        │
│ • Validation  │
│ • Errors      │
└───────┬───────┘
        │
        ▼
┌───────────────┐
│  Controller   │
└───────┬───────┘
        │
        ▼
┌───────────────┐
│    Mongoose   │
└───────┬───────┘
        │
        ▼
┌───────────────┐
│    MongoDB    │
└───────┬───────┘
        │
        ▼
      JSON
    Response
```

---

# 📡 API Overview

## Authentication

```http
/api/auth
```

| Method | Endpoint    | Purpose               |
| ------ | ----------- | --------------------- |
| `POST` | `/register` | Register user         |
| `POST` | `/login`    | Authenticate user     |
| `GET`  | `/me`       | Retrieve current user |

---

## Users

```http
/api/users
```

| Operation | Purpose                 |
| --------- | ----------------------- |
| Create    | Create a user           |
| Read      | Retrieve users          |
| Update    | Modify user information |
| Delete    | Remove user             |
| Profile   | Retrieve/update profile |

---

## Tasks

```http
/api/tasks
```

| Operation | Purpose            |
| --------- | ------------------ |
| Create    | Create task        |
| Read      | Retrieve tasks     |
| Update    | Modify task        |
| Delete    | Remove task        |
| Status    | Update task status |

---

## Projects

```http
/api/projects
```

| Operation | Purpose           |
| --------- | ----------------- |
| Create    | Create project    |
| Read      | Retrieve projects |
| Update    | Modify project    |
| Delete    | Remove project    |

The current repository README documents these API modules and their primary purposes.

---

# ⚙️ Getting Started

## Prerequisites

Make sure you have:

* **Node.js 18+**
* **npm**
* **MongoDB**

MongoDB can run either:

* Locally
* MongoDB Atlas
* Another compatible MongoDB deployment

The repository currently specifies Node.js 18+ and a running MongoDB instance as prerequisites.

---

# 📥 Installation

Clone the repository:

```bash
git clone https://github.com/Shubs-m7/HRM-backend.git
```

Navigate into the project:

```bash
cd HRM-backend
```

Install dependencies:

```bash
npm install
```

---

# 🔐 Environment Variables

Create a `.env` file in the project root.

```env
PORT=5000

MONGODB_URI=mongodb://localhost:27017/hrm_db

JWT_SECRET=your_super_secret_jwt_key

CLIENT_URL=http://localhost:3000
```

### Environment Variables

| Variable      | Description               | Example                            |
| ------------- | ------------------------- | ---------------------------------- |
| `PORT`        | API server port           | `5000`                             |
| `MONGODB_URI` | MongoDB connection string | `mongodb://localhost:27017/hrm_db` |
| `JWT_SECRET`  | JWT signing secret        | `your_secret`                      |
| `CLIENT_URL`  | Frontend URL for CORS     | `http://localhost:3000`            |

These variables correspond to the configuration documented by the repository.

> ⚠️ Never commit `.env` files or production secrets to GitHub.

---

# ▶️ Running the Server

## Development

Run the development server with hot reload:

```bash
npm run dev
```

The API will be available at:

```text
http://localhost:5000
```

The current repository documents `npm run dev` as the development command and port `5000` as the default local API endpoint.

---

# 🗄️ Database Seeding

The project includes a database seeding command.

```bash
npm run seed
```

This can be used to verify the database connection and populate initial data.

---

# 🏭 Production

Build the TypeScript project:

```bash
npm run build
```

Then start the compiled server:

```bash
npm start
```

> Ensure production environment variables are configured before starting the application.

---

# ☁️ Deployment

The backend includes a Vercel configuration and has a deployed backend endpoint.

### Production API

[HRM Backend API](https://hrm-backend.vercel.app/?utm_source=chatgpt.com)

---

# 🔗 Frontend Integration

This backend is designed to work with the companion HRM frontend.

### Frontend

```text
Next.js
React
TypeScript
Tailwind CSS
Zustand
Axios
Socket.IO Client
```

### Backend

```text
Node.js
Express
TypeScript
MongoDB
Mongoose
JWT
Socket.IO
```

### Full Stack Architecture

```text
             ┌──────────────────────────┐
             │       HRM FRONTEND       │
             │                          │
             │ Next.js + React + TS     │
             └────────────┬─────────────┘
                          │
                 REST API / Socket.IO
                          │
                          ▼
             ┌──────────────────────────┐
             │       HRM BACKEND        │
             │                          │
             │ Node + Express + TS      │
             └────────────┬─────────────┘
                          │
                          ▼
             ┌──────────────────────────┐
             │         MongoDB          │
             │        Mongoose          │
             └──────────────────────────┘
```

---

# 🔐 Security Considerations

The backend incorporates several security mechanisms:

### Authentication

JWT-based authentication protects authenticated resources.

### Password Security

Passwords are hashed using bcrypt rather than stored as plaintext.

### Validation

Incoming data is validated before reaching business logic.

### CORS

The frontend origin can be configured through:

```env
CLIENT_URL=http://localhost:3000
```

### Secrets

Sensitive configuration is provided through environment variables.

---

# 📈 Scalability

The backend architecture is designed to allow additional HR modules to be introduced without rewriting the core server.

Potential modules include:

```text
HRM Backend
│
├── Authentication
├── Users
├── Employees
├── Attendance
├── Leave Management
├── Payroll
├── Projects
├── Tasks
├── Recruitment
├── Performance
├── Notifications
├── Documents
├── Reports
└── Analytics
```

---

# 🛣️ Roadmap

## Phase 1 — Core API

* [x] Express server
* [x] TypeScript
* [x] MongoDB integration
* [x] Mongoose models
* [x] JWT authentication
* [x] Password hashing
* [x] User APIs
* [x] Task APIs
* [x] Project APIs
* [x] Validation
* [x] Socket.IO integration
* [x] File upload infrastructure

## Phase 2 — HR Operations

* [ ] Employee management API
* [ ] Attendance API
* [ ] Leave management
* [ ] Payroll processing
* [ ] Payslip generation
* [ ] Employee documents

## Phase 3 — Advanced HR

* [ ] Recruitment pipeline
* [ ] Performance management
* [ ] Advanced reporting
* [ ] Notifications
* [ ] Audit logs
* [ ] Activity tracking

## Phase 4 — Enterprise

* [ ] Multi-tenant architecture
* [ ] Organization management
* [ ] Advanced RBAC
* [ ] API rate limiting
* [ ] Audit trails
* [ ] Background jobs
* [ ] Redis caching
* [ ] Advanced observability

---

# 🧪 API Development

For API testing and development, the backend can be used with tools such as:

* Postman
* Insomnia
* Thunder Client
* REST Client
* Frontend Axios integration

Example:

```http
POST /api/auth/login
Content-Type: application/json
```

```json
{
  "email": "user@example.com",
  "password": "password"
}
```

---

# 📊 Backend Responsibilities

```text
┌─────────────────────────────────────────────┐
│                 HRM BACKEND                 │
├─────────────────────────────────────────────┤
│                                             │
│  🔐 Authentication                          │
│  👥 User Management                         │
│  📋 Task Management                         │
│  📁 Project Management                      │
│  🗄️ Database Operations                     │
│  📡 Real-Time Communication                 │
│  📎 File Uploads                            │
│  🛡️ Validation & Middleware                 │
│  ⚠️ Error Handling                          │
│                                             │
└─────────────────────────────────────────────┘
```

---

# 💡 Engineering Highlights

This backend demonstrates practical implementation of:

* RESTful API design
* Express.js architecture
* TypeScript backend development
* MongoDB data modeling
* Mongoose ODM
* JWT authentication
* Password hashing
* Request validation
* Middleware architecture
* Controller/service separation
* Real-time communication
* File upload handling
* Database seeding
* Environment-based configuration
* Vercel deployment

---

# 🤝 Contributing

Contributions and improvements are welcome.

### Create a branch

```bash
git checkout -b feature/your-feature
```

### Make your changes

```bash
git add .
```

### Commit

```bash
git commit -m "feat: add your feature"
```

### Push

```bash
git push origin feature/your-feature
```

Then create a Pull Request.

---

# 🐛 Bug Reports

If you discover a bug, open an issue with:

* Bug description
* Steps to reproduce
* Expected behavior
* Actual behavior
* API endpoint
* Request payload
* Response
* Error logs
* Environment information

---

# 📄 License

This project is currently maintained as a personal/portfolio project.

If you intend to use this code commercially or redistribute it, please contact the repository owner first.

---

# 👨‍💻 Author

## Shubham Mulye

Full-Stack / Frontend Developer building modern web applications with:

**Next.js • React • TypeScript • Node.js • Express • MongoDB**

<p align="center">

<a href="https://github.com/Shubs-m7">
<img src="https://img.shields.io/badge/GitHub-Shubs--m7-181717?style=for-the-badge&logo=github" />
</a>

</p>

---

# ⭐ Support

If this project helped you or you found the architecture interesting, consider giving the repository a ⭐.

<p align="center">

### Built with Node.js + Express + TypeScript + MongoDB

**Web Agency HRM — One backend for people, projects, and operations.**

</p>
