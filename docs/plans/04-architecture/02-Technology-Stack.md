# Technology Stack

---
**Document ID:** ARCH-02  
**Version:** 2.0  
**Date:** 2025-11-28  
**Author:** Senior Technical Writer  
**Status:** Draft  
---

## 1. Overview
This document defines the comprehensive technology stack for OpusNode. The selection criteria prioritize **scalability**, **developer productivity**, and **interoperability** with existing educational ecosystems. The architecture is designed to support asynchronous AI processing and real-time collaboration.

## 2. Purpose
The purpose of this document is to:
1.  Standardize the development environment for all engineers.
2.  Ensure the chosen technologies support the key functional requirements (AI, Real-time, LTI).
3.  Mitigate technical risks associated with scaling and maintenance.

## 3. Terminology
| Term | Definition |
| :--- | :--- |
| **LTI (Learning Tools Interoperability)** | A standard protocol that allows OpusNode to integrate seamlessly with LMS platforms like Canvas and Blackboard. |
| **BullMQ** | A Node.js message queue based on Redis, used for handling asynchronous background jobs. |
| **Vector Database** | A database optimized for storing and querying high-dimensional vectors, essential for AI similarity search. |

## 4. Stack Summary

### 4.1 Backend & API
*   **Runtime:** Node.js (v20 LTS)
*   **Framework:** NestJS (TypeScript) - Chosen for its modular architecture and strict typing.
*   **Language:** TypeScript (Primary), Python (Secondary, for AI microservices).
*   **API Style:** REST (Standard endpoints) & GraphQL (Complex data fetching).

### 4.2 Frontend
*   **Framework:** Next.js 14 (App Router)
*   **Language:** TypeScript
*   **State Management:** Zustand (Client), TanStack Query (Server State).
*   **UI Library:** Tailwind CSS, Shadcn/UI (Radix Primitives).

### 4.3 Database & Storage
*   **Primary DB:** PostgreSQL (Relational Data: Users, Teams, Projects).
*   **Caching & Queues:** Redis (Session store, BullMQ job queues).
*   **Vector DB:** Pinecone or pgvector (AI Embeddings for matching).
*   **Object Storage:** AWS S3 (User uploads, Portfolio assets).

### 4.4 AI & Data Pipeline
*   **LLM Orchestration:** LangChain (Node.js/Python).
*   **Models:** OpenAI GPT-4o (Primary), Claude 3.5 Sonnet (Code Review), GPT-3.5-turbo (High volume tasks).
*   **Async Processing:** BullMQ workers for handling long-running AI tasks (e.g., Curriculum Generation).

## 5. Detailed Component Description

### 5.1 Asynchronous Job Queue (BullMQ)
To prevent AI latency from blocking the main thread, all heavy operations are offloaded to a job queue.
*   **Use Case:** When a user requests "Generate Curriculum," the API responds immediately with `202 Accepted`, and the job is processed in the background.
*   **Retry Logic:** Automatic retries with exponential backoff for failed AI API calls.

### 5.2 LTI Integration Layer
OpusNode must function as a tool *within* a university's LMS.
*   **Standard:** LTI 1.3 Advantage.
*   **Function:** Allows Single Sign-On (SSO) from Canvas/Moodle and grade pass-back (sending project scores back to the LMS gradebook).

## 6. Use Cases

### UC-01: AI Matching Execution
1.  **Trigger:** Admin clicks "Match Teams".
2.  **Backend:** NestJS pushes a `match_job` to Redis.
3.  **Worker:** Python microservice picks up the job, fetches vectors from Pinecone, runs the Genetic Algorithm, and writes results to PostgreSQL.
4.  **Frontend:** Updates via WebSocket when the job is complete.

## 7. Limitations & Constraints
*   **Cost:** High reliance on paid APIs (OpenAI, Pinecone) requires strict quota management.
*   **Complexity:** Managing a polyglot environment (Node.js + Python) adds DevOps overhead.
*   **Latency:** Real-time features depend on WebSocket stability; fallback polling is required for restrictive firewalls.

## 8. Conclusion
The chosen stack balances modern web development speed (Next.js/NestJS) with the robust computational needs of AI (Python/Vector DB). The inclusion of LTI and Async Queues ensures the platform is enterprise-ready and scalable from Day 1.


