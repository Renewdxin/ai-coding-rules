# Spec-Driven Development Example Demo

## Complete Workflow Demonstration

### User Input Example
**User**: "使用 Vue + TypeScript 开发一个文章评论系统"

---

## Phase 1: Requirements Generation

### AI Response:
```markdown
# 🚀 Spec-Driven Development Session Started

## Session Overview
- **Project**: Article Comment System
- **Technology Stack**: Vue.js + TypeScript
- **Complexity**: Medium
- **Estimated Duration**: 2-3 weeks

## Next Steps
1. Generate detailed requirements document
2. Wait for user approval
3. Proceed to design phase

**Shall I proceed with requirements generation?**
```

### Generated Requirements Document (`requirements.md`):
```markdown
# Article Comment System - Requirements Document

## Project Overview
Develop a modern article comment system using Vue.js and TypeScript that allows users to read articles, post comments, reply to comments, and manage their interactions.

## User Stories

### Core User Stories
- **US001**: As a reader, I want to view articles so that I can read content
- **US002**: As a registered user, I want to post comments so that I can share my thoughts
- **US003**: As a registered user, I want to reply to comments so that I can engage in discussions
- **US004**: As a registered user, I want to edit my comments so that I can correct mistakes
- **US005**: As a registered user, I want to delete my comments so that I can remove unwanted content
- **US006**: As a moderator, I want to moderate comments so that I can maintain content quality

### Authentication Stories
- **US007**: As a user, I want to register an account so that I can participate in discussions
- **US008**: As a user, I want to login so that I can access my account
- **US009**: As a user, I want to logout so that I can secure my account

## Functional Requirements

### Article Management
- Display article content with proper formatting
- Show article metadata (title, author, date, tags)
- Support article categories and search

### Comment System
- Hierarchical comment structure (nested replies)
- Real-time comment posting and updates
- Comment sorting (newest, oldest, most liked)
- Comment pagination for performance

### User Management
- User registration and authentication
- User profile management
- Role-based permissions (user, moderator, admin)

### Interaction Features
- Like/dislike comments
- Report inappropriate comments
- Comment notifications
- User mention system (@username)

## Non-Functional Requirements

### Performance
- Page load time < 2 seconds
- Comment posting response < 500ms
- Support 1000+ concurrent users

### Security
- Input sanitization and XSS protection
- CSRF protection
- Rate limiting for comment posting
- Secure authentication (JWT tokens)

### Usability
- Responsive design (mobile-first)
- Accessibility compliance (WCAG 2.1)
- Intuitive user interface
- Keyboard navigation support

## Technical Constraints
- Must use Vue.js 3 with Composition API
- TypeScript for type safety
- Modern browser support (ES2020+)
- RESTful API design

## Clarification Questions
1. Do you need real-time notifications for new comments?
2. Should comments support rich text formatting (bold, italic, links)?
3. Do you need social login integration (Google, GitHub)?
4. What's the expected comment volume per article?
5. Do you need comment moderation workflow?
6. Should the system support file attachments in comments?

## Acceptance Criteria

### US002: Post Comments
**Given** a registered user is viewing an article
**When** they enter a comment and click "Post Comment"
**Then** the comment should appear immediately below the article
**And** the comment should be saved to the database
**And** the user should receive confirmation

### US003: Reply to Comments
**Given** a user is viewing comments on an article
**When** they click "Reply" on a specific comment
**Then** a reply form should appear below that comment
**And** when submitted, the reply should be nested under the original comment

## Out of Scope (V1)
- Advanced rich text editor
- Comment analytics and insights
- Multi-language support
- Comment export functionality
- Advanced spam detection AI
```

