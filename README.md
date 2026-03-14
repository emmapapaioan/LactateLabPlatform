# Lactate Lab

**Lactate Lab** is a cloud-based web application for **managing and analyzing lactate testing data** for endurance athletes.

The platform allows coaches to record lactate tests, analyze physiological thresholds (**LT1 / LT2**), generate training zones, and share results with athletes through a **secure access code**.

Supported sports:

- 🚴 Cycling  
- 🏃 Running  
- 🏊 Swimming  

The project demonstrates **full-stack development, cloud architecture, data visualization, and sports performance analysis**.

---

## Core Functionality

### Coach Workflow

1. Create a **coach account**
2. Login to the platform
3. Create **athlete profiles**
4. Record **lactate tests**
5. Run **automatic analysis**
6. Provide **test feedback**

Each coach manages their own athletes and testing data.

---

### Athlete Access

Athletes **do not create accounts**.

When a coach creates an athlete profile the system generates a **unique athlete access code**.

Athletes can:

1. Enter the platform  
2. Select **“I am an athlete”**  
3. Enter their **access code**  
4. View their **test results and analysis**

Athlete access is **read-only**.

---

## Lactate Test System

Each lactate test consists of **multiple stages** defined by the coach.

For every stage the following data can be recorded:

- Stage number 
- Stage length  
- Power / Pace
- Lactate concentration 
- Heart Rate   

The system supports **any number of stages**, allowing flexible laboratory or field testing protocols.

---

## Lactate Curve Analysis

After entering stage data the system generates a **lactate curve** and performs automatic analysis.

### Threshold Detection

The application calculates:

- **LT1 — First Lactate Threshold**
- **LT2 — Second Lactate Threshold**

These thresholds are derived from the **lactate progression across stages**.

---

## Training Zone Calculation

Training zones are calculated using two methods.

### TrainingPeaks Method

Standard endurance training zones commonly used in coaching platforms.

### Lactate Threshold Method

Zones derived directly from the athlete’s **lactate curve and threshold values**.

This allows coaches to compare **different physiological interpretations of the test**.

---

## Data Visualization

Each test produces the following outputs.

### Lactate Curve Graph

Displays:

- Lactate progression per stage
- Workload vs lactate relationship
- LT1 and LT2 threshold points

### Stage Data Table

Structured overview of the recorded test:

| Stage | Length | Power / Pace | Lactate | Heart Rate |
|-------|--------|--------------|---------|------------|

### Coach Feedback

Each test includes a **coach feedback section** where the coach can write:

- Performance interpretation  
- Training recommendations  
- Observations from the test  

Athletes can view this feedback when accessing their results.

---

## System Architecture

The application follows a **separated frontend / backend architecture** deployed on **Google Cloud**.

```

Client Browser
│
▼
Angular Frontend (Cloud Run)
│
▼
Node.js / Express API (Cloud Run)
│
▼
Google Firestore

```

---

## Technology Stack

### Frontend

- **Angular 21**
- Angular Material
- Angular Signals
- Standalone APIs
- Route Guards
- HTTP Interceptors

Responsibilities:

- User interface
- Graph visualization
- Access flow handling

---

### Backend

- **Node.js**
- **Express**
- REST API architecture

Responsibilities:

- Authentication
- Athlete management
- Test storage
- Analysis calculations
- Access control

---

### Database

**Google Firestore (Native Mode)**

Stores:

- Coaches
- Athletes
- Lactate tests
- Stage data
- Analysis results

---

## Cloud Infrastructure

The application is **fully containerized** and deployed on **Google Cloud Platform**.

### Cloud Run

Two independent services:

| Service | Purpose |
|------|------|
| Frontend Service | Serves Angular application |
| Backend Service | Node.js REST API |

### Artifact Registry

Stores **Docker images** used for Cloud Run deployments.

### Monitoring

Google Cloud services used:

- **Cloud Logging**
- **Cloud Monitoring**

Used to track:

- Requests
- Errors
- Service latency
- Application logs

---

## Security Model

The platform implements two access levels.

### Coaches

- Account required
- Full data management access

### Athletes

- Access via **unique athlete code**
- **Read-only access**

Athletes cannot modify or create data.

---

## Example Test Flow

```

Coach creates athlete
│
▼
Athlete receives unique code
│
▼
Coach records lactate test
│
▼
Coach runs analysis
│
▼
System calculates LT1 / LT2
│
▼
Athlete views results

```

---

## Development Tools

- Angular CLI  
- Node.js  
- Docker  
- Google Cloud SDK (`gcloud`)  
- Cloud Shell  

---

## Project Goals

This project demonstrates:

- Full-stack web development  
- Cloud-native architecture  
- Containerized deployment  
- Secure access control  
- Data visualization  
- Sports physiology analysis  

The system is a **fully functional production-style application**, not a demo scaffold.

---

## Contact

For access, a walkthrough, or a demo:

**Email**  
emmapapaioannou@outlook.com  

**GitHub**  
https://github.com/emmapapaioan  

**LinkedIn**  
https://www.linkedin.com/in/emma-papaioannou-49b770153
