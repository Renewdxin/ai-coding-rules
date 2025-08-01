# Task Execution Rules

## When to Use These Rules

### ✅ Apply for:
- **Multi-step development tasks** (3+ distinct phases)
- **Tasks requiring user confirmation** at multiple points
- **Development work that may be interrupted** or need continuation
- **Complex refactoring** or architecture changes
- **Tasks with dependencies** between components

### 🔄 Works alongside:
- **GENERAL_RULES.md**: Enhances the five key steps with detailed task management
- **SPEC_DRIVEN_RULES.md**: Provides execution framework for spec-driven projects
- **AI_CODING_RULES.md**: Implements structured AI interaction patterns

For complex development tasks, execute according to the following specifications:

## Execution Process

### 0. Task Status Check Phase (Priority Execution)
- **Check for retry tasks**: Review conversation history for incomplete task execution records
- **Identify execution breakpoint**: If retrying, determine which step was last executed
- **Status recovery**: Display current task completion status, clarify where to continue
- **User confirmation**: Confirm whether to continue from breakpoint or restart

### 1. Task Analysis Phase
- Analyze task complexity and requirements
- If solution design is needed, conduct solution comparison first
- Provide multiple optional solutions with pros and cons
- Wait for user confirmation of final solution

### 2. Task Planning Phase
- Based on confirmed solution, display complete task breakdown and execution plan
- Use markdown format task lists
- Clearly mark overall objectives and subtasks
- **Wait for user confirmation of task steps, ask if adjustments are needed**

### 3. During Execution
- Update progress status in real-time
- Use [x] for completed, [ ] for pending, 🔄 for currently executing
- Update status after completing each step

### 4. When Problems Occur
- Clearly indicate current execution position
- List completed work
- Explain specific failure point

### 5. Breakpoint Recovery Execution
- Based on status check results from step 0
- Skip completed steps
- Continue execution from specific breakpoint position
- Update execution status of remaining tasks

## Trigger Conditions

Automatically enable this process for:
- Tasks requiring creation of multiple files
- Tasks requiring modification of multiple components
- Development tasks with clear step sequences
- Tasks that may require multiple rounds of interaction
- Tasks requiring solution design and technology selection
- Tasks involving architecture design or refactoring

## Example Formats

### Solution Design Phase Example:
```markdown
## 🎯 Solution Design

### Requirements Analysis: [requirement description]

### Solution Comparison:

#### Solution 1: [solution name]
- Pros: ...
- Cons: ...
- Use cases: ...

#### Solution 2: [solution name]
- Pros: ...
- Cons: ...
- Use cases: ...

### Recommended Solution: [recommended solution and reasoning]

**Please confirm your chosen solution, then I will create a detailed execution plan.**
```

### Task Planning Phase Example:
```markdown
## 📋 Task Execution Plan

### Overall Objective: [task description]
### Selected Solution: [confirmed solution]

### Task Breakdown:
- [ ] 1. First major step
  - [ ] 1.1 Subtask one
  - [ ] 1.2 Subtask two
- [ ] 2. Second major step
  - [ ] 2.1 Subtask one

**Please confirm if the above task steps are appropriate. Any adjustments needed? I will begin execution after confirmation.**
```

### Status Check Phase Example:
```markdown
## 🔍 Task Status Check

### Detected Possible Retry Scenario
Based on conversation history, found previous task execution: [task description]

### Previous Execution Status:
- [x] 1. First major step ✅
- [x] 1.1 Subtask one ✅
- [ ] 1.2 Subtask two ❌ (previous failure point)
- [ ] 2. Second major step ⏸️ (not started)

**Continue from step 1.2, or restart the entire task?**
```

### Execution Phase Example:
```markdown
## 🔄 Current Execution Status
- [x] 1.1 Subtask one ✅
- [ ] 1.2 Subtask two 🔄 (currently executing)
```

## Important Notes

- **Priority status check**: Must check for retry scenarios before starting any task
- Keep task lists concise and clear
- Update progress status promptly
- Don't restart from beginning on failure, continue from breakpoint
- Prioritize parallel operations for efficiency
- **Solution design phase must wait for user solution confirmation**
- **Task planning phase must wait for user step confirmation**
- Complex tasks should prioritize multi-solution comparison
- Ensure user understands purpose and impact of each step
- **Retry identification keywords**: Pay attention to keywords like "continue", "retry", "proceed" in user messages

## Integration with Other Rules

### Relationship with GENERAL_RULES.md
- Follows the five key steps framework
- Enhances step 1 (Define Task Scope) with detailed planning
- Strengthens step 5 (Clear Deliverable Summary) with status tracking

### Relationship with AI_CODING_RULES.md
- Implements multi-step planning strategy
- Provides structured approach for AI-assisted development
- Enhances prompt engineering with clear status communication

### Relationship with WORKFLOW.md
- Extends daily development process with detailed task management
- Provides framework for complex task execution
- Integrates with code review and deployment preparation phases

## Usage Guidelines

### When to Apply
- Any task with more than 3 distinct steps
- Tasks requiring user input or confirmation at multiple points
- Development work that may be interrupted or need continuation
- Complex refactoring or architecture changes

### Best Practices
- Always start with status check for conversation continuity
- Break down complex tasks into manageable subtasks
- Provide clear progress indicators throughout execution
- Maintain detailed status tracking for easy recovery
- Use consistent formatting for better readability