### User Approval Checkpoint:
```markdown
## 📋 Requirements Review Checkpoint

**Generated**: requirements.md (2,847 words)

**Key Features Identified**:
✅ Hierarchical comment system
✅ User authentication
✅ Real-time interactions
✅ Moderation capabilities
✅ Responsive design

**Please review the requirements document and confirm**:
1. Are all required features covered?
2. Any missing functionality?
3. Any features to remove or modify?
4. Ready to proceed to design phase?

**User Response Required**: (approve/modify/questions)
```

---

## Phase 2: Design Documentation

### User Approval: "Approved, proceed to design"

### Generated Design Document (`design.md`):
```markdown
# Article Comment System - Design Document

## Architecture Overview

### System Architecture
```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Vue.js SPA    │    │   Express API   │    │   PostgreSQL    │
│                 │    │                 │    │                 │
│ - Components    │◄──►│ - REST Routes   │◄──►│ - Articles      │
│ - Stores        │    │ - Middleware    │    │ - Comments      │
│ - Services      │    │ - Auth Logic    │    │ - Users         │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

### Component Architecture
```
App.vue
├── Header.vue
├── ArticleView.vue
│   ├── ArticleContent.vue
│   └── CommentSection.vue
│       ├── CommentForm.vue
│       ├── CommentList.vue
│       └── CommentItem.vue
│           ├── CommentActions.vue
│           └── ReplyForm.vue
├── AuthModal.vue
└── Footer.vue
```

## Technical Stack

### Frontend Stack
- **Framework**: Vue.js 3.4+ with Composition API
- **Language**: TypeScript 5.0+
- **State Management**: Pinia for global state
- **Routing**: Vue Router 4
- **HTTP Client**: Axios with interceptors
- **UI Framework**: Tailwind CSS + Headless UI
- **Build Tool**: Vite 5.0+
- **Testing**: Vitest + Vue Test Utils

**Rationale**: Vue 3 with Composition API provides excellent TypeScript support and performance. Pinia offers better DevTools and TypeScript integration than Vuex.

### Backend Stack
- **Runtime**: Node.js 18+ LTS
- **Framework**: Express.js 4.18+
- **Language**: TypeScript
- **Database**: PostgreSQL 15+
- **ORM**: Prisma 5.0+
- **Authentication**: JWT with refresh tokens
- **Validation**: Zod for schema validation
- **Testing**: Jest + Supertest

**Rationale**: Express provides flexibility, Prisma offers excellent TypeScript support and migrations, PostgreSQL handles hierarchical data well.

## Database Design

### Entity Relationship Diagram
```sql
Users (1) ──── (N) Comments
Articles (1) ──── (N) Comments  
Comments (1) ──── (N) Comments (self-referencing for replies)
Users (N) ──── (N) CommentLikes
```

### Schema Design
```typescript
// Prisma Schema
model User {
  id        String   @id @default(cuid())
  email     String   @unique
  username  String   @unique
  password  String
  role      Role     @default(USER)
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  
  comments     Comment[]
  commentLikes CommentLike[]
}

model Article {
  id          String   @id @default(cuid())
  title       String
  content     String
  slug        String   @unique
  authorId    String
  publishedAt DateTime @default(now())
  
  comments Comment[]
}

model Comment {
  id        String   @id @default(cuid())
  content   String
  authorId  String
  articleId String
  parentId  String?  // For nested replies
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  
  author   User      @relation(fields: [authorId], references: [id])
  article  Article   @relation(fields: [articleId], references: [id])
  parent   Comment?  @relation("CommentReplies", fields: [parentId], references: [id])
  replies  Comment[] @relation("CommentReplies")
  likes    CommentLike[]
}
```

## API Design

### Authentication Endpoints
```typescript
POST /api/auth/register
POST /api/auth/login
POST /api/auth/logout
POST /api/auth/refresh
GET  /api/auth/me
```

### Article Endpoints
```typescript
GET    /api/articles           // List articles
GET    /api/articles/:slug     // Get article by slug
```

