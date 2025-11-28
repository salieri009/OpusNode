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
| **[01-System-Architecture](01-System-Architecture.md)** | High-level overview of system layers, data flow, and component interactions. | All Engineers, Architects |
| **[02-Technology-Stack](02-Technology-Stack.md)** | Detailed list of approved technologies, frameworks, and libraries. | All Engineers |
| **[03-Database-Schema](03-Database-Schema.md)** | ER diagrams, table definitions, and indexing strategies for PostgreSQL. | Backend Engineers, DBAs |
| **[04-API-Endpoints](04-API-Endpoints.md)** | Specification of REST and GraphQL endpoints, including request/response formats. | Frontend & Backend Engineers |
| **[05-CI-CD-Pipeline](05-CI-CD-Pipeline.md)** | CI/CD strategy, deployment workflows, and rollback procedures. | DevOps, Engineers |

## Key Architectural Decisions

1.  **Microservices for AI & Matching:** While the core backend is a monolithic NestJS application, the AI Engine and Matching Service are decoupled to allow for independent scaling and the use of Python-specific libraries.
2.  **Vector Database Integration:** A dedicated Vector DB (Milvus/Pinecone) is used alongside PostgreSQL to support semantic search and RAG (Retrieval-Augmented Generation) features.
3.  **Real-time First:** WebSocket integration is core to the architecture, not an afterthought, to support live collaboration in the Project Workspace.

## Related Sections

-   [Features Overview](../03-features/README.md)
-   [Security & Privacy](../09-security/01-Security-Privacy.md)
