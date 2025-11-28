# F-002: Intelligent Group Matching

---
**Document ID:** F-002  
**Version:** 2.0  
**Date:** 2025-11-28  
**Author:** Senior Technical Writer  
**Status:** Draft  
---

## 1. Overview
The **Intelligent Group Matching** system is the core engine of OpusNode. It utilizes a weighted multi-variable algorithm to form project teams that are balanced in skills, compatible in schedule, and diverse in perspective. The system aims to maximize the "Project Success Probability" metric.

## 2. Purpose
The purpose of this feature is to:
1.  **Optimize Team Composition:** Prevent common failure modes like "all-beginner teams" or "conflicting schedules."
2.  **Automate Administration:** Replace manual spreadsheet-based grouping with an instant, data-driven process.
3.  **Enhance Learning Outcomes:** Pair students in ways that foster peer learning (e.g., Mentor-Mentee dynamics).

## 3. Terminology
| Term | Definition |
| :--- | :--- |
| **Matching Score ($S$)** | A calculated numerical value representing the compatibility between a user and a potential group. |
| **Hard Constraint** | A rule that must be met (e.g., "Must speak English"). Violation results in a score of 0. |
| **Soft Constraint** | A preference that increases the score but is not mandatory (e.g., "Prefers Frontend"). |
| **Genetic Algorithm** | An optimization heuristic that mimics the process of natural selection to find high-quality solutions for optimization problems. |

## 4. Feature Summary
The matching engine processes user profiles through a three-stage pipeline: **Filtering (Hard Constraints)** -> **Scoring (Soft Constraints)** -> **Optimization (Team Formation)**.

## 5. Detailed Description

### 5.1 Matching Algorithm Logic
The compatibility score ($S$) between a set of users is calculated as follows:

$$ S = (w_1 \times C_{skill}) + (w_2 \times C_{schedule}) + (w_3 \times C_{style}) - P_{conflict} $$

#### Variables & Weights
1.  **Skill Complementarity ($C_{skill}$, 40%)**
    *   Ensures a mix of roles (e.g., 1 Backend, 1 Frontend, 1 Designer).
    *   Calculates the variance of skill levels; lower variance is better for peer groups, high variance is better for mentorship groups.
2.  **Schedule Compatibility ($C_{schedule}$, 30%)**
    *   Calculates the number of overlapping available hours per week.
    *   **Threshold:** Minimum 4 hours of overlap required.
3.  **Work Style & Personality ($C_{style}$, 20%)**
    *   Based on Big 5 or MBTI-like inputs.
    *   Balances "Leader" and "Follower" traits.
4.  **Diversity Bonus (10%)**
    *   Adds points for mixed majors or backgrounds.

#### Penalties
*   **$P_{conflict}$:** If users have blocked each other or have a history of negative peer reviews, the score is penalized heavily (-$\infty$).

### 5.2 Execution Flow
1.  **Data Collection:** Users complete the onboarding survey (Skills, Schedule, Style).
2.  **Batch Processing:** The system runs the matching job (via BullMQ) at a scheduled time (e.g., after registration deadline).
3.  **Draft Generation:** The Genetic Algorithm generates 3 candidate team configurations.
4.  **Instructor Review:** The instructor reviews the drafts and selects the best configuration.
5.  **Notification:** Users are notified of their team assignment.

## 6. Use Cases

### UC-01: Balanced Team Formation
*   **Scenario:** A class has 100 students with varying skill levels (20 Experts, 50 Intermediates, 30 Beginners).
*   **System Action:** The algorithm distributes Experts evenly across teams to ensure no team is left without technical leadership.

### UC-02: Schedule-Based Matching
*   **Scenario:** Student A works part-time and is only available on weekends. Student B is free only on weekdays.
*   **System Action:** The system detects zero overlap and prevents them from being matched, avoiding future scheduling conflicts.

## 7. Limitations & Constraints
*   **Cold Start Problem:** The algorithm requires accurate user input. If students lie about their skills, the matching will be suboptimal.
*   **Computational Complexity:** The problem is NP-Hard. For $N > 500$, exact solutions are impossible; heuristic approximations are used.
*   **Human Factor:** Algorithms cannot predict interpersonal chemistry perfectly. A manual "Team Change Request" process is required as a fallback.

## 8. Conclusion
F-002 transforms team formation from a random guess into a scientific process. By explicitly defining weights for Skills, Schedule, and Style, OpusNode ensures that every team has a fighting chance at success.

