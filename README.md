# Grain Quality Analyzer

An AI + IoT grain intelligence platform built to help storage operators, mandis, and agri teams monitor grain quality in real time, generate quality reports, and get decision support for pricing, shelf life, and advisory workflows.

## Why This Project Stands Out

This project goes beyond a basic dashboard. It combines live hardware signals, computer-assisted grain capture, backend AI orchestration, and a modern analytics UI into one end-to-end system:

- Real-time monitoring of moisture, humidity, and temperature
- Grain purity grading with impurity breakdowns
- MQTT-driven camera capture and device communication
- AI-backed price prediction, shelf-life estimation, and advisory generation
- Searchable historical reports with downloadable PDF exports
- Farmer-facing multilingual assistant with image upload support
- Dockerized local deployment with MongoDB, Redis, and Mosquitto

## Product Snapshot

The repository currently contains the full application inside:

`Ai-based-grain-quality-analyzer-and-disease-detection/`

Core modules:

- `frontend/`: React + Vite dashboard and operator UI
- `Backend/`: Express API, Socket.IO server, MQTT integration, report generation, and Python agent orchestration
- `hardware_automation/`: hardware-side automation code
- `Edge_models/`: model assets and edge inference artifacts

## Architecture

```text
Sensors / Camera / ESP32
        |
        v
   MQTT Broker (Mosquitto)
        |
        v
Backend API (Express + Socket.IO)
        |
        +--> Redis stream/cache
        +--> MongoDB reports
        +--> Python AI agents
                - price prediction
                - shelf-life estimation
                - advisory generation
        |
        v
Frontend Dashboard (React + TypeScript)
```

## Tech Stack

### Frontend

- React 19
- TypeScript
- Vite
- Tailwind CSS
- Framer Motion
- TanStack Query
- MQTT over WebSockets
- Socket.IO client

### Backend

- Node.js
- Express
- Socket.IO
- MongoDB + Mongoose
- Redis
- MQTT
- PDFKit

### AI / Automation

- Python agents for inference workflows
- Shelf-life and pricing logic
- Advisory generation pipeline
- Edge model artifacts for grain analysis

### Infrastructure

- Docker
- Docker Compose
- Eclipse Mosquitto

## Key Features

### 1. Real-Time Grain Monitoring

Live sensor values are streamed into the system and surfaced through a production-style dashboard for operators. The UI highlights risk states, trendlines, and current conditions for temperature, humidity, and moisture.

### 2. Quality and Purity Analysis

The platform transforms scan data into business-friendly outputs such as purity percentage, grade classification, and impurity composition. This makes it easier to standardize quality checks across batches.

### 3. AI-Driven Decisions

The backend runs Python agents in parallel to enrich each report with:

- Estimated market price
- Shelf-life prediction
- Storage and selling advisory

### 4. Reporting Workflow

Each analysis is saved, searchable, and exportable as a PDF. This helps create an auditable record for operations, quality control, and downstream sharing.

### 5. Kisan Sahayak

The project also includes a conversational assistant that accepts text and optional image input, designed to make the system more accessible for Hindi- and English-speaking users.

## Repository Structure

```text
Ai-based-grain-quality-analyzer-and-disease-detection/
|-- Backend/
|   |-- src/
|   |-- agents/
|   |-- scripts/
|   |-- tests/
|   `-- Dockerfile
|-- frontend/
|   |-- client/
|   |-- server/
|   |-- shared/
|   `-- Dockerfile
|-- hardware_automation/
|-- Edge_models/
|-- docker/
`-- docker-compose.yml
```

## Local Setup

### Option 1: Run with Docker

From the project folder:

```bash
cd Ai-based-grain-quality-analyzer-and-disease-detection
docker compose up --build
```

Services:

- Frontend: `http://localhost:5173`
- Backend: `http://localhost:5000`
- MongoDB: `mongodb://localhost:27017`
- Redis: `redis://localhost:6379`
- Mosquitto MQTT: `mqtt://localhost:1883`

### Option 2: Run Services Manually

Backend:

```bash
cd Ai-based-grain-quality-analyzer-and-disease-detection/Backend
npm install
pip install -r requirements.txt
npm run dev
```

Frontend:

```bash
cd Ai-based-grain-quality-analyzer-and-disease-detection/frontend
npm install
npm run dev
```

## Environment Configuration

### Backend

Typical backend variables:

```env
PORT=5000
FRONTEND_URL=http://localhost:5173
MONGO_URI=mongodb://localhost:27017/grain_quality
REDIS_URL=redis://localhost:6379
MQTT_BROKER_URL=mqtt://localhost:1883
MQTT_TOPIC_SENSOR=grain/sensor/data
MQTT_TOPIC_TRIGGER=grain/camera/trigger
MQTT_TOPIC_STATUS=grain/camera/status
MQTT_TOPIC_IMAGE=grain/camera/image
AI_TIMEOUT_MS=8000
HUGGINGFACEHUB_API_TOKEN=
HF_TOKEN=
HF_TOKEN_ADVISORY=
ADVISORY_MODEL_NAME=meta-llama/Llama-3.2-3B-Instruct
```

### Frontend

```env
VITE_API_URL=http://localhost:5000/api
VITE_SOCKET_URL=http://localhost:5000
VITE_MQTT_BROKER_URL=ws://localhost:9001
VITE_MQTT_TOPIC_STATUS=grain/camera/status
VITE_MQTT_TOPIC_IMAGE=grain/camera/image
VITE_MQTT_TOPIC_RESULT=grain/quality/result
```

## Available Scripts

### Backend

- `npm run dev` - start backend in development mode
- `npm start` - start backend in production mode
- `npm test` - run backend tests

### Frontend

- `npm run dev` - start Vite dev server
- `npm run build` - build production assets
- `npm run start` - run built frontend server
- `npm test` - run frontend service tests

## Recruiter Notes

This project demonstrates practical full-stack engineering across multiple domains:

- System design across frontend, backend, AI, and IoT layers
- Real-time data pipelines using MQTT and WebSockets
- Backend orchestration of multiple Python AI services
- Production-minded developer experience with Docker and automated tests
- A UX layer that translates technical data into operational decisions

If you are reviewing this repository as a hiring manager or recruiter, the strongest signal here is not just model usage, but the integration of hardware, data pipelines, APIs, AI services, and a polished operator interface into one working product.

## Status

This repository is being organized for GitHub publication. Some generated local folders may still exist in the working directory, but the root `.gitignore` now prevents them from being committed.
