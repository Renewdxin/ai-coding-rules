# Code Quality Rules

## Static Analysis Standards
- Use ESLint/TSLint for JavaScript/TypeScript projects
- Implement SonarQube for comprehensive code analysis
- Configure pre-commit hooks for automated quality checks
- Maintain code coverage above 80% for critical modules

## Code Metrics Standards
- **Cyclomatic Complexity**: Keep functions under 10 complexity points
- **Function Length**: Maximum 50 lines per function
- **Class Size**: Maximum 300 lines per class
- **Parameter Count**: Maximum 5 parameters per function
- **Nesting Depth**: Maximum 4 levels of nesting

## Refactoring Guidelines
- Apply Extract Method pattern for code duplication
- Use Strategy Pattern for complex conditional logic
- Implement Dependency Injection for better testability
- Follow Single Responsibility Principle (SRP)
- Apply Open/Closed Principle for extensibility

## Technical Debt Management
- Document technical debt in code comments with TODO tags
- Prioritize debt by impact and effort matrix
- Allocate 20% of sprint capacity for debt reduction
- Track debt metrics in project dashboard
- Regular architecture review sessions

## Code Smell Detection
- **Long Method**: Functions exceeding 30 lines
- **Large Class**: Classes with too many responsibilities
- **Duplicate Code**: Identical logic in multiple places
- **Dead Code**: Unused variables, functions, or imports
- **Magic Numbers**: Hardcoded values without explanation
- **God Object**: Classes that know too much or do too much

## Design Patterns Application
- **Creational**: Factory, Builder, Singleton (use sparingly)
- **Structural**: Adapter, Decorator, Facade
- **Behavioral**: Observer, Strategy, Command
- **Architectural**: MVC, MVP, MVVM, Clean Architecture

## Code Review Quality Gates
- All functions have single responsibility
- No hardcoded configuration values
- Proper error handling implementation
- Consistent naming conventions
- Adequate unit test coverage
- Performance considerations documented
