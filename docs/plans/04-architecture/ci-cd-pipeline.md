# CI/CD Pipeline & Deployment

**Document:** TailCamp PRD - CI/CD Pipeline  
**Version:** 1.0  
**Last Updated:** 2025-11-23

---

## 1. Overview

This document defines the Continuous Integration and Continuous Deployment (CI/CD) strategy for TailCamp, including branching strategy, automated testing, deployment stages, and rollback procedures.

---

## 2. Git Branching Strategy

### GitHub Flow (Simplified)

```
main (production)
  ├── dev (staging)
  │   ├── feature/F-001-ai-assessment
  │   ├── feature/F-002-matching-algorithm
  │   └── bugfix/fix-websocket-reconnect
```

### Branch Protection Rules

| Branch | Protection | Required Checks |
|:-------|:-----------|:----------------|
| `main` | - No direct commits<br>- Require PR approval (2 reviewers)<br>- Require status checks<br>- No force push | All CI checks pass, Manual QA sign-off |
| `dev` | - Require PR approval (1 reviewer)<br>- Require status checks | All CI checks pass |
| `feature/*` | None | CI checks run but not required for merge to `dev` |

---

## 3. CI Pipeline (GitHub Actions)

### On Pull Request (to `dev` or `main`)

```yaml
name: CI Pipeline

on:
  pull_request:
    branches: [dev, main]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm run lint  # ESLint + Prettier
      
  type-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm run type-check  # TypeScript tsc --noEmit
      
  test-unit:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm run test:unit  # Jest unit tests
      - uses: codecov/codecov-action@v3  # Upload coverage
      
  test-integration:
    runs-on: ubuntu-latest
    services:
      postgres:
        image: postgres:16
      redis:
        image: redis:7
    steps:
      - uses: actions/checkout@v3
      - run: npm run test:integration
      
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm run build  # Next.js + NestJS
      - uses: actions/upload-artifact@v3
        with:
          name: build-artifacts
          path: dist/
```

**Coverage Requirement:** 80% for critical paths (authentication, matching algorithm).

---

## 4. CD Pipeline (Deployment)

### Environments

| Environment | Branch | Auto-Deploy | URL | Purpose |
|:------------|:-------|:------------|:----|:--------|
| **Development** | `dev` | Yes | dev.tailcamp.io | Feature validation, internal testing |
| **Staging** | `main` (pre-release) | Yes | staging.tailcamp.io | Final QA, client demos |
| **Production** | `main` (tagged) | Manual approval | app.tailcamp.io | Live users |

### Deployment Strategy: Rolling Update

-   **Zero Downtime:** Blue-green deployment for backend services.
-   **Database Migrations:** Run before deployment, reversible with `down` migrations.
-   **Feature Flags:** Use Unleash or LaunchDarkly for gradual rollouts.

### Example Deployment Workflow

```yaml
name: Deploy to Production

on:
  push:
    tags:
      - 'v*.*.*'  # e.g., v1.0.0

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Run DB Migrations
        run: npm run migrate:up
        
      - name: Deploy Backend (AWS ECS)
        run: |
          aws ecs update-service --cluster tailcamp-prod --service api --force-new-deployment
          
      - name: Deploy Frontend (Vercel)
        run: vercel --prod --token=${{ secrets.VERCEL_TOKEN }}
        
      - name: Smoke Tests
        run: npm run test:smoke  # Health check endpoints
        
      - name: Notify Slack
        uses: slackapi/slack-github-action@v1
        with:
          payload: |
            {
              "text": "Deployed ${{ github.ref }} to production"
            }
```

---

## 5. Database Migration Strategy

### TypeORM Migrations

-   **Naming:** `YYYYMMDDHHMMSS-DescriptiveName.ts` (e.g., `20250101120000-AddUserRolesTable.ts`)
-   **Versioning:** Stored in `src/migrations/`, tracked in DB table `migrations`.
-   **Testing:** Run migrations on a staging DB copy before production.

### Safety Checklist

- [ ] Migration is reversible (`up` and `down` defined)
- [ ] Tested on staging with production-like data volume
- [ ] No destructive operations (e.g., `DROP COLUMN`) in MVP
- [ ] Additive changes only (new columns, new tables)

---

## 6. Rollback Procedures

### Application Rollback

1.  **Revert Git Tag:** `git tag -d v1.2.0 && git push origin :refs/tags/v1.2.0`
2.  **Redeploy Previous Tag:** `git checkout v1.1.0 && git tag v1.1.0-rollback`
3.  **Trigger Deployment:** Push tag to trigger CD pipeline.

**RTO (Recovery Time Objective):** 15 minutes for application rollback.

### Database Rollback

1.  **Run Down Migration:** `npm run migrate:down -- -n 1`
2.  **Verify Data Integrity:** Check critical tables for consistency.

**RPO (Recovery Point Objective):** 24 hours (daily backups).

---

## 7. Monitoring & Alerts

### Health Checks

-   **API:** `GET /health` endpoint (checks DB connection, Redis, external APIs).
-   **Frontend:** Synthetic monitoring (Pingdom, UptimeRobot).

### Deployment Success Criteria

-   All smoke tests pass (HTTP 200 responses).
-   Error rate < 1% (Sentry threshold).
-   p95 latency < 500ms (DataDog APM).

### Alert Thresholds

| Metric | Warning | Critical | Action |
|:-------|:--------|:---------|:-------|
| **Error Rate** | >1% | >5% | Auto-rollback if critical for >5 min |
| **API Latency (p95)** | >1s | >3s | Scale up backend pods |
| **Failed Deployments** | 1 | 2 consecutive | Page on-call engineer |

---

## 8. Tools & Services

-   **Version Control:** GitHub
-   **CI/CD:** GitHub Actions
-   **Secret Management:** GitHub Secrets, AWS Secrets Manager
-   **Container Registry:** AWS ECR (Elastic Container Registry)
-   **Deployment Platform:** AWS ECS (Backend), Vercel (Frontend)
-   **Feature Flags:** Unleash (self-hosted) or LaunchDarkly

---

**Next Step:** Review [Observability](observability.md) for monitoring implementation.
