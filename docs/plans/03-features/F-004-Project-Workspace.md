# F-004: Project Workspace (Integration Hub)

---
**Document ID:** F-004  
**Version:** 2.0  
**Date:** 2025-11-28  
**Author:** Senior Technical Writer  
**Status:** Draft  
---

## 1. Overview
The **Project Workspace** serves as the central digital hub for student teams. In its initial release (MVP), it functions primarily as an **Integration Hub**, orchestrating the automatic provisioning and management of external collaboration tools (Slack, GitHub, Notion) rather than providing native alternatives. This approach minimizes the learning curve and leverages industry-standard tools.

## 2. Purpose
The purpose of this feature is to:
1.  **Reduce Setup Time:** Eliminate the manual friction of creating repositories, communication channels, and document spaces for new teams.
2.  **Centralize Activity:** Provide a single dashboard that aggregates activity logs from disparate external tools.
3.  **Standardize Workflow:** Ensure all teams use a consistent set of tools and templates for their projects.

## 3. Terminology
| Term | Definition |
| :--- | :--- |
| **Integration Hub** | The core system component that connects OpusNode with external APIs (Slack, GitHub, etc.). |
| **Provisioning** | The automated process of creating accounts, channels, or repositories and assigning permissions. |
| **Activity Feed** | A chronological stream of events (commits, messages, edits) collected from connected tools. |
| **LTI (Learning Tools Interoperability)** | A standard protocol for connecting learning systems, used here for potential LMS integration. |

## 4. Feature Summary
The Project Workspace focuses on **Tool Provisioning** and **Activity Aggregation**.
*   **Auto-Provisioning:** Automatically creates a Slack channel, GitHub repository, and Notion page upon team formation.
*   **Unified Dashboard:** Displays a high-level view of team progress, including recent commits, active tasks, and unread messages.
*   **Milestone Tracking:** Simple checklist-based tracking of project phases, synced with external issue trackers where possible.

## 5. Detailed Description

### 5.1 Tool Provisioning Workflow
When a group is finalized (Status: `MATCHED`), the system triggers the following sequence:

1.  **GitHub Repository Creation:**
    *   Creates a private repository in the organization's GitHub account.
    *   Adds all team members as collaborators.
    *   Initializes with a standard `README.md` and `.gitignore` template.
2.  **Communication Channel Setup:**
    *   Creates a private channel in the course's Slack workspace or a dedicated Discord server.
    *   Invites all team members and the assigned mentor.
3.  **Documentation Space:**
    *   Generates a new Team Space in Notion or a Shared Folder in Google Drive.
    *   Populates it with project templates (PRD, Weekly Report).

### 5.2 Activity Aggregation Logic
The system uses Webhooks and Polling to gather data:
*   **GitHub:** Listens for `push`, `pull_request`, and `issue` events via Webhooks.
*   **Slack/Discord:** Fetches message counts and activity trends (privacy-preserving: no content storage).
*   **Notion/Drive:** Tracks "Last Edited" timestamps to monitor documentation progress.

## 6. Use Cases

### UC-01: Team Onboarding
*   **Actor:** Student (Team Leader)
*   **Scenario:** A student logs in after being matched. They see a "Start Project" button.
*   **Outcome:** Clicking the button instantly opens links to the pre-configured GitHub repo, Slack channel, and Notion page. No manual setup is required.

### UC-02: Progress Monitoring
*   **Actor:** Instructor
*   **Scenario:** An instructor wants to check if Team A is active.
*   **Outcome:** The instructor views the Team A Dashboard and sees "5 Commits today" and "Active discussion in Slack," confirming engagement without needing to log into each tool separately.

## 7. Limitations & Constraints
*   **Dependency Risk:** The system relies entirely on third-party APIs. Downtime in GitHub or Slack will affect provisioning.
*   **Authentication:** Users must link their personal accounts (OAuth) for full functionality.
*   **Data Privacy:** The system stores metadata (timestamps, counts) but does not archive full chat logs or code content to minimize privacy risks.

## 8. Conclusion
By pivoting F-004 to an **Integration Hub**, OpusNode delivers immediate value with lower development risk. This strategy allows the platform to focus on its core differentiator—**Matching and Assessment**—while relying on best-in-class tools for the actual collaboration experience. Native collaboration features will be reconsidered in Phase 3.

