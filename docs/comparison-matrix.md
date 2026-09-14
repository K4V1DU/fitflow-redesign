# FitFlow Redesign — Technology Comparison Matrix
### IT3060 – Human Computer Interaction | Activity 3

---

## 1. Purpose

This document consolidates the frontend, backend, database, and authentication comparisons from Activities 1 and 2 into a single weighted decision matrix. The goal is to objectively determine the most suitable technology stack for the FitFlow redesign, given its requirements: cross-platform delivery (iOS/Android/Web), AI-powered personalization, computer-vision nutrition logging, real-time social features, and strict health-data compliance (GDPR/CCPA).

---

## 2. Evaluation Criteria and Weights

Weights are assigned based on what matters most to FitFlow's success, out of a total of 100%.

| Criterion | Weight | Justification |
|---|---|---|
| Security & Compliance | 20% | FitFlow handles sensitive health and fitness data; GDPR/CCPA compliance is non-negotiable given prior data-privacy stakeholder concerns. |
| Performance | 15% | App previously lost users partly due to friction; smooth, responsive interactions are critical to retention. |
| Scalability | 15% | Social features, real-time notifications, and growing user base require infrastructure that scales without re-architecture. |
| AI/ML Integration | 15% | Core redesign value proposition (AI workout engine, computer-vision nutrition logging) depends on strong AI/ML support. |
| Development Speed | 15% | Startup needs to reach market quickly to reverse declining ratings and retention. |
| Cost | 10% | Mid-sized startup budget constraints. |
| Maintainability | 10% | Small-to-mid engineering team must sustainably maintain the codebase long-term. |
| **Total** | **100%** | |

Scoring scale: **1 (poor) – 5 (excellent)** per criterion, per option.

---

## 3. Frontend Framework Comparison

| Option | Security | Performance | Scalability | AI/ML | Dev Speed | Cost | Maintainability | **Weighted Score** |
|---|---|---|---|---|---|---|---|---|
| **React Native** | 3 | 4 | 4 | 4 | 5 | 4 | 4 | **3.95** |
| Flutter | 3 | 4 | 4 | 3 | 4 | 4 | 4 | 3.65 |
| Kotlin Multiplatform | 4 | 5 | 4 | 3 | 2 | 3 | 3 | 3.45 |
| Swift/SwiftUI (iOS-only) | 4 | 5 | 3 | 3 | 2 | 3 | 3 | 3.35 |

**Weighted score calculation example (React Native):**
`(3×0.20) + (4×0.15) + (4×0.15) + (4×0.15) + (5×0.15) + (4×0.10) + (4×0.10) = 3.95`

**Winner: React Native** — best balance of development speed, code reuse across iOS/Android, and mature AI/ML + real-time library support, despite Kotlin/Swift edging it out on raw native performance and security sandboxing.

---

## 4. Backend Framework Comparison

| Option | Security | Performance | Scalability | AI/ML | Dev Speed | Cost | Maintainability | **Weighted Score** |
|---|---|---|---|---|---|---|---|---|
| **Node.js / Express** | 3 | 4 | 4 | 3 | 5 | 4 | 4 | **3.75** |
| Python / FastAPI | 4 | 4 | 4 | 5 | 4 | 4 | 4 | 4.15 |
| Go | 4 | 5 | 5 | 2 | 2 | 4 | 3 | 3.65 |

**Winner: Python / FastAPI** scores highest overall due to superior native AI/ML ecosystem support (critical for the workout engine and computer vision), strong async performance, and solid security tooling. However, **Node.js/Express** remains attractive if the team wants a single JavaScript codebase across frontend and backend for faster onboarding — noted as a viable alternative below.

**Recommended approach:** Use **Node.js/Express** for the core API and real-time social/notification services (leveraging JS-everywhere efficiency), paired with a **Python/FastAPI AI microservice** for the workout engine and computer vision — giving the best of both without forcing a single-language compromise.

---

## 5. Database Comparison

| Option | Security | Performance | Scalability | AI/ML fit | Dev Speed | Cost | Maintainability | **Weighted Score** |
|---|---|---|---|---|---|---|---|---|
| **PostgreSQL** | 5 | 4 | 4 | 4 | 4 | 4 | 4 | **4.15** |
| MongoDB | 3 | 4 | 4 | 4 | 4 | 4 | 4 | 3.75 |
| Firebase (Firestore) | 3 | 4 | 4 | 3 | 5 | 3 | 4 | 3.65 |
| DynamoDB | 4 | 5 | 5 | 3 | 3 | 3 | 3 | 3.75 |

**Winner: PostgreSQL** — strongest fit for structured health/fitness data requiring relational integrity (users, workouts, nutrition logs), best security posture for compliance, with JSONB support covering flexible/unstructured needs (e.g., diary entries) without needing a separate NoSQL store for most cases. **Firebase Firestore/Realtime DB** is recommended as a *supplementary* store specifically for real-time social feed and notification data, where its low-latency sync is a strength PostgreSQL lacks natively.

---

## 6. Authentication & Authorization Comparison

| Option | Security | Performance | Scalability | Dev Speed | Cost | Maintainability | **Weighted Score*** |
|---|---|---|---|---|---|---|---|
| **Firebase Auth** | 4 | 4 | 4 | 5 | 4 | 5 | **4.29** |
| Auth0 | 5 | 4 | 4 | 4 | 3 | 4 | 4.14 |
| AWS Cognito | 4 | 4 | 5 | 3 | 4 | 3 | 3.86 |
| Supabase Auth | 4 | 4 | 4 | 4 | 4 | 4 | 4.00 |

*(AI/ML criterion excluded here as not applicable; remaining weights re-normalized proportionally.)*

**Winner: Firebase Auth** — fastest to implement, strong security defaults (OAuth, MFA support), low maintenance overhead, and integrates natively if Firebase is already used for real-time social features — a practical synergy for a mid-sized team.

---

## 7. Consolidated Recommended Stack

| Layer | Recommended Choice |
|---|---|
| **Frontend** | React Native (mobile) |
| **Backend (core API)** | Node.js + Express |
| **AI Microservice** | Python + FastAPI + TensorFlow Lite / cloud ML |
| **Primary Database** | PostgreSQL |
| **Real-time / Social Data** | Firebase (Firestore + Realtime features) |
| **Authentication** | Firebase Auth |
| **Caching** | Redis |

---

## 8. Rationale Summary

The scoring consistently favors a **hybrid, best-of-breed stack** rather than a single all-in-one platform. React Native delivers the fastest path to a unified iOS/Android experience without sacrificing performance for a fitness app's needs. Splitting the backend — Node.js for general API and real-time orchestration, Python/FastAPI for AI workloads — reflects the highest-weighted criteria (AI/ML support and development speed) better than forcing one language to do both jobs. PostgreSQL anchors the system for compliant, structured health data, while Firebase's real-time strengths are used selectively for social features and authentication, keeping development speed and cost low for a mid-sized team.

This consolidated stack directly carries forward into the Activity 4 system architecture design.
