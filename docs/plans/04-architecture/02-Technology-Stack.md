# Technology Stack

**Document:** TailCamp PRD - Technology Stack  
**Version:** 1.2  
**Last Updated:** 2025-11-23

---

## 1. Overview

This document specifies the technology choices for the TailCamp platform, organized by layer and purpose. All selections prioritize developer productivity, scalability, and alignment with modern best practices.

**Related Documents:**
- [01-System-Architecture](01-System-Architecture.md) - Overall system design
- [03-Database-Schema](03-Database-Schema.md) - Data models
- [05-CI-CD-Pipeline](05-CI-CD-Pipeline.md) - Development workflow

---

## 2. Frontend

### 2.1 Core Framework

| Technology | Version | Purpose |
|:-----------|:--------|:--------|
| **Next.js** | 14+ | React framework with SSR, API routes, file-based routing |
| **React** | 18+ | UI library for component-based architecture |
| **TypeScript** | 5+ | Type safety, improved developer experience |

### 2.2 State Management

-   **Recoil** or **Zustand** - Lightweight state management for client-side data
-   **TanStack Query (React Query)** - Server state management, caching, data fetching

### 2.3 UI & Styling

| Technology | Purpose |
|:-----------|:--------|
| **Tailwind CSS** | Utility-first CSS framework |
| **Radix UI** or **Headless UI** | Accessible, unstyled component primitives |
| **Framer Motion** | Animations and micro-interactions |

### 2.4 Real-Time Communication

-   **Socket.io Client** - WebSocket client for chat and collaboration features

---

## 3. Backend

### 3.1 Core Framework

| Technology | Version | Purpose |
|:-----------|:--------|:--------|
| **NestJS** | 10+ | Node.js framework with TypeScript, modular architecture |
| **Node.js** | 20+ LTS | JavaScript runtime |

### 3.2 API Layer

-   **GraphQL** (with Apollo Server) - Flexible querying for complex data relationships
-   **REST** - Simple CRUD operations, public API endpoints

### 3.3 Real-Time Features

-   **Socket.io Server** - WebSocket server for bidirectional communication
-   **Redis Pub/Sub** - Message broker for scaling WebSocket connections across servers

### 3.4 Background Jobs

-   **BullMQ** - Redis-backed job queue for async tasks (email sending, report generation)

---

## 4. AI Engine

### 4.1 Large Language Models (LLM)

| Provider | Model | Use Case |
|:---------|:------|:---------|
| **OpenAI** | GPT-4 | Primary model for assessment, curriculum generation |
| **Anthropic** | Claude 3.5 Sonnet | Fallback model, code review suggestions |
| **OpenAI** | GPT-3.5 Turbo | Cost-effective option for simple tasks |

### 4.2 Orchestration & Tooling

-   **LangChain (Python)** - LLM orchestration, prompt templates, chains
-   **LangGraph** - Stateful workflows for complex multi-step AI interactions
-   **LangSmith** - Prompt debugging and monitoring (optional)

### 4.3 Embeddings

-   **OpenAI text-embedding-3-large** - Generate vector embeddings for documents and code
-   **text-embedding-3-small** - Cost-effective option for less critical embeddings

### 4.4 Intent Classification (Optional)

-   **Fine-tuned BERT** or **DistilBERT** - Custom intent detection for chatbot interactions

---

## 5. Database & Storage

### 5.1 Primary Database

| Technology | Version | Purpose |
|:-----------|:--------|:--------|
| **PostgreSQL** | 16+ | Relational data, ACID compliance, JSONB support |

**Extensions:**
-   `pgvector` - Vector similarity search directly in PostgreSQL (alternative to dedicated vector DB)

### 5.2 Caching Layer

| Technology | Version | Purpose |
|:-----------|:--------|:--------|
| **Redis** | 7+ | Session storage, cache, rate limiting, job queue |

### 5.3 Vector Database

