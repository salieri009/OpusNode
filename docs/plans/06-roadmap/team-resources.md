# Team & Resource Allocation

**Document:** TailCamp PRD - Team & Resources  
**Version:** 1.0  
**Last Updated:** 2025-11-23

---

## 1. Team Composition

### Phase 1: MVP (Months 1-3)

| Role | FTE | Responsibilities | Justification |
|:-----|:----|:----------------|:--------------|
| **Frontend Engineer** | 2.0 | Next.js UI, Real-time features, Assessment interface | Complex UI for chat assessment, dashboard visualizations |
| **Backend Engineer** | 2.0 | NestJS API, WebSocket, Database design, Integration | Core service layer, matching algorithm integration |
| **AI/ML Engineer** | 1.0 | LangChain workflows, Prompt engineering, Vector DB | AI assessment and curriculum generation are core differentiators |
| **Product Manager** | 0.5 | Requirements, Prioritization, User research | Part-time PM sufficient for MVP scope |
| **UX/UI Designer** | 0.5 | Wireframes, Design system, User testing | Upfront design work concentrated in Month 1 |
| **QA Engineer** | 0.5 | Test planning, Manual testing, Automation setup | Critical path testing only for MVP |
| **DevOps/SRE** | 0.3 | CI/CD setup, Infrastructure, Monitoring | Initial setup, then on-call as needed |

**Total:** 6.8 FTE

### Phase 2: Enhancement (Months 4-6)

| Role | FTE Change | New Responsibilities |
|:-----|:-----------|:---------------------|
| **Frontend Engineer** | +0.5 (2.5 total) | GitHub integration, Portfolio templates |
| **Backend Engineer** | Maintain 2.0 | Project workspace features, File management |
| **QA Engineer** | +0.5 (1.0 total) | E2E test coverage, Performance testing |
| **Community Manager** | +1.0 (NEW) | Beta user onboarding, Feedback loops, Content moderation |

**Total:** 7.8 FTE

---

## 2. Budget Estimate

### Infrastructure & Tools (Monthly)

| Category | Service | Cost (USD/month) | Phase 1 | Phase 2 |
|:---------|:--------|:-----------------|:--------|:--------|
| **Hosting** | Vercel (Frontend) | $20-100 | $50 | $100 |
| | AWS EC2/ECS (Backend) | $200-500 | $300 | $500 |
| | AWS RDS (PostgreSQL) | $100-300 | $150 | $300 |
| | AWS S3 + CloudFront | $50-150 | $75 | $150 |
| **AI Services** | OpenAI API (GPT-4) | $500-2000 | $800 | $1500 |
| | Pinecone/Milvus | $70-200 | $100 | $200 |
| **Monitoring** | Sentry | $29 | $29 | $29 |
| | DataDog (optional) | $0-500 | $0 | $200 |
| **Tools** | GitHub Enterprise | $21/user | $147 | $168 |
| | Figma | $12/editor | $24 | $24 |
| | Linear/Jira | $10/user | $70 | $84 |
| **Subtotal** | | | **$1,745** | **$3,255** |

### Annual Infrastructure: **$21K-40K**

### Personnel Costs (Placeholder)
-   Varies significantly by region (SF Bay Area vs. Remote Global)
-   Estimated range: $500K-800K/year for the 6.8 FTE MVP team
-   Not including equity, benefits, or overhead

---

## 3. External Dependencies

### Critical Path Blockers

| Dependency | Timeline | Risk Level | Mitigation |
|:-----------|:---------|:-----------|:-----------|
| **OpenAI API Access** | 1 week approval | Low | Apply early, have Claude fallback |
| **AWS Quota Increase** | 2-3 weeks | Medium | Request during Month 1 setup |
| **Beta Tester Recruitment** | Ongoing (Month 2-3) | Medium | Partner with bootcamps, Reddit communities |
| **Vector DB Evaluation** | Month 1 | Low | Parallel POC: Milvus (self-hosted) vs. Pinecone (managed) |

### Non-Blocking Dependencies
-   Payment gateway integration (Stripe) - Post-MVP
-   Email service provider (SendGrid/AWS SES) - Month 1
-   Analytics platform (Mixpanel/Amplitude) - Month 2

---

## 4. Go/No-Go Decision Criteria

### End of Month 3 Review

**Proceed to Phase 2 if:**
-   ✅ Assessment completion rate > 70%
-   ✅ Match success rate (48hrs) > 80%
-   ✅ Week 1 retention > 40%
-   ✅ Group formation rate > 85%
-   ✅ Infrastructure costs < $2,500/mo (at 500 users)

**PAUSE and Re-scope if:**
-   ❌ Any of the above thresholds missed by >20%
-   ❌ Critical technical debt identified (e.g., matching algorithm doesn't scale)
-   ❌ Negative user feedback on core value prop (assessment quality, match quality)

**PIVOT if:**
-   ❌ Unable to achieve product-market fit indicators: NPS < 20, churn > 60% Week 1

---

**Next Step:** Review [Development Roadmap](development-roadmap.md).
