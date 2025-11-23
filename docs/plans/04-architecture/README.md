# System Architecture & Technical Specifications

**Document:** TailCamp PRD - Architecture Overview  
**Version:** 1.1  
**Last Updated:** 2025-11-23

---

## Overview

This directory contains the technical specifications and architectural designs for the TailCamp platform. These documents serve as the blueprint for development, ensuring scalability, security, and maintainability.

## Documentation Map

| Document | Description | Audience |
|:---------|:------------|:---------|
| **[System Architecture](system-architecture.md)** | High-level overview of system layers, data flow, and component interactions. | All Engineers, Architects |
| **[Technology Stack](technology-stack.md)** | Detailed list of approved technologies, frameworks, and libraries. | All Engineers |
| **[Database Schema](database-schema.md)** | ER diagrams, table definitions, and indexing strategies for PostgreSQL. | Backend Engineers, DBAs |
| **[API Endpoints](api-endpoints.md)** | Specification of REST and GraphQL endpoints, including request/response formats. | Frontend & Backend Engineers |

## Key Architectural Decisions

1.  **Microservices for AI & Matching:** While the core backend is a monolithic NestJS application, the AI Engine and Matching Service are decoupled to allow for independent scaling and the use of Python-specific libraries.
2.  **Vector Database Integration:** A dedicated Vector DB (Milvus/Pinecone) is used alongside PostgreSQL to support semantic search and RAG (Retrieval-Augmented Generation) features.
3.  **Real-time First:** WebSocket integration is core to the architecture, not an afterthought, to support live collaboration in the Project Workspace.

## Related Sections

-   [Features Overview](../03-features/README.md)
-   [Security & Privacy](../09-security/security-privacy.md)
