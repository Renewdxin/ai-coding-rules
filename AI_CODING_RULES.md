# AI-Assisted Coding Rules

## Cursor/Claude Specific Workflow

### Five-Step Process
1. **Define Task Scope**: Analyze task, clarify objectives, create clear plan
2. **Precisely Locate Modification Points**: Identify specific files and code lines
3. **Minimal and Isolated Changes**: Write only task-required code
4. **Strict Code Review**: Check correctness, scope compliance, side effects
5. **Clear Deliverable Summary**: Document changes and reasons

### Multi-Step Planning Strategy
- Generate comprehensive implementation plan before coding
- Break complex tasks into smaller, manageable phases
- Implement and test each phase before proceeding to next
- Review and validate each step for correctness

## AI-Optimized Code Organization

### File Structure Guidelines
- Keep files under 500 lines for better AI comprehension
- Use descriptive file and function names
- Maintain logical directory structure
- Group related functionality together

### Code Patterns for AI
- Use consistent naming conventions across project
- Implement clear separation of concerns
- Write self-documenting code with meaningful variable names
- Avoid complex nested structures when possible

### Documentation for AI Context
- Provide file overviews at the top of each file
- Use block comments for complex business logic
- Document architectural decisions and patterns used
- Maintain up-to-date README with project structure

## AI Interaction Best Practices

### Request Formatting
- Be specific about requirements and constraints
- Provide context about existing codebase
- Specify which files should or shouldn't be modified
- Include relevant error messages or logs

### Iterative Development
- Request small, focused changes rather than large refactors
- Validate each change before requesting next modification
- Provide feedback on generated code quality
- Ask for explanations of complex implementations

### Code Review with AI
- Request explanation of generated code logic
- Ask for potential edge cases and error scenarios
- Verify that changes align with project architecture
- Check for security implications of generated code

## Common Patterns and Libraries

### Reusable Code Snippets
- Maintain library of common validation patterns (email, phone, ID)
- Create templates for standard CRUD operations
- Build collection of error handling patterns
- Develop standard logging and monitoring utilities

### Design Pattern Implementation
- Use Factory pattern for object creation complexity
- Implement Strategy pattern for algorithm variations
- Apply Observer pattern for event-driven architectures
- Utilize Repository pattern for data access abstraction

## Quality Assurance for AI-Generated Code

### Automated Checks
- Run linting tools on all generated code
- Execute test suites after each modification
- Perform security scans on new implementations
- Check for performance regressions

### Manual Review Points
- Verify business logic correctness
- Check integration with existing systems
- Validate error handling completeness
- Ensure code follows project conventions

## Prompt Engineering Guidelines

### Effective Prompts
- Include relevant context and constraints
- Specify desired code style and patterns
- Mention testing requirements upfront
- Request documentation alongside code

### Context Management
- Provide relevant existing code snippets
- Include error messages and stack traces
- Share project structure and dependencies
- Mention performance or security requirements

## Troubleshooting AI-Generated Code

### Common Issues
- Over-engineered solutions for simple problems
- Missing error handling in edge cases
- Inconsistent naming conventions
- Unnecessary dependencies or imports

### Resolution Strategies
- Request simpler, more focused implementations
- Ask for specific error handling scenarios
- Specify naming conventions explicitly
- Review and minimize dependencies

## Continuous Improvement

### Learning from AI Interactions
- Document successful prompt patterns
- Keep track of common AI mistakes
- Build knowledge base of effective solutions
- Share learnings with team members

### Feedback Loop
- Provide specific feedback on code quality
- Request improvements for unclear implementations
- Ask for alternative approaches when needed
- Validate AI suggestions against best practices
