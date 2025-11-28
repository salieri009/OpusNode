# 13. Project Voting

**Document:** TailCamp PRD - Page Design: Project Voting  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Project Voting page allows team members to vote on proposed project ideas and leave comments. It displays all proposals with vote counts and enables democratic project selection.

**Page Type:** Authenticated (Group members only)  
**Complexity:** ⚡ Medium  
**Priority:** P0 (MVP)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 3.3.2
- **[F-004: Project Workspace](../../../03-features/F-004-Project-Workspace.md)** - **Feature:** Democratic project selection, voting mechanism, team decision-making

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│  [← Back]                               │
├─────────────────────────────────────────┤
│                                         │
│  Vote on Project Ideas                  │
│                                         │
│  ┌───────────────────────────────────┐ │
│  │ Project: E-commerce API            │ │
│  │ By: Alex                           │ │
│  │                                    │ │
│  │ "Build a RESTful API for an       │ │
│  │  e-commerce platform with..."     │ │
│  │                                    │ │
│  │ Tech: Node.js, PostgreSQL         │ │
│  │ Duration: 2-3 months              │ │
│  │                                    │ │
│  │ 👍 3 votes  |  💬 2 comments     │ │
│  │                                    │ │
│  │ [👍 Vote] [💬 Comment]           │ │
│  └───────────────────────────────────┘ │
│                                         │
│  ┌───────────────────────────────────┐ │
│  │ Project: Task Management App      │ │
│  │ ...                               │ │
│  └───────────────────────────────────┘ │
│                                         │
│  Voting ends in 48 hours                │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Project Card Components

### 3.1 Project Header
- **Project Name:** Large, prominent
- **Proposer:** "By: [Name]"
- **Timestamp:** "Proposed 2 hours ago"

### 3.2 Project Description
- **Text:** Full description (truncated if long, expandable)
- **Read More:** Expandable section for long descriptions

### 3.3 Project Metadata
- **Tech Stack:** Chips showing technologies
- **Duration:** "2-3 months"
- **Difficulty:** "Intermediate"

### 3.4 Engagement Metrics
- **Vote Count:** "👍 3 votes"
- **Comment Count:** "💬 2 comments"
- **Real-time Updates:** Via WebSocket

### 3.5 Actions
- **Vote Button:** 👍 (upvote only, no downvotes)
- **Comment Button:** 💬 (opens comment section)

---

## 4. Interactions

### 4.1 Voting
- **Mechanism:** Upvote only (simple 👍 button)
- **Multiple Votes:** Users can vote for multiple projects
- **Real-time:** Vote count updates via WebSocket
- **Visual:** Button highlights when user has voted

### 4.2 Commenting
- **Inline Comments:** Expandable section below each project
- **Real-time:** New comments appear instantly
- **Notifications:** Alert when someone comments on your proposal
- **Format:** Threaded comments (optional)

### 4.3 Voting Timer
- **Display:** "Voting ends in 48 hours"
- **Countdown:** Real-time countdown timer
- **End State:** "Voting ended. Winner: [Project Name]"

---

## 5. States

### 5.1 Default
- All proposals visible
- Vote counts displayed
- Comment sections collapsed

### 5.2 User Voted
- Vote button highlighted
- Vote count updated
- Confirmation: "You voted for this project"

### 5.3 Comments Expanded
- Comment section visible
- Comment input field
- Previous comments displayed

### 5.4 Voting Ended
- Vote buttons disabled
- Winner highlighted
- "Voting ended" message

---

## 6. Design Specifications

### 6.1 Components Used
- **Project Cards:** Proposal display cards
- **Vote Button:** Thumbs up icon with count
- **Comment Section:** Expandable comment thread
- **Timer:** Countdown display
- **Winner Badge:** Highlight for winning project

### 6.2 Visual Hierarchy
- **Winning Project:** Highlighted, badge, top of list
- **Vote Counts:** Prominent display
- **Comments:** Secondary, expandable

---

## 7. Real-time Updates

### 7.1 WebSocket Integration
- **Vote Updates:** Real-time vote count changes
- **Comment Updates:** New comments appear instantly
- **Timer Updates:** Countdown updates every minute

### 7.2 Notification
- **New Comment:** Toast notification when someone comments
- **Vote Change:** Subtle animation when vote count changes

---

## 8. Accessibility

- **Keyboard Navigation:** Tab through projects, Enter to vote
- **Screen Reader:** "Project: E-commerce API. 3 votes. [Vote] button."
- **Focus Indicators:** Clear focus on interactive elements

---

## 9. Related Pages

- **Previous:** [12-Project-Proposal](12-Project-Proposal.md) - After proposal submitted
- **Next:** [14-Project-Workspace](14-Project-Workspace.md) - After voting ends, winning project selected
- **Back:** [11-Group-Profile](11-Group-Profile.md) - User clicks back

---

## 10. Acceptance Criteria

- [ ] All proposals display correctly
- [ ] Voting works (upvote only)
- [ ] Vote counts update in real-time
- [ ] Comments work correctly
- [ ] Timer countdown works
- [ ] Winner is highlighted after voting ends
- [ ] Real-time updates via WebSocket work
- [ ] Mobile layout is responsive

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 3.3.2 for detailed flow context.

