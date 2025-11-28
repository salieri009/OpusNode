# 07. AI Interview Interface

**Document:** TailCamp PRD - Page Design: AI Interview Interface  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The AI Interview Interface is the core assessment screen where users engage in a conversational interview with an AI. It features a split-screen layout with chat interface and real-time skill analysis panel.

**Page Type:** Authenticated  
**Complexity:** 🔥 High  
**Priority:** P0 (MVP)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 3.1.7
- **[F-001: AI Assessment](../../../03-features/F-001-AI-Assessment.md)** - **Core Feature:** Interactive chat interface, real-time analysis, skill heatmap (FR-1, FR-2, FR-3)
- [NFRs-Design Integration](../../../03-features/NFRs/02-NFRs-Design-Integration.md) - Performance requirements

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────────────────┐
│  [← Exit]                    Progress: 3/7 (43%)   │
├──────────────────┬──────────────────────────────────┤
│                  │                                  │
│  Chat Interface  │  Real-time Analysis Panel       │
│  (Left 60%)      │  (Right 40%)                    │
│                  │                                  │
│  ┌────────────┐  │  ┌──────────────────────────┐  │
│  │ 🤖 AI      │  │  │ Skill Heatmap            │  │
│  │            │  │  │                          │  │
│  │ What's     │  │  │ Backend:    ████░░ 0.7  │  │
│  │ your       │  │  │ Frontend:   ██░░░░ 0.3  │  │
│  │ experience │  │  │ AI/ML:      █░░░░░ 0.2  │  │
│  │ with       │  │  │ Mobile:     ░░░░░░ 0.1  │  │
│  │ REST APIs? │  │  │ DevOps:     ██░░░░ 0.4  │  │
│  └────────────┘  │  └──────────────────────────┘  │
│                  │                                  │
│  ┌────────────┐  │  ┌──────────────────────────┐  │
│  │ 👤 You     │  │  │ Estimated Level          │  │
│  │            │  │  │                          │  │
│  │ I've built │  │  │ ⭐⭐⭐ Intermediate      │  │
│  │ several    │  │  │                          │  │
│  │ APIs using │  │  │ Confidence: 75%          │  │
│  │ Node.js... │  │  └──────────────────────────┘  │
│  └────────────┘  │                                  │
│                  │                                  │
│  ┌────────────┐  │                                  │
│  │ [Type...]  │  │                                  │
│  │ [Send]     │  │                                  │
│  └────────────┘  │                                  │
│                  │                                  │
└──────────────────┴──────────────────────────────────┘
```

---

## 3. Chat Interface (Left 60%)

### 3.1 Message Bubbles
- **AI Messages:**
  - Left-aligned
  - Blue background (#0a95ff)
  - AI avatar/icon
  - Typing indicator: "AI is thinking..." with animated dots

- **User Messages:**
  - Right-aligned
  - Gray background (#f3f4f6)
  - User avatar/initials
  - Timestamp (optional, on hover)

### 3.2 Input Field
- **Auto-focus:** On question load
- **Character Limit:** 1000 characters
- **Submit:** "Send" button or Enter key
- **Disabled:** While AI is processing

### 3.3 Progress Bar
- **Location:** Top of screen
- **Display:** "Progress: 3/7 (43%)"
- **Visual:** Progress bar with percentage

---

## 4. Real-time Analysis Panel (Right 40%)

### 4.1 Skill Heatmap
- **Type:** Bar chart with color gradient
- **Colors:** Red (low) → Yellow (medium) → Green (high)
- **Update:** After each answer
- **Animation:** Smooth transition (300ms) when values change
- **Skills Shown:**
  - Backend Development
  - Frontend Development
  - AI/ML
  - Mobile Development
  - DevOps

### 4.2 Estimated Level
- **Display:** Star rating (⭐⭐⭐ Intermediate)
- **Confidence:** Percentage (e.g., "Confidence: 75%")
- **Update:** Dynamically as assessment progresses

---

## 5. Interactions

### 5.1 Question Flow
1. **Question Loading:** Typing indicator appears, input disabled
2. **User Types:** Input active, character counter visible
3. **User Submits:** "Sending..." button state, input disabled
4. **AI Processing:** Analysis panel animates, heatmap updates
5. **Next Question:** New question appears, cycle repeats

### 5.2 Exit Handling
- **Exit Button:** Confirmation modal
- **Modal Content:**
  - "Your progress will be saved. You can resume within 24 hours."
  - Options: [Cancel] [Save & Exit] [Continue Interview]

---

## 6. States

### 6.1 Question Loading
- Typing indicator: "AI is thinking..."
- Input field disabled
- Analysis panel shows previous state

### 6.2 User Typing
- Input active
- Character counter visible (X/1000)
- Send button enabled

### 6.3 Submitting
- "Sending..." button state
- Input disabled
- Loading spinner on send button

### 6.4 Processing
- Analysis panel animates
- Heatmap updates with new values
- Estimated level may change

### 6.5 Error
- Red error message in chat
- Retry button appears
- Input re-enabled

---

## 7. Error Handling

### 7.1 Network Error
- **Message:** "Connection lost. [Retry]"
- **Action:** Retry button re-sends last message

### 7.2 Timeout
- **Message:** "Taking longer than expected. [Continue waiting] or [Skip question]"
- **Options:** Wait or skip current question

### 7.3 Invalid Input
- **Message:** "Please provide a more detailed answer (min 20 characters)"
- **Validation:** Real-time character count

---

## 8. Mobile Adaptations

### 8.1 Layout
- **Desktop:** Split view (60% chat, 40% analysis)
- **Mobile:** Full-screen chat, swipe to view analysis panel
- **Tab Option:** Tab bar to switch between Chat and Analysis

### 8.2 Interactions
- **Swipe Gesture:** Swipe left to view analysis panel
- **Back Button:** Return to chat view

---

## 9. Performance Requirements

### 9.1 Response Time
- **NFR:** AI question generation ≤ 3 seconds (95th percentile)
- **Design:** Typing indicator manages expectations during wait

### 9.2 Real-time Updates
- **NFR:** Analysis updates after each answer
- **Design:** Smooth animations (300ms) for value changes

---

## 10. Design Specifications

### 10.1 Components Used
- **Chat Interface:** Message bubbles, input field, send button
- **Analysis Panel:** Bar chart, star rating, confidence indicator
- **Progress Bar:** Top navigation with progress
- **Modal:** Exit confirmation dialog

### 10.2 Animations
- **Message Appearance:** Fade in from bottom
- **Heatmap Update:** Smooth bar growth animation
- **Typing Indicator:** Animated dots

---

## 11. Accessibility

- **Keyboard Navigation:** Tab through messages, Enter to send
- **Screen Reader:** "AI question: [question text]. Your turn to answer."
- **Focus Management:** Auto-focus on input when new question loads
- **ARIA Labels:** "Chat interface", "Skill analysis panel"

---

## 12. Related Pages

- **Previous:** [06-Assessment-Intro](06-Assessment-Intro.md) - User started assessment
- **Next:** [08-Assessment-Results](08-Assessment-Results.md) - After final question
- **Exit:** [18-Solo-Dashboard](18-Solo-Dashboard.md) - User exits assessment

---

## 13. Acceptance Criteria

- [ ] Chat interface displays messages correctly
- [ ] Real-time analysis panel updates after each answer
- [ ] Typing indicator shows during AI processing
- [ ] Progress bar updates correctly
- [ ] Exit confirmation modal works
- [ ] Error handling works for network issues
- [ ] Mobile layout is responsive
- [ ] Performance meets 3-second response time

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 3.1.7 for detailed flow context.

