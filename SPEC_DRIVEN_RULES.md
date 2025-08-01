# Spec-Driven Development Rules

## Overview

Spec-Driven Development is a structured approach inspired by Specification by Example (SBE) methodology. This process guides users and AI through collaborative development using a waterfall-like model with AI asynchronous execution and user control, reducing rework and improving efficiency.

## When to Use This Framework

### ✅ Ideal for:
- **Large projects** (2+ weeks development time)
- **Team collaboration** requiring formal documentation
- **Complex systems** with multiple integrations
- **Client projects** needing detailed specifications
- **MVP development** with planned iterations
- **Projects requiring formal approval processes**

### ⚠️ Consider alternatives for:
- **Simple scripts** or single-file solutions
- **Rapid prototyping** without documentation needs
- **Emergency hotfixes** requiring immediate action
- **Personal projects** with flexible requirements

### 🔄 Relationship with Other Rules:
- **Extends GENERAL_RULES.md**: Builds upon the five key steps with formal documentation
- **Complements TASK_EXECUTION_RULES.md**: Uses structured documentation for complex task management
- **Integrates with AI_CODING_RULES.md**: Provides framework for multi-step AI planning

## Core Process Flow

### Phase 1: Requirements Collection
**Trigger**: User provides high-level prompt (e.g., "Develop an article comment system using Vue + TypeScript")

**AI Actions**:
1. Generate detailed requirements document (`requirements.md`)
2. Include user stories, feature points, and clarification questions
3. Present for user review and modification

**Output Structure**:
```markdown
# Requirements Document

## Project Overview
[High-level description]

## User Stories
- As a [user type], I want [functionality] so that [benefit]

## Functional Requirements
- [Detailed feature list]

## Non-Functional Requirements
- Performance, security, scalability requirements

## Clarification Questions
- [Questions for user to refine requirements]

## Acceptance Criteria
- [Testable conditions for completion]
```

### Phase 2: Design Documentation
**Trigger**: Requirements approved by user

**AI Actions**:
1. Analyze requirements and generate design specification (`design.md`)
2. Cover architecture, technical solutions, and potential risks
3. Support visualization output (logic diagrams, Markdown format)

**Output Structure**:
```markdown
# Design Document

## Architecture Overview
- System architecture diagram
- Component relationships
- Data flow

## Technical Stack
- Frontend: [Technology choices with rationale]
- Backend: [Technology choices with rationale]
- Database: [Database design]

## API Design
- Endpoint specifications
- Request/response formats
- Authentication strategy

## Risk Analysis
- Technical risks and mitigation strategies
- Performance considerations
- Security implications

## Implementation Strategy
- Development phases
- Integration points
- Testing approach
```

### Phase 3: Task Breakdown
**Trigger**: Design document approved by user

**AI Actions**:
1. Generate comprehensive task list (`tasks.md`)
2. Each task includes "Start Task" indicator
3. Support execution order selection, queue management, and modification

**Output Structure**:
```markdown
# Task List

## Development Phases

### Phase 1: Project Setup
- [ ] **Task 1.1**: Initialize project structure
  - **Priority**: High
  - **Estimated Time**: 30 minutes
  - **Dependencies**: None
  - **Deliverables**: Project scaffolding, configuration files
  
- [ ] **Task 1.2**: Setup development environment
  - **Priority**: High
  - **Estimated Time**: 45 minutes
  - **Dependencies**: Task 1.1
  - **Deliverables**: Development server, build tools

### Phase 2: Backend Development
- [ ] **Task 2.1**: Database schema design
  - **Priority**: High
  - **Estimated Time**: 1 hour
  - **Dependencies**: Task 1.1
  - **Deliverables**: Database models, migrations

### Phase 3: Frontend Development
[Continue with detailed task breakdown]

## Task Execution Queue
1. [User-selected task order]
2. [Parallel execution opportunities]
3. [Critical path identification]
```

### Phase 4: Execution and Iteration
**Process**:
1. AI executes tasks step by step
2. User can intervene at any time
3. Requirement changes cascade to all phases
4. Support preview, rollback, and automation
5. Documents and code stored in `.spec` folder

## File Organization Structure

```
project-root/
├── .spec/
│   ├── requirements.md
│   ├── design.md
│   ├── tasks.md
│   ├── execution-log.md
│   └── iterations/
│       ├── v1.0/
│       ├── v1.1/
│       └── current/
├── src/
│   ├── components/
│   ├── services/
│   ├── utils/
│   └── tests/
├── docs/
│   ├── api/
│   ├── user-guide/
│   └── technical/
└── README.md
```

## Implementation Guidelines

