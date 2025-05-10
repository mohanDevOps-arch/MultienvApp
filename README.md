# Multi-Environment Ticket Management Application – Docker Deployment

This project is a multi-environment ticket management system consisting of:

- A **Flask development backend**
- A **Flask production backend**
- A **React frontend**
- A **MongoDB**

The entire application is containerized using **Docker** and orchestrated using **Docker Compose** to run seamlessly in isolated environments on your local machine.

---

## Task Overview

This project includes the following:

1. **Docker Configuration**
   - Dockerfiles for:
     - Development backend
     - Production backend
     - React frontend
   - Docker Compose configuration
   - Proper environment variable integration using `.env` files

2. **Application Deployment**
   - Install and use Docker & Docker Compose
   - Deploy all services using a single command
   - Ensure inter-service communication (Frontend ⇄ Backend ⇄ MongoDB)

---

## Docker Configuration

Each service has its own `Dockerfile`:

### Backend Development Dockerfile
```dockerfile
FROM python:3.10
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 3001
CMD ["python", "app.py"]


### 📦 Frontend Development Dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 3002
CMD ["python", "app.py"]

### Environment Configuration

MONGO_URI=mongodb://mongo:27017/devdb
REACT_APP_API_URL=http://localhost:5001

