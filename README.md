# Nyra AI Companion

Nyra is an AI companion application featuring a React Native / Expo frontend and a Node.js / Express backend. The project is organized as a monorepo holding the frontend client, backend API server, and shared common utilities.

## Features

Nyra provides multiple integrated modules to assist the user:

- **🔐 Authentication**: User sign-up and sign-in functionality utilizing JSON Web Tokens (JWT).
- **🛡️ Safety Module**: Features to ensure user physical safety, including:
  - SOS alerts
  - Emergency contacts management
  - Safe routing and tracking
  - Routine check-ins
  - Safety tips
- **🧘 Wellbeing Module**: Mood tracking and wellbeing summaries.
- **✅ Productivity Module**: Task management and to-do lists.
- **🤖 AI Module**: Direct AI chatbot interactions to serve as a companion.

## Project Architecture

The project is structured as a monolithic repository (monorepo) using npm workspaces.

- `/backend`: The Express Node.js API server, written in TypeScript. Hosts the core logic, routes, and an in-memory database mock for prototyping.
- `/client`: The React Native Expo application, presenting the user interface. It works across Android, iOS, and the Web.
- `/shared`: A shared dependency space containing unified TypeScript types, interfaces, and utilities that conform both client and backend.

## Prerequisites

- Node.js (v18 or v22+ recommended)
- npm (v7+ which natively supports workspaces)
- Expo CLI

## How to Run Locally

### 1. Install Dependencies
Run the installation script specifically from the **root** folder to correctly resolve all shared workspace dependencies:
```bash
npm install
```

### 2. Build Shared Library
Compile the common shared workspace logic before running the backend:
```bash
cd shared
npm run build
```

### 3. Start the Backend API
Navigate to the backend to start the Node server. It defaults to listening on `http://localhost:3000`.
```bash
cd backend
npm start
```

### 4. Start the Frontend Application
Navigate to the client and launch Expo. By default, you can press `w` in the CLI to open the web layout, which launches at `http://localhost:8081`. 
```bash
cd client
npx expo start --web
```

## Environment Variables

**Backend (`/backend/.env`)**
Requires some configuration secrets (example context):
- `PORT`: 3000
- `JWT_SECRET`: Your JSON Web Token encoding phrase
- `ENCRYPTION_KEY`: A 64-character long hex string used for securing sensitive interactions