### Requirements Phase Best Practices
- **User Story Format**: Follow "As a [role], I want [feature] so that [benefit]" structure
- **Acceptance Criteria**: Use Given-When-Then format for testability
- **Clarification Questions**: Ask specific, actionable questions
- **Scope Definition**: Clearly define what's in and out of scope

### Design Phase Best Practices
- **Architecture Decisions**: Document rationale for technical choices
- **Risk Assessment**: Identify and plan mitigation for technical risks
- **API First**: Design APIs before implementation
- **Scalability Considerations**: Plan for future growth

### Task Breakdown Best Practices
- **Atomic Tasks**: Each task should be completable in 1-4 hours
- **Clear Dependencies**: Explicitly define task relationships
- **Deliverable Focus**: Each task should produce tangible output
- **Priority Classification**: High/Medium/Low priority assignment

### Execution Best Practices
- **Incremental Delivery**: Complete tasks produce working features
- **Continuous Integration**: Regular integration and testing
- **Documentation Updates**: Keep specs updated with implementation
- **User Feedback Loops**: Regular checkpoints for user validation

## Integration with Existing Rules

### Relationship with GENERAL_RULES.md
- Enhances the five key steps with structured documentation
- Provides framework for task scope definition
- Strengthens deliverable clarity through formal specifications

### Relationship with TASK_EXECUTION_RULES.md
- Extends task execution with formal documentation
- Provides structured approach to complex task management
- Enhances breakpoint recovery with persistent documentation

### Relationship with AI_CODING_RULES.md
- Implements multi-step planning with formal specifications
- Provides structured context for AI interactions
- Enhances prompt engineering with documented requirements

## Execution Commands and Workflow

### Starting a Spec Session
```markdown
## 🚀 Spec Session Initialization

**User Input**: [High-level requirement]

**AI Response Format**:
```
# Spec-Driven Development Session Started

## Session Overview
- **Project**: [Extracted project name]
- **Technology Stack**: [Identified from user input]
- **Complexity**: [Simple/Medium/Complex]

## Next Steps
1. Generate requirements document
2. Wait for user approval
3. Proceed to design phase

**Shall I proceed with requirements generation?**
```

### Phase Transitions
```markdown
## Phase Completion Checklist

### Requirements Phase ✅
- [x] Requirements document generated
- [x] User stories defined
- [x] Acceptance criteria established
- [x] User approval received

**Ready to proceed to Design Phase? (y/n)**

### Design Phase ✅
- [x] Architecture defined
- [x] Technical stack confirmed
- [x] API specifications created
- [x] Risk analysis completed

**Ready to proceed to Task Breakdown? (y/n)**
```

### Task Execution Format
```markdown
## 🔄 Task Execution Status

### Current Task: [Task ID and Name]
**Status**: In Progress 🔄
**Started**: [Timestamp]
**Estimated Completion**: [Time]

### Progress Indicators
- [x] Subtask 1 ✅
- [ ] Subtask 2 🔄 (Current)
- [ ] Subtask 3 ⏸️

### Deliverables Ready for Review
- [List of completed deliverables]

**Continue with next subtask? (y/n)**
```

## Quality Gates and Checkpoints

### Requirements Quality Gate
- [ ] All user stories follow proper format
- [ ] Acceptance criteria are testable
- [ ] Non-functional requirements defined
- [ ] Scope clearly bounded
- [ ] User approval documented

### Design Quality Gate
- [ ] Architecture supports all requirements
- [ ] Technical choices justified
- [ ] API contracts defined
- [ ] Security considerations addressed
- [ ] Performance requirements addressed

### Task Quality Gate
- [ ] All tasks are atomic and achievable
- [ ] Dependencies clearly mapped
- [ ] Deliverables well-defined
- [ ] Priorities assigned
- [ ] Effort estimates provided

## Advantages and Use Cases

### Advantages
- **Structured & Controllable**: Suitable for complex projects, avoiding "slot machine" uncertainty
- **High-Quality Output**: Professional documentation for team collaboration
- **Extensible**: Applicable beyond coding (articles, planning, etc.)
- **Recoverable**: Interruptions can be resumed from documented state

### Ideal Use Cases
- Complex feature development (web applications, games)
- Over-engineered backend projects requiring careful planning
- Team collaboration scenarios (PM + SWE integration)
- MVP iteration from small requirements to full features

### When NOT to Use
- Simple, single-file scripts
- Rapid prototyping without documentation needs
- Exploratory coding sessions
- Time-critical hotfixes

## Success Metrics

### Documentation Quality
- Requirements clarity score (1-10)
- Design completeness percentage
- Task granularity appropriateness

### Execution Efficiency
- Task completion rate
- Rework percentage
- User intervention frequency

### User Satisfaction
- Requirement accuracy after implementation
- Design adherence percentage
- Overall project success rate
