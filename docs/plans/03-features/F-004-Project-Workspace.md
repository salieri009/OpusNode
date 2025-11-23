# F-004: Project Workspace

---
**Date:** 2025-11-23  
**Audience:** Product Manager, Full Stack Engineer, DevOps Engineer  
---

## 1. Overview

The **Project Workspace** is a collaborative environment where matched teams plan, execute, and deploy their projects. It integrates task management, version control (GitHub), and AI-driven coaching to facilitate a professional development workflow.

**Direct Quote:**
> "그룹 프로젝트 협업을 위한 워크스페이스입니다." ([Features Overview](README.md))

## 2. User Stories

- **US-4.1:** As a **team member**, I want to assign tasks to myself or others so that we know who is doing what.
- **US-4.2:** As a **developer**, I want to see my GitHub PR status directly in the workspace to track code reviews.
- **US-4.3:** As a **team**, we want an AI Coach to suggest technical stacks and review our architecture.

## 3. Functional Requirements (FR)

### FR-1: Task Management
- **FR-1.1:** The system shall provide a Kanban-style board for managing tasks (To Do, In Progress, Done).
- **FR-1.2:** Users shall be able to assign tasks, set due dates, and add labels.

### FR-2: GitHub Integration
- **FR-2.1:** The system shall authenticate users via GitHub OAuth.
- **FR-2.2:** The system shall automatically create a repository for the new group.
- **FR-2.3:** The workspace shall display real-time commit history and open Pull Requests.

### FR-3: AI Coach
- **FR-3.1:** The AI Coach shall analyze PRs and provide automated code review feedback.
- **FR-3.2:** The AI Coach shall answer technical questions related to the project's tech stack.

### FR-4: Real-time Collaboration
- **FR-4.1:** The workspace shall support real-time chat for group members.
- **FR-4.2:** Task board updates shall be synchronized instantly across all connected clients.

## 4. Non-Functional Requirements (NFR)

### NFR-1: Reliability
- **NFR-1.1:** The GitHub integration module shall handle API rate limits gracefully with exponential backoff.
- **NFR-1.2:** Chat messages must be delivered with < 500ms latency.

### NFR-2: Security
- **NFR-2.1:** All file uploads must be scanned for malware before storage.
- **NFR-2.2:** Access to the workspace must be strictly limited to group members and admins.

## 5. Interface Specifications

### API Endpoints
- `POST /api/projects`: Creates a new project workspace.
- `POST /api/projects/:id/tasks`: Adds a new task.
- `GET /api/projects/:id/github/prs`: Fetches open PRs from GitHub.

*Refer to [API Endpoints](../04-architecture/api-endpoints.md) for detailed schemas.*

## 6. Acceptance Criteria

- [ ] A new GitHub repository is successfully created upon project initialization.
- [ ] Task drag-and-drop updates the status for all users in real-time.
- [ ] AI Coach correctly identifies a potential bug in a sample code snippet.
- [ ] Users can upload and download project-related files (e.g., architecture diagrams).

## 7. Related Documents

- [F-002: Group Matching Algorithm](F-002-Group-Matching.md)
- [F-006: Portfolio Generator](F-006-Portfolio-Generator.md)
- [System Architecture](../04-architecture/system-architecture.md)