### Comment Endpoints
```typescript
GET    /api/articles/:id/comments     // Get comments for article
POST   /api/articles/:id/comments     // Create comment
PUT    /api/comments/:id              // Update comment
DELETE /api/comments/:id              // Delete comment
POST   /api/comments/:id/like         // Like/unlike comment
```

### Request/Response Examples
```typescript
// POST /api/articles/:id/comments
interface CreateCommentRequest {
  content: string;
  parentId?: string;
}

interface CommentResponse {
  id: string;
  content: string;
  author: {
    id: string;
    username: string;
  };
  createdAt: string;
  updatedAt: string;
  likesCount: number;
  repliesCount: number;
  isLiked: boolean;
  canEdit: boolean;
  canDelete: boolean;
}
```

## State Management Design

### Pinia Stores
```typescript
// stores/auth.ts
export const useAuthStore = defineStore('auth', () => {
  const user = ref<User | null>(null)
  const isAuthenticated = computed(() => !!user.value)
  
  const login = async (credentials: LoginCredentials) => { /* */ }
  const logout = async () => { /* */ }
  const register = async (userData: RegisterData) => { /* */ }
  
  return { user, isAuthenticated, login, logout, register }
})

// stores/comments.ts
export const useCommentsStore = defineStore('comments', () => {
  const comments = ref<Comment[]>([])
  const loading = ref(false)
  
  const fetchComments = async (articleId: string) => { /* */ }
  const createComment = async (commentData: CreateCommentData) => { /* */ }
  const updateComment = async (id: string, content: string) => { /* */ }
  
  return { comments, loading, fetchComments, createComment, updateComment }
})
```

## Security Considerations

### Frontend Security
- **XSS Prevention**: Sanitize user input, use v-text instead of v-html
- **CSRF Protection**: Include CSRF tokens in API requests
- **Content Security Policy**: Implement strict CSP headers
- **Input Validation**: Client-side validation with server-side verification

### Backend Security
- **Authentication**: JWT with short expiry + refresh token rotation
- **Authorization**: Role-based access control (RBAC)
- **Rate Limiting**: Implement rate limiting for comment posting
- **Input Sanitization**: Use Zod for request validation
- **SQL Injection Prevention**: Prisma ORM provides protection

## Performance Optimization

### Frontend Performance
- **Code Splitting**: Route-based code splitting with Vue Router
- **Lazy Loading**: Lazy load comment sections and replies
- **Virtual Scrolling**: For large comment lists
- **Caching**: HTTP caching with proper cache headers
- **Bundle Optimization**: Tree shaking and minification

### Backend Performance
- **Database Indexing**: Index on articleId, authorId, createdAt
- **Query Optimization**: Use Prisma's include/select for efficient queries
- **Pagination**: Implement cursor-based pagination for comments
- **Caching**: Redis for session storage and frequently accessed data

## Risk Analysis

### Technical Risks
1. **Nested Comment Performance**: Deep nesting may cause performance issues
   - **Mitigation**: Limit nesting depth to 5 levels, implement pagination
   
2. **Real-time Updates**: WebSocket complexity for live comments
   - **Mitigation**: Start with polling, upgrade to WebSockets in v2
   
3. **Spam and Abuse**: Comment spam and inappropriate content
   - **Mitigation**: Rate limiting, content moderation, user reporting

### Scalability Risks
1. **Database Growth**: Large comment volumes may slow queries
   - **Mitigation**: Proper indexing, archiving old comments
   
2. **Concurrent Users**: High concurrent comment posting
   - **Mitigation**: Database connection pooling, horizontal scaling

## Implementation Phases

### Phase 1: Core Infrastructure (Week 1)
- Project setup and configuration
- Database schema and migrations
- Basic authentication system
- Article display functionality

### Phase 2: Comment System (Week 2)
- Comment CRUD operations
- Nested reply functionality
- Comment listing and pagination
- Basic moderation features

