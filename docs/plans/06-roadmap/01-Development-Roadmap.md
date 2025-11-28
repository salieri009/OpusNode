# Development Roadmap

---
**Document ID:** ROAD-01  
**Version:** 2.0  
**Date:** 2025-11-28  
**Author:** Senior Technical Writer  
**Status:** Draft  
---

## 1. Overview
This roadmap outlines the strategic development plan for OpusNode, divided into three distinct phases. The strategy prioritizes **Core Value Validation** (Matching) in the MVP phase, followed by **Content Generation** and **Ecosystem Expansion**.

## 2. Purpose
The purpose of this document is to:
1.  Align stakeholders on delivery timelines and priorities.
2.  Manage scope creep by clearly defining what is "In Scope" for each phase.
3.  Ensure technical dependencies are resolved in the correct order.

## 3. Terminology
| Term | Definition |
| :--- | :--- |
| **MVP (Minimum Viable Product)** | The smallest set of features required to deliver value to early adopters (Instructors/Students). |
| **Integration Hub** | The strategy of connecting existing tools rather than building new ones (Phase 1 focus). |
| **Native Ecosystem** | The long-term goal of building proprietary tools within OpusNode (Phase 3 focus). |

## 4. Phased Rollout Strategy

### Phase 1: MVP - Core Matching & Integration (Months 1-3)
**Goal:** Enable instructors to assess students, form teams, and provision workspaces using external tools.

| Feature ID | Feature Name | Scope |
| :--- | :--- | :--- |
| **F-001** | **AI Assessment** | Basic text-based skill survey. |
| **F-002** | **Group Matching** | Algorithm v1 (Skills + Schedule). Batch processing. |
| **F-004** | **Project Workspace** | **Integration Only.** Auto-setup for Slack/GitHub. |
| **F-007** | **Admin Dashboard** | User management, Matching trigger, Basic settings. |
| **INFRA** | **Foundation** | Auth (SSO), DB Setup, CI/CD, LTI Basic Handshake. |

### Phase 2: Enhancement - Content & Analytics (Months 4-6)
**Goal:** Enrich the learning experience with AI-generated content and deeper insights.

| Feature ID | Feature Name | Scope |
| :--- | :--- | :--- |
| **F-005** | **Curriculum Generator** | AI-generated weekly learning paths based on project stack. |
| **F-006** | **Portfolio Generator** | Auto-generation of project case studies (PDF/Web). |
| **F-003** | **Learning Dashboard** | Advanced analytics, Peer review system. |
| **F-004** | **Workspace v2** | Activity aggregation feed (Webhooks implementation). |

### Phase 3: Expansion - Native Ecosystem (Months 7+)
**Goal:** Reduce reliance on external tools and capture more user time.

| Feature ID | Feature Name | Scope |
| :--- | :--- | :--- |
| **F-004** | **Native Workspace** | Built-in Chat, Wiki, and Kanban board. |
| **MOBILE** | **Mobile App** | React Native app for notifications and quick tasks. |
| **ENT** | **Enterprise** | Audit logs, Advanced RBAC, Multi-tenancy. |

## 5. Critical Path & Dependencies
1.  **Month 1:** Infrastructure & Auth must be completed before any user data can be collected for F-001.
2.  **Month 2:** F-001 (Assessment) data is a hard prerequisite for F-002 (Matching).
3.  **Month 3:** F-004 (Integration) requires F-002 to be stable, as workspace provisioning depends on finalized team rosters.

## 6. Limitations & Risks
*   **Scope Creep:** Phase 1 is tight. Any request to add "Native Chat" to MVP must be rejected to meet the timeline.
*   **Integration Complexity:** Delays in LTI certification or OAuth verification with Google/GitHub could push back the launch.

## 7. Conclusion
This roadmap adopts a **"Lean Startup"** approach. By deferring complex native features (Chat, Wiki) to Phase 3, the team can focus resources on the unique value proposition of OpusNode: **Intelligent Matching and Automated Setup**. This maximizes the chance of a successful MVP launch within 3 months.

