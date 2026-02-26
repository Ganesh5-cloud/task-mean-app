In this DevOps project, you will design, containerize, and deploy a **full-stack CRUD application** using the **MEAN stack (MongoDB, Express, Angular, and Node.js)**, fully automated with **Docker, Docker Compose, Nginx, and CI/CD**.

The backend is built using **Node.js and Express**, exposing RESTful APIs that interact with a **MongoDB** database.  
The frontend is developed using **Angular**, which communicates with the backend using **HttpClient**.

The entire application is deployed on an **Ubuntu virtual machine**, exposed through **port 80 only** using **Nginx as a reverse proxy**, and continuously deployed using **GitHub Actions**.

---

## Application Description

The application manages a collection of **tutorials**, where each tutorial contains:

- ID  
- Title  
- Description  
- Published status  

Users can perform the following operations:

- Create a tutorial  
- View all tutorials  
- View a tutorial by ID  
- Update a tutorial  
- Delete a tutorial  
- Search tutorials by title  

---

## Project Setup

### Backend (Node.js + Express)

Navigate to the backend directory:

```bash
 cd backend
 ## Install dependencies
    npm install
 ## Update MongoDB connection details in
    app/config/db.config.js
 ## The backend API runs on:
    http://localhost:8080/api

### frontend (Angular)

Navigate to the rontend directory:

```bash
  cd frontend 
## Install dependencies
    npm install
## Access the frontend at:
   http://localhost:80/

## Docker Setup
# Backend Dockerfile

The backend is containerized using Node.js Alpine image and exposes port 5000 for API access.

# Frontend Dockerfile

The Angular application is built using a multi-stage Docker build and served using Nginx.

## Docker Compose Deployment

Docker Compose is used to orchestrate the following services:

Frontend container

Backend container

MongoDB container

Nginx reverse proxy

All services run on a single Docker network, and only port 80 is exposed to users.

# Nginx Reverse Proxy

Nginx acts as a single entry point for the application:

/ → Frontend (Angular)

/api → Backend (Node.js API)

This ensures clean routing and centralized access

# CI/CD Pipeline

A CI/CD pipeline is implemented using GitHub Actions:

Triggered on push to the main branch

Builds updated Docker images for frontend and backend

Pushes images to Docker Hub

Connects to the Ubuntu VM via SSH

Pulls latest images

Restarts containers using Docker Compose

This enables fully automated deployments.

# Application Access
  http://<VM_PUBLIC_IP>