### Phase 3: Enhanced Features (Week 3)
- Like/dislike functionality
- User profiles and management
- Advanced moderation tools
- Performance optimizations

### Phase 4: Polish and Deploy (Week 4)
- UI/UX improvements
- Testing and bug fixes
- Security audit
- Production deployment
```

### Design Approval Checkpoint:
```markdown
## 🏗️ Design Review Checkpoint

**Generated**: design.md (4,123 words)

**Architecture Highlights**:
✅ Vue 3 + TypeScript + Pinia stack
✅ PostgreSQL with Prisma ORM
✅ JWT authentication with refresh tokens
✅ Hierarchical comment structure
✅ Comprehensive security measures

**Key Design Decisions**:
- Nested comments limited to 5 levels for performance
- Cursor-based pagination for scalability
- Role-based access control for moderation
- Client-side and server-side validation

**Ready to proceed to task breakdown? (y/n)**
```

---

## Phase 3: Task Breakdown

### User Approval: "Yes, proceed"

### Generated Task List (`tasks.md`):
```markdown
# Article Comment System - Task Breakdown

## Development Phases Overview
- **Phase 1**: Project Setup & Infrastructure (8 tasks)
- **Phase 2**: Authentication System (6 tasks)  
- **Phase 3**: Article Management (4 tasks)
- **Phase 4**: Comment System Core (10 tasks)
- **Phase 5**: Advanced Features (8 tasks)
- **Phase 6**: Testing & Deployment (6 tasks)

**Total Tasks**: 42 | **Estimated Time**: 3-4 weeks

---

## Phase 1: Project Setup & Infrastructure

### 🚀 Task 1.1: Initialize Frontend Project
- **Priority**: Critical
- **Estimated Time**: 45 minutes
- **Dependencies**: None
- **Assignee**: AI
- **Status**: Ready to Start

**Deliverables**:
- Vue 3 + TypeScript project with Vite
- Tailwind CSS configuration
- ESLint + Prettier setup
- Basic project structure

**Acceptance Criteria**:
- [x] Project builds without errors
- [x] TypeScript strict mode enabled
- [x] Hot reload working
- [x] Linting rules configured

**[▶️ Start Task]**

---

### 🚀 Task 1.2: Initialize Backend Project  
- **Priority**: Critical
- **Estimated Time**: 45 minutes
- **Dependencies**: None
- **Assignee**: AI
- **Status**: Ready to Start

**Deliverables**:
- Express + TypeScript server
- Prisma ORM setup
- Environment configuration
- Basic middleware setup

**Acceptance Criteria**:
- [x] Server starts on specified port
- [x] TypeScript compilation working
- [x] Environment variables loaded
- [x] Basic error handling middleware

**[▶️ Start Task]**

---

### 🚀 Task 1.3: Database Schema Design
- **Priority**: Critical  
- **Estimated Time**: 1 hour
- **Dependencies**: Task 1.2
- **Assignee**: AI
- **Status**: Queued

**Deliverables**:
- Prisma schema file
- Database migrations
- Seed data script
- ER diagram documentation

**Acceptance Criteria**:
- [x] All entities properly defined
- [x] Relationships correctly established
- [x] Indexes on performance-critical fields
- [x] Migration runs successfully

**[⏸️ Queued]**

---

### 🚀 Task 1.4: API Route Structure
- **Priority**: High
- **Estimated Time**: 30 minutes  
- **Dependencies**: Task 1.2
- **Assignee**: AI
- **Status**: Queued

**Deliverables**:
- Express router setup
- Route organization structure
- Middleware chain configuration
- API versioning setup

**[⏸️ Queued]**

---

## Phase 2: Authentication System

### 🔐 Task 2.1: JWT Authentication Implementation
- **Priority**: Critical
- **Estimated Time**: 2 hours
- **Dependencies**: Task 1.3, Task 1.4
- **Assignee**: AI
- **Status**: Queued

