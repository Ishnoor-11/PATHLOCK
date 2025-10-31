# Project Manager Application

A full-stack project management application built with ASP.NET Core Web API backend and React TypeScript frontend. This application allows users to manage projects, tasks, and includes a smart scheduler feature for efficient task allocation.

## Features

- **User Authentication**: JWT-based authentication with registration and login
- **Project Management**: Create, read, update, and delete projects
- **Task Management**: Manage tasks within projects with status tracking
- **Smart Scheduler**: Intelligent task scheduling and resource allocation using Kahn's algorithm for topological sorting and circular dependency detection
- **Responsive UI**: Modern React frontend with Tailwind CSS
- **API Documentation**: Swagger/OpenAPI documentation for backend APIs
- **Database**: SQLite database with Entity Framework Core

## Prerequisites

Before running this application, ensure you have the following installed:

- **.NET 8.0 SDK** (for backend)
  - Download from: https://dotnet.microsoft.com/download/dotnet/8.0
- **Node.js** (version 18 or higher, for frontend)
  - Download from: https://nodejs.org/
- **Git** (for cloning the repository)
  - Download from: https://git-scm.com/

## Installation

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd Assignment2
   ```

2. **Backend Setup:**
   - Navigate to the backend directory:
     ```bash
     cd backend/ProjectManagerApi
     ```
   - Restore NuGet packages:
     ```bash
     dotnet restore
     ```

3. **Frontend Setup:**
   - Navigate to the frontend directory:
     ```bash
     cd ../../frontend
     ```
   - Install npm dependencies:
     ```bash
     npm install
     ```

## Configuration

### Backend Configuration

1. **Database Configuration:**
   - The application uses SQLite by default. The database file will be created automatically in the backend directory.

2. **JWT Settings:**
   - Open `backend/ProjectManagerApi/appsettings.json`
   - Configure JWT settings (default values are provided for development):
     ```json
     {
       "JwtSettings": {
         "SecretKey": "your-super-secret-key-here-make-it-long-and-secure",
         "Issuer": "ProjectManagerApi",
         "Audience": "ProjectManagerApi"
       }
     }
     ```
   - **Important:** Change the `SecretKey` to a secure random string in production.

3. **CORS Configuration:**
   - CORS is configured in `Program.cs` to allow requests from:
     - `http://localhost:3000` (Create React App default)
     - `http://localhost:5173` (Vite default)
     - `https://your-app-name.vercel.app` (update this for production deployment)

### Frontend Configuration

1. **API Base URL:**
   - Open `frontend/src/services/api.ts`
   - Ensure the base URL points to your backend:
     ```typescript
     const API_BASE_URL = 'http://localhost:5074/api';
     ```

## Running the Application

### Backend

1. **Navigate to backend directory:**
   ```bash
   cd backend/ProjectManagerApi
   ```

2. **Run the application:**
   ```bash
   dotnet run
   ```

3. **Access the API:**
   - API will be available at: `http://localhost:5074`
   - Swagger documentation: `http://localhost:5074/swagger`

### Frontend

1. **Navigate to frontend directory:**
   ```bash
   cd frontend
   ```

2. **Start the development server:**
   ```bash
   npm run dev
   ```

3. **Access the application:**
   - Frontend will be available at: `http://localhost:5173`

### Running Both Services

To run both backend and frontend simultaneously:

1. **Terminal 1 (Backend):**
   ```bash
   cd backend/ProjectManagerApi
   dotnet run
   ```

2. **Terminal 2 (Frontend):**
   ```bash
   cd frontend
   npm run dev
   ```

## API Endpoints

The API provides the following main endpoints:

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login

### Projects
- `GET /api/projects` - Get all projects
- `POST /api/projects` - Create a new project
- `GET /api/projects/{id}` - Get project by ID
- `PUT /api/projects/{id}` - Update project
- `DELETE /api/projects/{id}` - Delete project

### Tasks
- `GET /api/tasks` - Get all tasks
- `POST /api/tasks` - Create a new task
- `GET /api/tasks/{id}` - Get task by ID
- `PUT /api/tasks/{id}` - Update task
- `DELETE /api/tasks/{id}` - Delete task

### Smart Scheduler
- `POST /api/scheduler/schedule` - Generate smart schedule

For detailed API documentation, visit the Swagger UI at `http://localhost:5074/swagger` when the backend is running.

## Building for Production

### Backend
```bash
cd backend/ProjectManagerApi
dotnet publish -c Release -o ./publish
```

### Frontend
```bash
cd frontend
npm run build
```

The built frontend files will be in the `dist` directory.

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Make your changes and commit: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a pull request

## Technologies Used

### Backend
- ASP.NET Core 8.0 Web API
- Entity Framework Core with SQLite
- JWT Authentication
- Swagger/OpenAPI
- CORS
- Kahn's Algorithm for topological sorting
- Circular dependency detection

### Frontend
- React 19
- TypeScript
- Vite
- Tailwind CSS
- Axios
- React Router DOM
- Framer Motion

## License

This project is licensed under the MIT License.
