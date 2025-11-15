# 🛠️ Technology Stack

**Document:** TailCamp PRD - Technology Stack  
**Version:** 1.0  
**Last Updated:** 2025-11-15

---

## 📋 Overview

TailCamp 개발에 사용되는 기술 스택의 상세 명세입니다.

**관련 문서:**
- [System Architecture](system-architecture.md) - 시스템 아키텍처
- [Database Schema](database-schema.md) - 데이터베이스 스키마

---

## 🎨 Frontend

### Core Framework
- **Next.js 14+** (App Router)
  - Server-Side Rendering (SSR)
  - Static Site Generation (SSG)
  - API Routes

### Language & Type Safety
- **TypeScript 5.0+**
  - Strict mode enabled
  - Type safety for all components

### State Management
- **Recoil** or **Zustand**
  - 선택 기준: 프로젝트 규모 및 팀 선호도
  - Recoil: 복잡한 상태 관리
  - Zustand: 간단하고 가벼운 상태 관리

### UI Library
- **Tailwind CSS 3.0+**
  - Utility-first CSS framework
  - Custom design system
- **shadcn/ui**
  - Component library
  - Accessible components

### Real-time Communication
- **Socket.io Client**
  - WebSocket connection
  - Real-time updates

### Data Visualization
- **Recharts** or **D3.js**
  - Recharts: React-friendly, 간단한 차트
  - D3.js: 복잡한 커스텀 시각화

---

## ⚙️ Backend

### Core Framework
- **NestJS**
  - Modular architecture
  - Dependency injection
  - TypeScript support

### Language
- **TypeScript**
  - Type safety
  - Better IDE support

### API
- **GraphQL (Apollo)**
  - Flexible queries
  - Type system
- **REST API**
  - Standard endpoints
  - RESTful principles

### Real-time
- **Socket.io**
  - WebSocket server
  - Real-time communication

### Task Queue
- **Bull (Redis-based)**
  - Job queue management
  - Background processing

### Scheduler
- **Temporal.io**
  - Workflow orchestration
  - Reliable scheduling

---

## 🤖 AI Engine

### LLM
- **OpenAI GPT-4**
  - Primary model
  - High accuracy
- **Anthropic Claude 3.5**
  - Alternative model
  - Fallback option
- **GPT-3.5**
  - Cost-effective fallback

### Orchestration
- **LangChain**
  - LLM orchestration
  - Prompt management
- **LangGraph**
  - Complex workflows
  - State management

### Embedding
- **OpenAI text-embedding-3-large**
  - Vector embeddings
  - High dimensionality

### Intent Classification
- **Fine-tuned BERT** or similar
  - Intent detection
  - Classification tasks

---

## 💾 Database

### Primary Database
- **PostgreSQL 15+**
  - Relational data
  - ACID compliance
  - JSONB support

### Cache
- **Redis 7+**
  - Session storage
  - Cache layer
  - Queue management

### Vector Database
- **Milvus** or **Pinecone**
  - Vector search
  - Similarity matching
  - Embedding storage

### Graph Database (Optional)
- **Neo4j**
  - Prerequisite relationships
  - Graph queries

---

## ☁️ Infrastructure

### Hosting
- **AWS** or **Vercel**
  - AWS: Full control, scalability
  - Vercel: Next.js optimized

### File Storage
- **AWS S3**
  - File uploads
  - Static assets
  - Portfolio files

### CI/CD
- **GitHub Actions**
  - Automated testing
  - Deployment pipeline
  - Code quality checks

### Monitoring
- **Sentry**
  - Error tracking
  - Performance monitoring
- **DataDog**
  - Infrastructure monitoring
  - Log aggregation

---

## 🔧 Development Tools

### Package Manager
- **npm** or **yarn**
  - Dependency management

### Code Quality
- **ESLint**
  - Code linting
- **Prettier**
  - Code formatting
- **TypeScript**
  - Type checking

### Testing
- **Jest**
  - Unit testing
- **React Testing Library**
  - Component testing
- **Playwright**
  - E2E testing

---

## 📊 Version Requirements

### Minimum Versions
- Node.js: 20+
- PostgreSQL: 15+
- Redis: 7+
- npm/yarn: Latest stable

---

## 🔗 관련 문서

- [System Architecture](system-architecture.md) - 시스템 아키텍처
- [Database Schema](database-schema.md) - 데이터베이스 스키마
- [API Endpoints](api-endpoints.md) - API 엔드포인트

---

**다음 단계:** [Database Schema](database-schema.md) 또는 [API Endpoints](api-endpoints.md) 확인