**Deliverables**:
- JWT token generation/validation
- Refresh token mechanism
- Auth middleware
- Password hashing utilities

**Acceptance Criteria**:
- [x] Secure password hashing (bcrypt)
- [x] JWT tokens with proper expiry
- [x] Refresh token rotation
- [x] Auth middleware protects routes

**[⏸️ Queued]**

---

### 🔐 Task 2.2: User Registration API
- **Priority**: Critical
- **Estimated Time**: 1.5 hours
- **Dependencies**: Task 2.1
- **Assignee**: AI  
- **Status**: Queued

**Deliverables**:
- Registration endpoint
- Input validation (Zod)
- Duplicate email/username check
- Welcome email integration

**[⏸️ Queued]**

---

## Phase 4: Comment System Core

### 💬 Task 4.1: Comment Model & API
- **Priority**: Critical
- **Estimated Time**: 2 hours
- **Dependencies**: Task 2.1, Task 3.2
- **Assignee**: AI
- **Status**: Queued

**Deliverables**:
- Comment CRUD endpoints
- Nested comment support
- Comment validation
- Permission checks

**Acceptance Criteria**:
- [x] Create/read/update/delete comments
- [x] Nested replies up to 5 levels
- [x] Author can edit/delete own comments
- [x] Moderators can manage all comments

**[⏸️ Queued]**

---

### 💬 Task 4.2: Comment Vue Components
- **Priority**: Critical
- **Estimated Time**: 3 hours
- **Dependencies**: Task 4.1
- **Assignee**: AI
- **Status**: Queued

**Deliverables**:
- CommentSection.vue
- CommentItem.vue  
- CommentForm.vue
- ReplyForm.vue

**Acceptance Criteria**:
- [x] Display comments hierarchically
- [x] Real-time comment posting
- [x] Edit/delete functionality
- [x] Reply to comments

**[⏸️ Queued]**

---

## Task Execution Queue

### Current Queue (User Configurable)
1. **Task 1.1** - Initialize Frontend Project ⚡ (Ready)
2. **Task 1.2** - Initialize Backend Project ⚡ (Ready)  
3. **Task 1.3** - Database Schema Design (Waiting for 1.2)
4. **Task 1.4** - API Route Structure (Waiting for 1.2)

### Parallel Execution Opportunities
- Tasks 1.1 and 1.2 can run in parallel
- Frontend tasks (2.3, 2.4) can run parallel to backend tasks (2.1, 2.2)
- Testing tasks can run parallel to documentation tasks

### Critical Path
```
1.2 → 1.3 → 2.1 → 2.2 → 4.1 → 4.2 → 5.1 → 6.1
```

**Critical Path Duration**: 18.5 hours
**With Parallel Execution**: 14 hours

---

## Task Management Commands

### Start Next Task
**Command**: "Start next task" or "Begin Task 1.1"
**AI Response**: Detailed task execution with real-time progress

### Modify Task Queue  
**Command**: "Move Task 2.1 to priority" or "Skip Task 1.4"
**AI Response**: Updated queue with new priorities

### Task Status Check
**Command**: "Show task status" or "What's the current progress?"
**AI Response**: Comprehensive progress report with completion percentages

### Add Custom Task
**Command**: "Add task: Implement dark mode toggle"
**AI Response**: Task analysis, estimation, and queue insertion
```

### Task Breakdown Approval:
```markdown
## 📋 Task Breakdown Review

**Generated**: tasks.md with 42 detailed tasks
**Total Estimated Time**: 3-4 weeks
**Critical Path**: 14 hours with parallel execution

**Task Categories**:
- 🚀 Infrastructure: 8 tasks
- 🔐 Authentication: 6 tasks  
- 📄 Articles: 4 tasks
- 💬 Comments: 10 tasks
- ⭐ Features: 8 tasks
- 🧪 Testing: 6 tasks

