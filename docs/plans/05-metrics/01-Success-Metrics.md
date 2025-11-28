# Success Metrics & KPIs

**Document:** TailCamp PRD - Success Metrics & KPIs  
**Version:** 2.0  
**Last Updated:** 2025-11-28  

---

## 1. Overview

This document defines the Key Performance Indicators (KPIs) and success metrics for the TailCamp (OpusNode) platform. These metrics are designed to measure the health of the ecosystem, user value realization, and business growth. They are categorized to align with the user lifecycle: **Acquisition**, **Activation**, **Retention**, **Referral**, and **Revenue** (AARRR Framework).

**Related Documents:**
- [Executive Summary](../01-executive-summary.md)
- [Development Roadmap](../06-roadmap/development-roadmap.md)

---

## 2. North Star Metric

### Active Learning Groups (ALG)
**Definition:** The number of groups that have generated at least **3 meaningful interactions** (chat message, code commit, task update) within a rolling 7-day period.

**Rationale:** This metric captures the core value of TailCamp—**collaborative learning**. It correlates directly with user retention, project completion, and overall platform health. A high ALG indicates that users are not just matched but are actively engaging and deriving value.

**Targets:**
-   **Q2 (Launch + 3mo):** 500 ALGs
-   **Q4 (Launch + 9mo):** 2,000 ALGs

---

## 3. Core KPIs by Category

### 3.1 Activation (First Value)
*Measuring the effectiveness of the onboarding and matching process.*

| Metric | Definition | Target (Q2) | Rationale |
|:-------|:-----------|:------------|:----------|
| **Assessment Completion Rate** | % of sign-ups who complete the initial AI assessment. | > 80% | Indicates the friction level of the onboarding flow. |
| **Time-to-Match** | Average time from joining the queue to being placed in a group. | < 24 Hours | Critical for maintaining user momentum and interest. |
| **First Project Start Rate** | % of new groups that initialize their first project within 48 hours. | > 90% | Measures the effectiveness of the "Integration Hub" setup. |

### 3.2 Retention (Habit Formation)
*Measuring long-term engagement and platform stickiness.*

| Metric | Definition | Target (Q2) | Rationale |
|:-------|:-----------|:------------|:----------|
| **Day 30 Retention** | % of users active on Day 30 after sign-up. | > 40% | Indicates if users find lasting value beyond the initial match. |
| **Weekly Active Users (WAU)** | Unique users who perform a core action (learn, code, chat) in a week. | 5,000 | Standard measure of platform growth and engagement. |
| **Group Survival Rate** | % of groups that remain active until project completion. | > 70% | Measures the quality of the matching algorithm. |

### 3.3 Outcomes (Value Realization)
*Measuring the tangible benefits delivered to users.*

| Metric | Definition | Target (Q2) | Rationale |
|:-------|:-----------|:------------|:----------|
| **Project Completion Rate** | % of started projects that result in a generated portfolio. | > 60% | The ultimate goal for the user; proves educational efficacy. |
| **Portfolio Generation Rate** | % of project completers who export a portfolio. | > 50% | Indicates the utility of the portfolio feature. |
| **Net Promoter Score (NPS)** | User willingness to recommend TailCamp (Scale -100 to 100). | > 50 | Proxy for overall user satisfaction and product-market fit. |

---

## 4. Operational Health Metrics

These metrics monitor the technical stability and operational efficiency required to support growth.

-   **System Uptime:** **99.9%** availability (excluding scheduled maintenance).
-   **Match Failure Rate:** **< 5%** of users failing to find a match within 48 hours (triggers manual intervention).
-   **AI Response Latency:** 
    -   Chat interactions: **< 2 seconds** (P95).
    -   Curriculum generation: **< 30 seconds** (P95).
-   **Support Ticket Volume:** **< 1 ticket** per 100 active users per week.

---

## 5. Measurement Strategy

### Data Sources
-   **Application DB (PostgreSQL):** Transactional data (sign-ups, project status, group formation).
-   **Event Logs (Mixpanel/Amplitude):** User behavior tracking (clicks, flow drop-offs, feature usage).
-   **System Logs (DataDog/Sentry):** Performance monitoring, error rates, and latency tracking.
-   **User Surveys:** Qualitative feedback (NPS, CSAT) collected via in-app prompts.

### Reporting Cadence
-   **Real-time Dashboard:** Operational health, live user count, queue status.
-   **Weekly Business Review (WBR):** WAU, Retention, Match Quality, Activation rates.
-   **Monthly Business Review (MBR):** Strategic goal progress, Roadmap adjustments, Financial metrics.

---

**Next Step:** Review [Development Roadmap](../06-roadmap/development-roadmap.md).

