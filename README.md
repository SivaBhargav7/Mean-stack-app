<<<<<<< HEAD
# MEAN Stack CRUD Application

A full-stack CRUD application built with the MEAN stack (MongoDB, Express, Angular 15, and Node.js). The application manages a collection of tutorials with create, read, update, and delete functionality, plus search capabilities.

## Features

- **Backend**: Node.js + Express REST API
- **Frontend**: Angular 15 with HTTP client
- **Database**: MongoDB
- **Docker**: Containerized deployment
- **CRUD Operations**: Create, Read, Update, Delete tutorials
- **Search**: Find tutorials by title
- **Published Status**: Track tutorial publication status

## Project Structure

```
├── backend/          # Node.js + Express API
├── frontend/         # Angular 15 application
├── docker-compose.yml # Docker orchestration
└── README.md         # This file
```

## Quick Start

### Option 1: Docker Deployment (Recommended)

1. **Docker Hub username** is already configured in `docker-compose.yml`:
   ```yaml
   image: sivabhargav/mean-backend:latest
   image: sivabhargav/mean-frontend:latest
   ```

2. **Build and run with Docker Compose**:
   ```bash
   docker-compose up --build
   ```

3. **Access the application**:
   - Frontend: http://localhost
   - Backend API: http://localhost/api
   - MongoDB: localhost:27017

### Option 2: Local Development

#### Backend Setup

```bash
cd backend
npm install
```

**Configure MongoDB**:
- Update `app/config/db.config.js` if needed
- Default: `mongodb://localhost:27017/meanapp`

**Start the server**:
```bash
npm start
# Server runs on http://localhost:8080
```

#### Frontend Setup

```bash
cd frontend
npm install
```

**Start the development server**:
```bash
ng serve --port 8081
# Application runs on http://localhost:8081
```

## API Endpoints

- `GET /api/tutorials` - Get all tutorials
- `GET /api/tutorials/:id` - Get tutorial by ID
- `POST /api/tutorials` - Create new tutorial
- `PUT /api/tutorials/:id` - Update tutorial
- `DELETE /api/tutorials/:id` - Delete tutorial
- `GET /api/tutorials?title=keyword` - Search tutorials by title
- `GET /api/tutorials/published` - Get published tutorials only

## Tutorial Model

```javascript
{
  id: String,
  title: String,
  description: String,
  published: Boolean,
  createdAt: Date,
  updatedAt: Date
}
```

## Environment Variables

### Backend
- `MONGO_URI`: MongoDB connection string (default: `mongodb://localhost:27017/meanapp`)
- `PORT`: Server port (default: 8080)

### Docker
- Backend container: Port 3000
- Frontend container: Port 80
- MongoDB container: Port 27017

## Troubleshooting

1. **CORS Issues**: Backend has CORS enabled for frontend communication
2. **Database Connection**: Ensure MongoDB is running and accessible
3. **Port Conflicts**: Check if ports 80, 8080, 8081, or 27017 are available
4. **Docker Issues**: Make sure Docker and Docker Compose are installed

## Development Notes

- Backend uses Express with Mongoose for MongoDB operations
- Frontend uses Angular 15 with Bootstrap for styling
- Docker setup includes nginx reverse proxy for API routing
- All CRUD operations are fully functional
- Search functionality works with partial title matching
=======
# Mean-stack-app
A Full stack MEAN app.
>>>>>>> 68c405d1789b7d264bbedff290a99cf0fef8de79