**Ready to begin execution? Which task would you like to start with?**
- Option 1: Follow recommended order (Task 1.1)
- Option 2: Start with specific task
- Option 3: Modify task priorities first

**Your choice**: [User input required]
```

---

## Phase 4: Execution Example

### User Choice: "Start with Task 1.1"

### Task Execution in Progress:
```markdown
## 🔄 Task 1.1 Execution: Initialize Frontend Project

**Status**: In Progress 🔄
**Started**: 2025-08-01 14:30:00
**Estimated Completion**: 15:15:00
**Progress**: 60% Complete

### Current Subtask: Setting up Tailwind CSS ⚡

### Completed Steps:
- [x] Create Vue 3 + TypeScript project with Vite ✅
- [x] Install and configure TypeScript strict mode ✅  
- [x] Setup ESLint with Vue and TypeScript rules ✅
- [x] Configure Prettier for code formatting ✅
- [x] Install Tailwind CSS and dependencies ✅
- [ ] Configure Tailwind CSS with Vue 🔄 (Current)
- [ ] Create basic project structure
- [ ] Setup development scripts
- [ ] Verify hot reload functionality

### Generated Files:
```
frontend/
├── package.json ✅
├── tsconfig.json ✅
├── vite.config.ts ✅
├── .eslintrc.js ✅
├── .prettierrc ✅
├── tailwind.config.js 🔄
├── src/
│   ├── main.ts ✅
│   ├── App.vue ✅
│   └── style.css 🔄
└── index.html ✅
```

### Next Steps:
1. Complete Tailwind configuration
2. Create component directory structure
3. Setup routing foundation
4. Test development server

**Continue with current subtask? (y/n)**
```

### Task Completion:
```markdown
## ✅ Task 1.1 Completed: Initialize Frontend Project

**Status**: Completed ✅
**Duration**: 42 minutes (3 minutes under estimate)
**Completed**: 2025-08-01 15:12:00

### Final Deliverables:
- [x] Vue 3 + TypeScript project with Vite ✅
- [x] Tailwind CSS fully configured ✅
- [x] ESLint + Prettier setup ✅
- [x] Basic project structure created ✅
- [x] Hot reload verified working ✅

### Generated Project Structure:
```
frontend/
├── package.json
├── tsconfig.json
├── vite.config.ts
├── tailwind.config.js
├── .eslintrc.js
├── .prettierrc
├── src/
│   ├── main.ts
│   ├── App.vue
│   ├── components/
│   ├── views/
│   ├── stores/
│   ├── services/
│   ├── types/
│   └── assets/
├── public/
└── index.html
```

### Quality Verification:
- ✅ Project builds without errors
- ✅ TypeScript strict mode enabled
- ✅ Linting passes all checks
- ✅ Hot reload working correctly
- ✅ Tailwind classes rendering properly

### Updated Task Queue:
- [x] **Task 1.1** - Initialize Frontend Project ✅ (Completed)
- [ ] **Task 1.2** - Initialize Backend Project 🔄 (Next)
- [ ] **Task 1.3** - Database Schema Design (Queued)

**Ready to proceed with Task 1.2? (y/n)**
```

---

## Documentation Persistence

### Generated `.spec` Folder Structure:
```
project-root/
├── .spec/
│   ├── requirements.md ✅
│   ├── design.md ✅
│   ├── tasks.md ✅
│   ├── execution-log.md 🔄
│   ├── iterations/
│   │   └── v1.0/
│   │       ├── requirements-v1.0.md
│   │       ├── design-v1.0.md
│   │       └── tasks-v1.0.md
│   └── assets/
│       ├── architecture-diagram.png
│       ├── database-schema.png
│       └── user-flow.png
├── frontend/ ✅
├── backend/ (pending)
└── README.md
```

This demonstrates the complete Spec-Driven Development workflow with structured documentation, clear phase transitions, detailed task management, and persistent documentation that supports team collaboration and project continuity.
