# Database Schema

**Document:** TailCamp PRD - Database Schema  
**Version:** 2.0  
**Last Updated:** 2025-11-28  

---

## 1. Overview

This document defines the database schema for the TailCamp (OpusNode) platform, utilizing **PostgreSQL** as the primary relational database. It details the core tables, relationships, and indexing strategies to ensure high performance, data integrity, and scalability.

**Related Documents:**
- [01-System-Architecture](01-System-Architecture.md)
- [02-Technology-Stack](02-Technology-Stack.md)

---

## 2. Core Tables

### 2.1 Users Table
Stores fundamental user information and authentication credentials.

```sql
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) UNIQUE NOT NULL,
  name VARCHAR(100) NOT NULL,
  password_hash VARCHAR(255) NOT NULL, -- Bcrypt hash
  role VARCHAR(50) DEFAULT 'user', -- ENUM: 'user', 'admin', 'moderator'
  auth_provider VARCHAR(50) DEFAULT 'local', -- 'local', 'google', 'github'
  provider_id VARCHAR(255), -- External ID for OAuth
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_role ON users(role);
```

**Relationships:**
-   Referenced by `assessments.user_id`
-   Referenced by `group_members.user_id`
-   Referenced by `curriculums.user_id`

### 2.2 Assessments Table [F-001]
Stores the results of AI-driven skill assessments.

```sql
CREATE TABLE assessments (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  scores JSONB NOT NULL, -- Detailed score breakdown (e.g., {"backend": 0.8})
  level VARCHAR(50) NOT NULL, -- ENUM: 'beginner', 'intermediate', 'advanced'
  collaboration_style VARCHAR(50), -- ENUM: 'leader', 'builder', 'researcher'
  learning_goals TEXT[], -- Array of strings
  recommended_paths TEXT[], -- Array of strings
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

CREATE INDEX idx_assessments_user_id ON assessments(user_id);
CREATE INDEX idx_assessments_level ON assessments(level);
CREATE INDEX idx_assessments_scores ON assessments USING GIN(scores); -- GIN index for JSONB querying
```

**JSONB Schema (scores):**
```json
{
  "backend": 0.7,
  "frontend": 0.2,
  "ai_ml": 0.3,
  "mobile": 0.1,
  "devops": 0.4
}
```

### 2.3 Groups Table [F-002]
Manages learning group entities formed by the matching algorithm.

```sql
CREATE TABLE groups (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name VARCHAR(200),
  status VARCHAR(50) DEFAULT 'active', -- ENUM: 'forming', 'active', 'completed', 'archived'
  matching_score JSONB, -- Metadata about why this group was formed
  project_repo_url VARCHAR(255), -- Link to GitHub Repository
  communication_channel_url VARCHAR(255), -- Link to Slack/Discord
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

CREATE INDEX idx_groups_status ON groups(status);
```

### 2.4 Group Members Table
Links users to groups with specific roles, implementing a many-to-many relationship.

```sql
CREATE TABLE group_members (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  group_id UUID REFERENCES groups(id) ON DELETE CASCADE,
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  role VARCHAR(50) DEFAULT 'member', -- ENUM: 'leader', 'member'
  joined_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  UNIQUE(group_id, user_id) -- Prevent duplicate membership
);

CREATE INDEX idx_group_members_group_id ON group_members(group_id);
CREATE INDEX idx_group_members_user_id ON group_members(user_id);
```

### 2.5 Projects Table [F-004]
Stores information about the projects undertaken by groups.

```sql
CREATE TABLE projects (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  group_id UUID REFERENCES groups(id) ON DELETE CASCADE,
  title VARCHAR(255) NOT NULL,
  description TEXT,
  status VARCHAR(50) DEFAULT 'planning', -- ENUM: 'planning', 'in_progress', 'review', 'completed'
  repository_url VARCHAR(255),
  demo_url VARCHAR(255),
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

CREATE INDEX idx_projects_group_id ON projects(group_id);
```

## 3. Design Considerations

### 3.1 JSONB Usage
-   **Flexibility:** `scores` and `matching_score` use JSONB to allow for evolving schema requirements without altering table structure.
-   **Indexing:** GIN indexes are applied to JSONB columns to ensure efficient querying of nested data.

### 3.2 Timezones
-   All timestamps are stored in `TIMESTAMP WITH TIME ZONE` (UTC) to ensure consistency across different geographical regions.

### 3.3 Data Integrity
-   **Foreign Keys:** Strict foreign key constraints with `ON DELETE CASCADE` ensure referential integrity (e.g., deleting a user removes their assessment data).
-   **Unique Constraints:** Applied where necessary (e.g., `email`, `group_id + user_id`) to prevent data duplication.

