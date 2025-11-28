# 01. Landing Page

**Document:** TailCamp PRD - Page Design: Landing Page  
**Version:** 1.0  
**Last Updated:** 2025-11-28

---

## 1. Overview

The Landing Page is the primary entry point for new users, providing service introduction and value proposition. It serves as the first impression and conversion point for user acquisition.

**Page Type:** Public (No authentication required)  
**Complexity:** 🟢 Low  
**Priority:** P0 (MVP)

**Related Documents:**
- [02-User-Journey-Flows](../../02-User-Journey-Flows.md) - Section 3.1.1
- [01-UX-UI-Principles](../../01-UX-UI-Principles.md) - Design system
- **Feature:** None (Entry point page, introduces all features)

---

## 2. Page Structure

### 2.1 Layout

```
┌─────────────────────────────────────────┐
│  [Logo]              [Login] [Sign Up]  │
├─────────────────────────────────────────┤
│                                         │
│         Hero Section                    │
│    "Find Your Perfect Learning Team"   │
│                                         │
│    [Watch Demo] [Get Started]          │
│                                         │
│  Features Grid (3 columns)              │
│  - AI Assessment                        │
│  - Smart Matching                       │
│  - Portfolio Builder                    │
│                                         │
│  Testimonials Carousel                  │
│  FAQ Accordion                          │
│                                         │
└─────────────────────────────────────────┘
```

### 2.2 Sections

1. **Header:** Logo, Navigation (Login, Sign Up)
2. **Hero Section:** Value proposition, primary CTAs
3. **Features Grid:** 3-column showcase of key features
4. **Testimonials:** User testimonials carousel
5. **FAQ:** Accordion-style frequently asked questions
6. **Footer:** Links, legal, social media

---

## 3. Interactions

### 3.1 Primary Actions

- **"Get Started" Button:** Navigate to `/signup` or smooth scroll to sign-up form
- **"Watch Demo" Button:** Open modal with embedded video (YouTube/Vimeo)
- **"Sign Up" (Header):** Navigate to `/signup`
- **"Login" (Header):** Navigate to `/login`

### 3.2 Scroll Behavior

- **Sticky Header:** Appears after 100px scroll, reduced opacity
- **Smooth Scrolling:** For anchor links to sections

### 3.3 Mobile Adaptations

- **Hamburger Menu:** Replaces top navigation on mobile
- **Stacked Layout:** Features grid becomes single column
- **Touch-Optimized:** Larger touch targets for mobile

---

## 4. States

### 4.1 Default State
- Hero section visible, CTA buttons prominent
- All sections loaded and visible

### 4.2 Loading State
- Skeleton screens for testimonials carousel
- Progressive image loading

### 4.3 Error States
- Video fails to load → Show thumbnail with "Play" button
- Network error → Retry button appears

---

## 5. Design Specifications

### 5.1 Components Used

- **Header:** Sticky navigation bar
- **Hero:** Large heading, subheading, dual CTAs
- **Feature Cards:** Icon, title, description
- **Testimonial Cards:** Avatar, quote, name
- **FAQ Accordion:** Question, expandable answer

### 5.2 Responsive Breakpoints

- **Mobile (< 768px):** Single column, hamburger menu
- **Tablet (768-1024px):** Two-column features grid
- **Desktop (> 1024px):** Three-column features grid, full navigation

---

## 6. Content Requirements

### 6.1 Hero Section

- **Headline:** "Find Your Perfect Learning Team"
- **Subheadline:** Value proposition (1-2 sentences)
- **CTAs:** "Get Started" (primary), "Watch Demo" (secondary)

### 6.2 Features Grid

- **Feature 1:** AI Assessment - Description
- **Feature 2:** Smart Matching - Description
- **Feature 3:** Portfolio Builder - Description

### 6.3 Testimonials

- Minimum 3 testimonials
- Include: User name, role, quote, avatar (optional)

### 6.4 FAQ

- Common questions about service, pricing, matching process

---

## 7. Performance Targets

- **First Contentful Paint:** < 1.5s
- **Largest Contentful Paint:** < 2.5s
- **Time to Interactive:** < 3.5s

---

## 8. Accessibility

- **WCAG 2.1 AA:** All text meets contrast requirements
- **Keyboard Navigation:** All interactive elements accessible via Tab
- **Screen Reader:** Semantic HTML, ARIA labels for dynamic content

---

## 9. Related Pages

- **Next:** [02-Sign-Up](02-Sign-Up.md) - User clicks "Get Started"
- **Alternative:** [16-Login-Page](16-Login-Page.md) - User clicks "Login"

---

## 10. Acceptance Criteria

- [ ] Page loads within 2 seconds
- [ ] All CTAs are functional and navigate correctly
- [ ] Video modal opens and plays correctly
- [ ] Mobile layout is fully responsive
- [ ] All interactive elements are keyboard accessible

---

**Next Step:** Review [02-User-Journey-Flows](../02-User-Journey-Flows.md) Section 3.1.1 for detailed flow context.