**Options:**
-   **Milvus** (self-hosted) - Open-source, high performance, lower cost
-   **Pinecone** (managed) - Ease of use, managed service, higher cost

**Decision:** Start with **Milvus** for cost control, migrate to Pinecone if operational burden is high.

### 5.4 Graph Database (Optional, Post-MVP)

-   **Neo4j** - Prerequisite relationships, learning path dependencies

### 5.5 File Storage

-   **AWS S3** - User uploads, portfolio files, static assets
-   **CloudFront CDN** - Fast delivery of static content globally

---

## 6. DevOps & Infrastructure

### 6.1 Hosting

| Component | Provider | Rationale |
|:----------|:---------|:----------|
| **Frontend** | Vercel | Optimized for Next.js, edge functions, automatic deployments |
| **Backend** | AWS ECS or Fly.io | Container-based deployment, easy scaling |
| **Database** | AWS RDS (PostgreSQL) | Managed database, automated backups |
| **Redis** | AWS ElastiCache or Upstash | Managed Redis, global replication |

### 6.2 CI/CD

-   **GitHub Actions** - Automated testing, builds, deployments
-   **Docker** - Containerization for consistent environments

### 6.3 Monitoring & Observability

| Tool | Purpose |
|:-----|:--------|
| **Sentry** | Error tracking, performance monitoring |
| **DataDog** or **New Relic** | Infrastructure monitoring, APM, log aggregation |
| **Mixpanel** or **Amplitude** | Product analytics, user behavior tracking |

### 6.4 Security

-   **AWS Secrets Manager** - API keys, database credentials
-   **Let's Encrypt** - SSL/TLS certificates (auto-renewal via Certbot)

---

## 7. Testing

### 7.1 Testing Frameworks

| Type | Tool | Purpose |
|:-----|:-----|:--------|
| **Unit** | Jest | Test individual functions, pure logic |
| **Component** | React Testing Library | Test React components in isolation |
| **Integration** | Supertest | Test API endpoints with database |
| **E2E** | Playwright | Test complete user flows in browser |

### 7.2 Code Quality

-   **ESLint** - JavaScript/TypeScript linting (Airbnb style guide)
-   **Prettier** - Code formatting (auto-format on save)
-   **Husky** - Git hooks for pre-commit linting and testing

---

## 8. Development Tools

### 8.1 Package Management

-   **npm** or **pnpm** - Dependency management (pnpm preferred for monorepo)

### 8.2 Monorepo (Optional)

-   **Nx** or **Turborepo** - Monorepo tooling if organizing multiple apps/packages

### 8.3 API Documentation

-   **Stoplight** or **Redoc** - Interactive API documentation from OpenAPI specs

---

## 9. Version Requirements

### Minimum Versions

| Technology | Minimum Version | Rationale |
|:-----------|:----------------|:----------|
| **Node.js** | 20 LTS | Latest stable features, long-term support |
| **PostgreSQL** | 16 | Performance improvements, JSONB enhancements |
| **Redis** | 7 | Redis Streams, better memory efficiency |
| **TypeScript** | 5+ | Modern type system features |
| **Next.js** | 14+ | App Router, Server Components |

---

## 10. Technology Decision Log

### Rationale for Key Choices

**Why Next.js over vanilla React?**
-   Built-in SSR/SSG for better SEO and performance
-   API routes for backend logic without separate server
-   File-based routing reduces boilerplate

**Why NestJS over Express?**
-   Built-in TypeScript support
-   Modular architecture scales better
-   Dependency injection simplifies testing

**Why PostgreSQL over MongoDB?**
-   Strong relational data (users, groups, projects)
-   ACID compliance for transactional integrity
-   JSONB provides flexibility for unstructured data

**Why Milvus over Pinecone initially?**
-   Lower cost for MVP (self-hosted)
-   Full control over data
-   Can migrate to Pinecone later if needed

---

**Next Step:** Review [03-Database-Schema](03-Database-Schema.md).


