# Task Manager Application

## Overview

This is a full-stack Task Manager application consisting of an ASP.NET Core Web API backend and a React frontend. The backend provides RESTful API endpoints for managing tasks, while the frontend offers a user-friendly interface to create, read, update, and delete tasks. Tasks are stored in-memory on the backend for simplicity.

The application demonstrates modern web development practices with a clean separation of concerns between the API and the UI.

## Features

- **Task Management**: Create, view, update, and delete tasks.
- **Task Filtering**: Filter tasks by status (all, active, completed).
- **Real-time Updates**: Changes are reflected immediately in the UI.
- **Error Handling**: Graceful error handling with user feedback.
- **Responsive Design**: Mobile-friendly interface using Tailwind CSS.
- **API Documentation**: Swagger UI for exploring API endpoints.
- **CORS Support**: Configured to allow requests from the React frontend.

## Tech Stack

### Backend
- **ASP.NET Core 8.0**: Web API framework.
- **C#**: Programming language.
- **Swagger/OpenAPI**: API documentation.
- **In-Memory Storage**: Simple data persistence (not suitable for production).

### Frontend
- **React 19**: UI library with hooks.
- **TypeScript**: Type-safe JavaScript.
- **Vite**: Build tool and development server.
- **Axios**: HTTP client for API calls.
- **Tailwind CSS**: Utility-first CSS framework.
- **ESLint**: Code linting.

## Prerequisites

Before running the application, ensure you have the following installed:

- **.NET 8.0 SDK**: Download from [Microsoft's official site](https://dotnet.microsoft.com/download/dotnet/8.0).
- **Node.js (v18 or later)**: Download from [nodejs.org](https://nodejs.org/).
- **npm or yarn**: Package manager (comes with Node.js).
- **Git**: For cloning the repository (optional).

## Installation

Follow these steps to set up the project locally:

### 1. Clone the Repository

```bash
git clone <repository-url>
cd Assignment1
```

### 2. Backend Setup

Navigate to the backend directory and restore dependencies:

```bash
cd backend/Taskmanagerapi
dotnet restore
```

### 3. Frontend Setup

Navigate to the frontend directory and install dependencies:

```bash
cd ../../frontend
npm install
```

## Running the Application

### Step-by-Step Guide

1. **Start the Backend API**:
   - Open a terminal and navigate to the backend directory:
     ```bash
     cd backend/Taskmanagerapi
     ```
   - Run the API:
     ```bash
     dotnet run
     ```
   - The API will start on `http://localhost:5006` (or another port if configured).
   - Access Swagger UI at `http://localhost:5006/swagger` to explore the API.

2. **Start the Frontend**:
   - Open a new terminal and navigate to the frontend directory:
     ```bash
     cd frontend
     ```
   - Run the development server:
     ```bash
     npm run dev
     ```
   - The frontend will start on `http://localhost:5173` (default Vite port).

3. **Access the Application**:
   - Open your browser and go to `http://localhost:5173`.
   - You should see the Task Manager interface.
   - The frontend will communicate with the backend API at `http://localhost:5006/api`.

4. **Stop the Applications**:
   - Press `Ctrl+C` in each terminal to stop the servers.

### Additional Commands

- **Backend**:
  - Build: `dotnet build`
  - Test: `dotnet test` (if tests are added)

- **Frontend**:
  - Build for production: `npm run build`
  - Preview production build: `npm run preview`
  - Lint: `npm run lint`

## API Endpoints

The backend exposes the following RESTful endpoints:

- **GET /api/tasks**: Retrieve all tasks.
- **POST /api/tasks**: Create a new task. Body: `{ "description": "string", "isCompleted": false }`
- **PUT /api/tasks/{id}**: Update an existing task. Body: `{ "description": "string", "isCompleted": boolean }`
- **DELETE /api/tasks/{id}**: Delete a task by ID.

### Example API Usage

Using curl:

```bash
# Get all tasks
curl -X GET "http://localhost:5006/api/tasks"

# Create a task
curl -X POST "http://localhost:5006/api/tasks" \
     -H "Content-Type: application/json" \
     -d '{"description": "New task", "isCompleted": false}'

# Update a task
curl -X PUT "http://localhost:5006/api/tasks/{id}" \
     -H "Content-Type: application/json" \
     -d '{"description": "Updated task", "isCompleted": true}'

# Delete a task
curl -X DELETE "http://localhost:5006/api/tasks/{id}"
```

## Project Structure

```
Assignment1/
├── backend/
│   └── Taskmanagerapi/
│       ├── Controllers/
│       │   └── TasksController.cs
│       ├── Models/
│       │   └── TaskItem.cs
│       ├── Services/
│       │   └── TaskService.cs
│       ├── Program.cs
│       ├── Taskmanagerapi.csproj
│       ├── appsettings.json
│       └── ...
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   │   ├── TaskForm.tsx
│   │   │   ├── TaskList.tsx
│   │   │   ├── TaskItem.tsx
│   │   │   └── TaskFilter.tsx
│   │   ├── services/
│   │   │   └── taskService.ts
│   │   ├── types/
│   │   │   └── index.ts
│   │   ├── App.tsx
│   │   ├── main.tsx
│   │   └── ...
│   ├── package.json
│   ├── vite.config.ts
│   └── ...
└── README.md
```

## Contributing

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/your-feature`.
3. Make your changes and commit: `git commit -m 'Add your feature'`.
4. Push to the branch: `git push origin feature/your-feature`.
5. Open a pull request.

## License

This project is licensed under the MIT License. See the LICENSE file for details.
