# 09. Matching Queue

**Document:** TailCamp PRD - Page Design: Matching Queue  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Matching Queue page displays the user's position in the matching queue while the algorithm searches for compatible teammates. It provides transparency, status updates, and estimated wait time to build trust in the matching process.

**Page Type:** Authenticated  
**Complexity:** ⚡ Medium  
**Priority:** P0 (MVP)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 3.2.1
- **[F-002: Group Matching](../../../03-features/F-002-Group-Matching.md)** - **Core Feature:** Matching algorithm execution, batch processing, team formation (Section 5.2)
- [NFRs-Design Integration](../../../03-features/NFRs/02-NFRs-Design-Integration.md) - Real-time updates

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│                                         │
│         🔍 Finding Your Team            │
│                                         │
│  ┌───────────────────────────────────┐ │
│  │                                   │ │
│  │    [Animated Pulsing Circles]     │ │
│  │    "Analyzing 47 potential       │ │
│  │     teammates..."                 │ │
│  │                                   │ │
│  └───────────────────────────────────┘ │
│                                         │
│  Queue Position: #12                    │
│  Estimated Time: 2-4 hours              │
│                                         │
│  What we're looking for:                │
│  ✓ Similar skill level                 │
│  ✓ Complementary strengths             │
│  ✓ Shared learning goals               │
│  ✓ Compatible schedules                │
│                                         │
│  [Leave Queue] (secondary)              │
│                                         │
│  💡 Tip: Keep the app open for         │
│     faster matching                    │
│                                         │
└─────────────────────────────────────────┘
```

---

## 3. Animation & Status

### 3.1 Pulsing Circles
- **Visual:** 3-5 circles pulsing in sequence
- **Purpose:** Indicate active processing
- **Animation:** Smooth, continuous pulse

### 3.2 Status Messages
- **Rotation:** Messages change every 10-15 seconds
- **Examples:**
  - "Analyzing potential teammates..."
  - "Found 3 promising matches..."
  - "Calculating compatibility scores..."
  - "Evaluating schedule overlap..."

### 3.3 Progress Indicator
- **Type:** Subtle progress bar (not time-based)
- **Purpose:** Visual feedback without false promises
- **Animation:** Subtle pulse or gradient movement

---

## 4. Information Display

### 4.1 Queue Position
- **Format:** "Queue Position: #12"
- **Update:** Real-time via WebSocket (every 30 seconds)
- **Purpose:** Show progress in queue

### 4.2 Estimated Time
- **Format:** "Estimated Time: 2-4 hours"
- **Calculation:** Based on historical matching times
- **Update:** Dynamic based on queue activity

### 4.3 Matching Criteria
- **Checklist:** What the algorithm is looking for
  - ✓ Similar skill level
  - ✓ Complementary strengths
  - ✓ Shared learning goals
  - ✓ Compatible schedules

---

## 5. Interactions

### 5.1 Real-time Updates
- **WebSocket Connection:** Live updates every 30 seconds
- **Queue Position:** Updates when others match or leave
- **Status Messages:** Change based on algorithm progress

### 5.2 Leave Queue
- **Button:** "Leave Queue" (secondary style)
- **Action:** Opens confirmation modal
- **Modal:** "Are you sure? You'll lose your position."
- **Options:** [Cancel] [Leave Queue]

---

## 6. States

### 6.1 Waiting
- Default state, animations active
- Queue position visible
- Status messages rotating

### 6.2 Matching
- "We found potential teammates! Finalizing..."
- Queue position may disappear
- Animation intensifies

### 6.3 Matched
- Celebration animation
- Auto-redirect to Match Found screen
- Success notification

### 6.4 Error
- "Something went wrong. [Retry]"
- Error message displayed
- Retry button available

---

## 7. Design Specifications

### 7.1 Components Used
- **Animation:** Pulsing circles, status message rotation
- **Progress Indicator:** Subtle progress bar
- **Information Cards:** Queue position, estimated time
- **Checklist:** Matching criteria display
- **Button:** Secondary (Leave Queue)
- **Modal:** Confirmation dialog

### 7.2 Visual Feedback
- **Active:** Animated, pulsing elements
- **Success:** Celebration animation on match
- **Error:** Red error message, retry button

---

## 8. Performance Requirements

### 8.1 Real-time Updates
- **NFR:** Match notification delivery ≤ 500ms via WebSocket
- **Design:** WebSocket connection for instant updates

### 8.2 Status Updates
- **Frequency:** Every 30 seconds
- **Method:** WebSocket push notifications

---

## 9. Accessibility

- **Screen Reader:** "Finding your team. Queue position 12. Estimated time 2 to 4 hours."
- **Status Announcements:** Screen reader announces status changes
- **Keyboard Navigation:** Tab to Leave Queue button

---

## 10. Related Pages

- **Previous:** [08-Assessment-Results](08-Assessment-Results.md) - User clicked "Find My Team"
- **Next:** [10-Match-Found](10-Match-Found.md) - When match is found
- **Exit:** [18-Solo-Dashboard](18-Solo-Dashboard.md) - User leaves queue

---

## 11. Acceptance Criteria

- [ ] Queue position updates in real-time
- [ ] Status messages rotate correctly
- [ ] Animation is smooth and not distracting
- [ ] Leave Queue confirmation works
- [ ] WebSocket connection maintains properly
- [ ] Match notification appears instantly
- [ ] Error handling works correctly

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 3.2.1 for detailed flow context.

