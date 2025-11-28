# Development Workflow & Collaboration

**Document:** TailCamp PRD - Development Workflow  
**Version:** 1.0  
**Last Updated:** 2025-11-23

---

## 1. Overview

This document defines the development workflow, code review process, communication standards, and collaboration best practices for the TailCamp team.

---

## 2. Development Workflow

### Sprint Cadence (2-Week Sprints)

| Day | Activity | Duration | Participants |
|:----|:---------|:---------|:-------------|
| **Monday (Week 1)** | Sprint Planning | 2 hours | Entire team |
| **Daily** | Standup | 15 minutes | Engineering team |
| **Wednesday (Week 2)** | Mid-Sprint Review | 30 minutes | PM + Tech Lead |
| **Friday (Week 2)** | Sprint Review + Retro | 1.5 hours | Entire team |

### Sprint Planning Process

1.  **Backlog Refinement** (prior to planning):
    -   PM presents prioritized issues from `docs/plans/06-roadmap/`.
    -   Engineers estimate complexity (1, 2, 3, 5, 8 story points).
2.  **Sprint Goal Definition:**
    -   Example: "Complete F-001 AI Assessment MVP (FR-001 through FR-005)."
3.  **Task Breakdown:**
    -   Engineers create granular tasks in Linear/Jira.
    -   Each task < 1 day of work.

---

## 3. Code Collaboration

### Pull Request (PR) Process

#### Creating a PR

1.  **Branch Naming:**
    -   `feature/F-XXX-short-description` (e.g., `feature/F-001-assessment-chat`)
    -   `bugfix/issue-number-short-description` (e.g., `bugfix/123-fix-websocket`)
2.  **PR Title Format:**
    -   `[F-XXX] Brief description` (e.g., `[F-001] Implement AI chat interface`)
3.  **PR Description Template:**
    ```markdown
    ## What
    Brief summary of changes.
    
    ## Why
    Link to feature spec or issue (e.g., `Implements F-001 FR-003`).
    
    ## How
    Technical approach, key decisions.
    
    ## Testing
    - [ ] Unit tests added
    - [ ] Integration tests added
    - [ ] Manual testing completed
    
    ## Screenshots (if UI change)
    [Attach before/after]
    ```

#### Code Review Guidelines

-   **Reviewers:** Minimum 1 approval required for `dev`, 2 for `main`.
-   **Review SLA:** Within 4 business hours for `dev`, 24 hours for `main`.
-   **Review Checklist:**
    -   [ ] Code follows style guide (ESLint passing).
    -   [ ] Tests cover new functionality (80% coverage maintained).
    -   [ ] No hardcoded secrets or API keys.
    -   [ ] Documentation updated (if public API change).
    -   [ ] Performance impact considered (no N+1 queries).

**Code Ownership (CODEOWNERS):**
```
# Frontend
/apps/web/           @frontend-team
/packages/ui/        @frontend-team

# Backend
/apps/api/           @backend-team
/packages/database/  @backend-team

# AI/ML
/apps/ai-engine/     @ai-team

# DevOps
/.github/workflows/  @devops-team
/infrastructure/     @devops-team
```

---

## 4. Communication Channels

### Synchronous (Real-Time)

| Channel | Purpose | Availability |
|:--------|:--------|:-------------|
| **Daily Standups** | Status updates, blockers | 9:00 AM daily |
| **Slack #engineering** | Quick questions, urgent issues | 9 AM - 6 PM |
| **Pair Programming** | Complex features, knowledge transfer | Ad-hoc, scheduled |

### Asynchronous

| Channel | Purpose | Response SLA |
|:--------|:--------|:-------------|
| **GitHub Issues** | Bug reports, feature requests | 24 hours (triage) |
| **GitHub Discussions** | Technical proposals, RFCs | 48 hours |
| **Slack #announcements** | Releases, incidents, major updates | Read-only |
| **Linear/Jira Comments** | Task-specific discussions | Next business day |

### Documentation

-   **Architecture Decision Records (ADRs):** Stored in `docs/plans/04-architecture/decisions/`.
-   **Technical Specs:** Use the `F-XXX` feature spec template in `docs/plans/03-features/`.
-   **API Documentation:** Auto-generated from OpenAPI/GraphQL schemas, hosted on Stoplight or similar.

---

## 5. Code Style & Standards

### Languages

-   **TypeScript:** Strict mode enabled, no `any` types without explicit justification.
-   **Python:** PEP 8 compliance for AI service.

### Formatting

-   **Prettier:** Auto-format on save (`.prettierrc` in repo root).
-   **ESLint:** Airbnb style guide with TailCamp-specific overrides.

### Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat(F-001): add AI chat interface
fix(matching): resolve deadlock in queue processing
docs: update API endpoint for portfolio generation
chore: upgrade Next.js to v14.2
```

**Scope:** Use feature ID (e.g., `F-001`) or module name (`matching`, `auth`).

---

## 6. Testing Standards

### Test Pyramid

-   **70% Unit Tests:** Fast, isolated, mock external dependencies.
-   **20% Integration Tests:** Test API endpoints, database interactions.
-   **10% E2E Tests:** Critical user paths (signup → assessment → match).

### Running Tests Locally

```bash
# Unit tests (fast)
npm run test:unit

# Integration tests (requires Docker containers)
docker-compose up -d postgres redis
npm run test:integration

# E2E tests (requires full stack running)
npm run dev &
npm run test:e2e
```

### Coverage Requirement

-   **Minimum:** 80% for all new code.
-   **Critical Paths:** 95% for authentication, matching algorithm, payment (if implemented).

---

## 7. Incident Response

### On-Call Rotation

-   **Primary:** Backend engineer (rotating weekly).
-   **Secondary:** DevOps/SRE.

### Incident Severity Levels

| Severity | Definition | Response Time | Example |
|:---------|:-----------|:--------------|:--------|
| **P0 - Critical** | Service down, data loss | Immediate (page) | Database unavailable |
| **P1 - High** | Major feature broken | 1 hour | Matching algorithm failing |
| **P2 - Medium** | Partial degradation | 4 hours | Slow API responses |
| **P3 - Low** | Minor bug, no user impact | Next business day | Typo in UI |

### Post-Incident Process

1.  **Incident Reported:** Create Slack thread in `#incidents`.
2.  **Mitigation:** On-call engineer resolves or escalates.
3.  **Post-Mortem:** Within 48 hours, document in `docs/plans/07-risks/incidents/YYYY-MM-DD-incident-name.md`.
4.  **Action Items:** Create follow-up GitHub issues, assign owners.

---

## 8. Onboarding New Engineers

### Day 1 Checklist

- [ ] Access to GitHub organization
- [ ] Slack workspace invitation
- [ ] Development environment setup (README instructions)
- [ ] Read `docs/plans/README.md` (PRD overview)
- [ ] Shadow a PR review session

### Week 1 Goals

-   Submit first PR (e.g., fix documentation typo, update dependencies).
-   Pair with senior engineer on one task from current sprint.
-   Attend Sprint Planning and Retro.

---

**Next Step:** Review [CI/CD Pipeline](../04-architecture/ci-cd-pipeline.md) for deployment workflow.
