# 🧪 Lactate Lab


https://github.com/user-attachments/assets/8bd80d48-ce0c-4161-9d51-43abbd352f35


Lactate Lab is a **private web application** used to manage lactate test data and perform basic performance analysis for cycling training.

The application is built with **Angular 21**, a **Node.js/Express backend**, and is deployed on **Google Cloud Run** using **Docker**.

The system is intentionally **access-restricted** and uses **Google Cloud IAM** for backend authorization.

---

## 📌 Application Overview

- **Frontend:** Angular 21 (standalone APIs, Angular Material)
- **Backend:** Node.js with Express
- **Database:** Google Firestore (Native mode)
- **Deployment:** Docker containers on Google Cloud Run
- **Access Control:** Google Cloud IAM (backend)
- **State Handling:** Angular signals, route guards, HTTP interceptors

---

## ☁️ Google Cloud Architecture

### 🖥️ Frontend Deployment (Angular)

**Cloud Run**
- Service name: `lactate-lab-service`
- Region: `europe-west1`
- Purpose: Serves the Angular application over HTTPS
- Authentication: `allow-unauthenticated`
- Port: `8080`
- Scaling: Fully managed by Cloud Run

**Artifact Registry**
- Repository: `lactate-lab-images`
- Region: `europe-west1`
- Image: Angular frontend Docker image

**Custom Domain**
- Domain: `andreopouloscoaching-lactatelab.com`
- Mapping: Cloud Run domain mapping
- SSL: Automatically managed by Google
- Load Balancing: Google global HTTP(S) load balancing (implicit via Cloud Run)

---

### 🔧 Backend Deployment (Node.js / Express)

**Cloud Run**
- Service name: `lactate-lab-backend-service`
- Region: `europe-west1`
- Purpose: REST API for data storage and access validation
- Authentication: **Require authentication (IAM)**
- Port: `8080`
- Runtime: Dockerized Node.js application

**Backend Endpoints**
- `GET /access-check` – IAM-protected access validation
- `GET /tests` – Fetch stored lactate tests
- `POST /tests` – Store new lactate test data

> If a request reaches the backend, access has already been approved by Google IAM.

---

## 🗄️ Database

**Firestore (Native Mode)**
- Mode: Native
- Collection: `tests`
- Usage: Stores lactate test data
- Access: Backend service account only

---

## 🔐 Access Control & IAM

### Backend Authorization
- Mechanism: Google Cloud IAM
- Role: `Cloud Run Invoker`
- Principals: Specific Google accounts only
- Frontend: Public
- Backend: Restricted

### Service Account
- Used by the backend to access Firestore
- Granted `roles/datastore.user`

### Local Development
- Uses a service account key via `GOOGLE_APPLICATION_CREDENTIALS`
- Production relies on Cloud Run’s attached service account

---

## 🧠 Frontend Access Handling

- Startup access check via `/access-check`
- Angular **signals** track access state
- **Route guards** block protected routes
- **HTTP interceptor** reacts to backend `403` responses
- Unauthorized users are redirected to `/private-access`

---

## 🐳 Docker & Deployment

- Frontend and backend are **separately Dockerized**
- Images built locally or via CI
- Images stored in **Artifact Registry**
- Deployed to **Cloud Run**
- No VM or server management required

---

## 📊 Monitoring & Logging

**Cloud Logging**
- Request logs
- Application logs (stdout / stderr)

**Cloud Monitoring**
- Cloud Run metrics (latency, requests, error rates)

---

## 🛠️ Development Tools

- Angular CLI
- Node.js
- Docker
- Google Cloud SDK (`gcloud`)
- Cloud Shell

---

## 🔒 Repository Access

This repository is **private**.

If you would like:
- Access to the source code
- A walkthrough of the architecture
- A demo video of the application

📩 **Contact:**
- **Email:** emmapapaioannou@outlook.com  
- **GitHub:** https://github.com/emmapapaioan  
- **LinkedIn:** https://www.linkedin.com/in/emma-papaioannou-49b770153  

---

## 📝 Notes

This project focuses on:
- Correct cloud architecture
- Clear separation of frontend and backend
- Real access control (IAM, not mock authentication)
- Production deployment practices

It is not a demo scaffold, but a working private system.
