# Analytics & Event Tracking Plan

**Document:** TailCamp PRD - Analytics Tracking Plan  
**Version:** 1.0  
**Last Updated:** 2025-11-23

---

## 1. Overview

This document defines the event taxonomy, data schema, and tracking implementation for TailCamp analytics. It ensures consistent data collection across the platform to support product decisions and validate success metrics.

**Tools:** Mixpanel (primary), Google Analytics 4 (backup)

---

## 2. Event Taxonomy

### Naming Convention

**Format:** `[Category]_[Action]_[Object]`

**Example:** `assessment_complete_interview`, `matching_join_queue`

### Event Categories

| Category | Description | Examples |
|:---------|:------------|:---------|
| `page_view` | Navigation and page loads | `page_view_dashboard`, `page_view_workspace` |
| `auth` | Authentication events | `auth_signup`, `auth_login`, `auth_logout` |
| `assessment` | AI interview events | `assessment_start`, `assessment_answer`, `assessment_complete` |
| `matching` | Group formation events | `matching_join_queue`, `matching_found`, `matching_leave` |
| `project` | Project activity | `project_create`, `project_task_add`, `project_complete` |
| `curriculum` | Learning progress | `curriculum_view`, `curriculum_task_complete` |
| `portfolio` | Portfolio generation | `portfolio_generate`, `portfolio_export` |

---

## 3. Critical Events (Top Priority)

### User Lifecycle Events

```javascript
// Sign-up
mixpanel.track('auth_signup', {
  method: 'email',  // 'email' | 'google' | 'github'
  referral_source: 'organic',  // 'organic' | 'referral' | 'ad'
  persona_guess: null  // Will be set after assessment
});

// Assessment Complete
mixpanel.track('assessment_complete', {
  duration_seconds: 620,
  questions_answered: 7,
  assessment_id: 'uuid',
  skill_scores: {
    backend: 0.7,
    frontend: 0.3
  },
  assessed_level: 'intermediate'  // 'beginner' | 'intermediate' | 'advanced'
});

// Match Found
mixpanel.track('matching_found', {
  match_id: 'uuid',
  group_id: 'uuid',
  wait_time_seconds: 7200,  // 2 hours
  match_score: 0.92,
  group_size: 4,
  shared_goals: ['backend', 'api_design']
});

// Project Complete
mixpanel.track('project_complete', {
  project_id: 'uuid',
  group_id: 'uuid',
  duration_days: 45,
  tech_stack: ['Next.js', 'NestJS', 'PostgreSQL'],
  tasks_completed: 23,
  commits_count: 142  // From GitHub API
});
```

---

## 4. User Properties (Profiles)

### Set on Sign-up

```javascript
mixpanel.people.set({
  $name: 'John Doe',
  $email: 'john@example.com',
  $created: '2025-01-15T10:00:00Z',
  signup_source: 'landing_page',
  persona: null  // Updated after assessment
});
```

### Updated After Assessment

```javascript
mixpanel.people.set({
  persona: 'career_switcher',  // From assessment
  skill_level: 'intermediate',
  primary_focus: 'backend',
  learning_goals: ['build_api', 'deploy_production']
});
```

### Incremented on Actions

```javascript
// When user completes a task
mixpanel.people.increment('tasks_completed', 1);
mixpanel.people.increment('total_study_minutes', 45);

// When user joins a group
mixpanel.people.increment('groups_joined', 1);
```

---

## 5. Funnel Tracking

### Onboarding Funnel

**Goal:** Measure drop-off from sign-up to first group formation.

**Steps:**
1.  `auth_signup` → **100%** (baseline)
2.  `assessment_start` → Target: **>85%**
3.  `assessment_complete` → Target: **>70%**
4.  `matching_join_queue` → Target: **>80%** of completers
5.  `matching_found` → Target: **>90%** within 48hrs
6.  `project_create` → Target: **>90%** of matched groups

**Mixpanel Funnel Query:**
```
Funnel:
  - auth_signup (baseline)
  - assessment_complete (within 7 days)
  - matching_join_queue (within 1 day of assessment)
  - matching_found (within 2 days of queue join)
  - project_create (within 2 days of match)
```

### Retention Cohorts

**Goal:** Track Week 1, Week 4, Month 3 retention by signup cohort.

**Cohort Definition:** All users who signed up in a given week.  
**Return Event:** `page_view_dashboard` OR `project_task_add` OR `curriculum_task_complete`

**Mixpanel Report:** Retention Analysis → `auth_signup` → `[return event]` → Group by `signup_week`

---

## 6. A/B Testing Events

### Feature Flags

Track exposure and conversion for experiments.

```javascript
// When user sees a variant
mixpanel.track('experiment_exposure', {
  experiment_name: 'assessment_ui_v2',
  variant: 'control',  // 'control' | 'treatment_a' | 'treatment_b'
  user_id: 'uuid'
});

// When user converts (completes desired action)
mixpanel.track('experiment_conversion', {
  experiment_name: 'assessment_ui_v2',
  variant: 'control',
  conversion_type: 'assessment_complete'
});
```

---

## 7. Performance Metrics

### Page Load Times

```javascript
// On every page load
mixpanel.track('page_performance', {
  page: 'dashboard',
  load_time_ms: 1200,
  ttfb_ms: 300,  // Time to First Byte
  fcp_ms: 800,   // First Contentful Paint
  device_type: 'desktop'  // 'mobile' | 'tablet' | 'desktop'
});
```

**Aggregation in Mixpanel:** Average `load_time_ms` by `page`, grouped by `device_type`.

---

## 8. Data Governance

### PII (Personally Identifiable Information)

**Never track:**
-   Full credit card numbers
-   Social Security Numbers
-   Passwords

**Hash before sending:**
-   Email addresses (use SHA-256 hash as `user_id` in analytics)
-   IP addresses (optional: use for geo-location only, then discard)

### GDPR Compliance

-   **Consent:** Show cookie banner, require opt-in for analytics.
-   **Right to Deletion:** Provide `mixpanel.people.delete_user()` in user settings.
-   **Data Retention:** Auto-delete raw event data after 2 years.

---

## 9. Implementation Checklist

- [ ] Install Mixpanel SDK (frontend + backend)
- [ ] Define `user_id` strategy (UUID from database)
- [ ] Implement critical lifecycle events (`auth_signup`, `assessment_complete`, `matching_found`)
- [ ] Set up funnel reports (Onboarding, Project Completion)
- [ ] Create retention cohort reports
- [ ] Configure alerts (e.g., "Assessment completion rate drops below 70%")
- [ ] Document event changes in this file (change log at bottom)

---

**Next Step:** Review [Development Roadmap](../06-roadmap/development-roadmap.md) to plan implementation timeline.
