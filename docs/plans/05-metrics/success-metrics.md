# Success Metrics & KPIs

**Document:** TailCamp PRD - Success Metrics & KPIs  
**Version:** 1.1  
**Last Updated:** 2025-11-23

---

## 1. Overview

This document defines the Key Performance Indicators (KPIs) and success metrics for the TailCamp platform. These metrics are designed to measure the health of the ecosystem, user value realization, and business growth. They are categorized to align with the user lifecycle: Acquisition, Activation, Retention, Referral, and Revenue (AARRR).

**Related Documents:**
- [Executive Summary](../01-executive-summary.md)
- [Development Roadmap](../06-roadmap/development-roadmap.md)

---

## 2. North Star Metric

### Active Learning Groups (ALG)
**Definition:** The number of groups that have generated at least 3 meaningful interactions (chat, code commit, task update) within a rolling 7-day period.

**Rationale:** This metric captures the core value of TailCamp—collaborative learning. It correlates directly with user retention, project completion, and platform health.

**Targets:**
-   **Q2 (Launch + 3mo):** 500 ALGs
-   **Q4 (Launch + 9mo):** 2,000 ALGs

---

## 3. Core KPIs by Category

### 3.1 Activation (First Value)
*Measuring the effectiveness of the onboarding and matching process.*

| Metric | Definition | Target (Q2) |
|:-------|:-----------|:------------|
| **Assessment Completion Rate** | % of sign-ups who complete the initial AI assessment. | > 80% |
| **Time-to-Match** | Average time from joining the queue to being placed in a group. | < 24 Hours |
| **First Project Start Rate** | % of new groups that initialize their first project within 48 hours. | > 90% |

### 3.2 Retention (Habit Formation)
*Measuring long-term engagement and platform stickiness.*

| Metric | Definition | Target (Q2) |
|:-------|:-----------|:------------|
| **Day 30 Retention** | % of users active on Day 30 after sign-up. | > 40% |
| **Weekly Active Users (WAU)** | Unique users who perform a core action (learn, code, chat) in a week. | 5,000 |
| **Group Survival Rate** | % of groups that remain active until project completion. | > 70% |

### 3.3 Outcomes (Value Realization)
*Measuring the tangible benefits delivered to users.*

| Metric | Definition | Target (Q2) |
|:-------|:-----------|:------------|
| **Project Completion Rate** | % of started projects that result in a generated portfolio. | > 60% |
| **Portfolio Generation Rate** | % of project completers who export a portfolio. | > 50% |
| **Net Promoter Score (NPS)** | User willingness to recommend TailCamp. | > 50 |

---

## 4. Operational Health Metrics

These metrics monitor the technical stability and operational efficiency required to support growth.

-   **System Uptime:** 99.9% availability.
-   **Match Failure Rate:** < 5% of users failing to find a match within 48 hours.
-   **AI Response Latency:** < 2 seconds for chat interactions; < 30 seconds for curriculum generation.
-   **Support Ticket Volume:** < 1 ticket per 100 active users per week.

---

## 5. Measurement Strategy

### Data Sources
-   **Application DB (PostgreSQL):** Transactional data (sign-ups, project status).
-   **Event Logs (Mixpanel/Amplitude):** User behavior tracking (clicks, flows).
-   **System Logs (DataDog/Sentry):** Performance and error tracking.
-   **User Surveys:** Qualitative feedback (NPS, CSAT).

### Reporting Cadence
-   **Real-time Dashboard:** Operational health, live user count.
-   **Weekly Business Review (WBR):** WAU, Retention, Match Quality.
-   **Monthly Business Review (MBR):** Strategic goal progress, Roadmap adjustments.

---

**Next Step:** Review [Development Roadmap](../06-roadmap/development-roadmap.md).

