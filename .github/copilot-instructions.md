# OpusNode (TailCamp) AI Coding Instructions

You are an expert AI developer working on **OpusNode (TailCamp)**, an AI-powered collaborative learning platform.
This project uses a **Microservices-ready Monolith** architecture.

## 1. Project Context & Architecture
- **Frontend:** Next.js 14 (App Router), TypeScript, Tailwind CSS, Shadcn/UI, Zustand/TanStack Query.
- **Backend:** NestJS (Main API), Python FastAPI (AI/Matching Microservice).
- **Database:** PostgreSQL (Core Data), Redis (Caching & BullMQ), Pinecone/pgvector (AI Embeddings).
- **Infrastructure:** AWS S3, Docker, LTI 1.3 Standard.
- **Documentation:** The source of truth is in `docs/plans/`. **ALWAYS** cross-reference these files before generating code.

## 2. Code Generation Guidelines

### Frontend (Next.js 14)
- **App Router:** Use the `app/` directory structure. Prefer **Server Components** by default. Use `'use client'` only for interactive components.
- **UI Components:** Use **Shadcn/UI** components. Do not reinvent UI elements.
- **Styling:** Use **Tailwind CSS** exclusively. Follow the "Trust Blue" (`#2563EB`) and "AI Violet" (`#7C3AED`) color palette.
- **Icons:** Use `lucide-react`.
- **State:** Use `zustand` for global client state and `tanstack-query` for server state.

### Backend (NestJS)
- **Modularity:** Organize code by feature modules (e.g., `AuthModule`, `ProjectModule`).
- **Validation:** Use `class-validator` and DTOs for all API inputs.
- **Async Processing:** Offload heavy AI/Matching tasks to **BullMQ** (Redis). Do not block the main thread.
- **API:** Follow REST standards as defined in `docs/plans/04-architecture/04-API-Endpoints.md`.

### AI & Data
- **Python Service:** Use FastAPI for the AI/Matching microservice.
- **Vector DB:** Use `pgvector` or Pinecone for embedding storage.
- **LLM:** Use LangChain for orchestration.

## 3. Critical Workflows
- **Documentation First:** If a feature is not fully defined in code, check `docs/plans/03-features/` or `docs/plans/04-architecture/`.
- **API Consistency:** Ensure implementation matches `docs/plans/04-architecture/04-API-Endpoints.md`.
- **Testing:** (Future) Write unit tests for all business logic using Jest (NestJS) and React Testing Library (Next.js).

## 4. Project-Specific Patterns
- **LTI Integration:** All LMS interactions must adhere to LTI 1.3 standards.
- **Microservices-Ready:** Write the NestJS monolith with clear boundaries so modules can be extracted into microservices later.
- **Error Handling:** Use standard HTTP status codes and the error response format defined in `04-API-Endpoints.md`.

## 5. File Structure (Planned)
```
/apps
  /web (Next.js)
  /api (NestJS)
  /ai-service (Python)
/packages
  /ui (Shared UI)
  /database (Prisma/TypeORM)
/docs (Project Plans)
```
