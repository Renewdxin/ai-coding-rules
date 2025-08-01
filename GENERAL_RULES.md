# General Development Rules

## Core Objective
This Cursor rule applies to all programming tasks, requiring engineers to approach tasks from a senior engineer's perspective, strictly following processes to ensure code changes are precise, efficient, and do not introduce problems or unnecessary complexity.

## Five Key Steps

### 1. Define Task Scope
- Analyze the task before writing code, clarify objectives
- Create a clear plan listing functions, modules, or components to modify with reasons
- Only start coding after the plan is clear and well-considered

### 2. Precisely Locate Code Modification Points
- Identify specific files and code lines that need modification
- Avoid changes to unrelated files; if multiple files are involved, clearly explain the reason for each file's changes
- Unless explicitly required by the task, do not create new abstractions or refactor code

### 3. Minimal and Isolated Code Changes
- Write only code directly required by the task
- Avoid adding unnecessary logs, comments, tests, TODOs, or error handling
- No "while we're at it" modifications; ensure new code doesn't interfere with existing functionality

### 4. Strict Code Review
- Check code correctness, task scope compliance, and potential side effects
- Ensure code style consistency with existing codebase, prevent breaking existing functionality
- Evaluate if changes will impact downstream systems

### 5. Clear Deliverable Summary
- Summarize specific changes and reasons
- List all modified files and their specific changes
- Document any assumptions or potential risks for review

## Core Principles
- **No Improvisation**: Execute strictly according to task requirements, no arbitrary innovation
- **No Over-Engineering**: Avoid complexity, do only necessary work
- **No Rule Deviation**: Always follow this process to ensure code safety and reliability

## Fundamental Programming Principles

### Basic Principles
- **DRY (Don't Repeat Yourself)**: Avoid code duplication, use functions, modules, or libraries for reusable logic
- **KISS (Keep It Simple, Stupid)**: Prioritize simple design, readability over clever code
- **YAGNI (You Ain't Gonna Need It)**: Build only necessary features, don't add speculative functionality
- **SOC (Separation of Concerns)**: Break complex programs into small units, each focused on single task
- **SRP (Single Responsibility Principle)**: Each class or method should have only one responsibility

### Design and Architecture
- **SOLID Principles**: Follow all five SOLID principles for maintainable and extensible code
- **Composition over Inheritance**: Prefer composition to build behavior
- **Reduce Mutable State**: Prioritize immutable objects to reduce interaction complexity
- **Abstraction**: Extract core logic to make code more generic and reusable
- **Unix Philosophy**: Modularity (simple parts with clean interfaces), clarity (clear over clever), simplicity (add complexity only when necessary)

## Naming and Readability Standards

### Meaningful Naming
- Use descriptive names that explain purpose, not data type (use `balance` not `iNumber`)
- Avoid magic numbers/strings, use constants or enums (`OrderStatus.Completed` not `3`)
- Avoid double negatives, use positive conditions (`user.IsActive` not `!user.IsNotActive`)

### Code Structure
- Reduce nesting with early returns to simplify code paths
- Format code with proper indentation, spacing, and line breaks
- Keep files under 500 lines for better maintainability
- Use descriptive naming and comments for AI compatibility

## Documentation and Comments

### Comment Guidelines
- Comments should explain "why" not "what"
- Add comments only for complex logic, avoid redundancy
- Use file overviews and block comments for complex sections
- Document code for future self and others

### Documentation Standards
- Maintain synchronized documentation with code
- Use JSDoc or similar for function documentation
- Document architectural decisions and complex business logic

## Testing and Robustness

### Testing Strategy
- **TDD (Test Driven Development)**: Write failing test first, then code to pass, then refactor
- Validate input at public interfaces, don't trust external data
- Write robust code that handles unexpected input without crashing
- Focus on critical business logic testing

### Security Priority
- Security > Usability > Maintainability > Simplicity > Performance
- Implement proper input validation and sanitization
- Use secure coding practices consistently

## AI-Assisted Development Rules

### Multi-Step Planning
- Generate comprehensive plan before implementation
- Implement in phases with testing at each step
- Review and validate each phase before proceeding

### Code Organization
- Maintain clean file structure with logical organization
- Use consistent patterns that AI can understand and follow
- Document complex logic for AI context understanding

## Additional Best Practices

### State Management
- Reduce global dependencies, prefer local state and parameter passing
- Minimize shared mutable state across components
- Use appropriate state management patterns for complexity level

### Continuous Improvement
- Continuous refactoring to reduce technical debt
- Maintain extensibility without over-engineering
- Apply design patterns appropriately, avoid overuse or misuse
- Follow principle of least surprise in interface design

## Language Standards
- Code comments: English only
- User communication: Chinese only
- Documentation: Chinese for project docs, English for code comments

## Code Quality Standards
- No emojis or cute expressions
- Keep comments concise and brief
- Clean code structure with proper naming conventions
- Follow established coding conventions and style guides

## Content Control
- Never enrich content beyond user requirements
- Execute strictly according to specifications
- Always confirm changes with user before implementation

## Code Optimization Rules
- Never change existing functionality during optimization
- Focus on performance and structure improvements only
- Maintain API compatibility and backward compatibility
