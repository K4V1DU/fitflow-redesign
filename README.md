# FitFlow Redesign

This repository holds the work for the FitFlow redesign project, done as part of the IT3060 Human Computer Interaction case study. FitFlow is a fitness tracking app that was losing users, and this project works through the full process of researching the problem, picking a technology stack, and planning out the architecture for a redesign.

## What's in here

- `frontend` - the mobile and web app
- `backend` - the core API server
- `ai-service` - the AI service for workout recommendations and food recognition
- `docs` - all the write ups and diagrams from the project

## Chosen Tech Stack

- Frontend: React Native (mobile) and React (web)
- Backend: Node.js with Express
- AI Service: Python with FastAPI and TensorFlow Lite
- Database: PostgreSQL, with Firebase Firestore for real time features
- Authentication: Firebase Auth
- Caching: Redis

The reasoning behind each of these choices is in the `docs` folder.

## Documentation

- [Frontend Comparison](docs/activity1-frontend-comparison.md)
- [Backend, Database and Authentication Comparison](docs/activity2-backend-db-auth-comparison.md)
- [Technology Comparison Matrix](docs/comparison-matrix.md)
- [Architecture Diagram](docs/architecture-diagram.png)
- [Architecture Decision Record](docs/adr.md)


