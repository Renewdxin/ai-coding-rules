# Architecture Rules

## SOLID Principles Implementation
- **Single Responsibility**: Each class/module has one reason to change
- **Open/Closed**: Open for extension, closed for modification
- **Liskov Substitution**: Derived classes must be substitutable for base classes
- **Interface Segregation**: Clients shouldn't depend on unused interfaces
- **Dependency Inversion**: Depend on abstractions, not concretions

## Design Patterns Standards
- **Repository Pattern**: For data access abstraction
- **Factory Pattern**: For object creation complexity
- **Observer Pattern**: For event-driven architectures
- **Strategy Pattern**: For algorithm variations
- **Decorator Pattern**: For feature enhancement without modification

## Dependency Injection Guidelines
- Use constructor injection as primary method
- Avoid service locator anti-pattern
- Configure dependencies at application root
- Use interfaces for loose coupling
- Implement proper lifetime management (Singleton, Transient, Scoped)

## API Design Principles
- **RESTful Design**: Use HTTP verbs correctly
- **Resource-Based URLs**: Nouns, not verbs in endpoints
- **Stateless Operations**: No server-side session state
- **HATEOAS**: Include navigation links in responses
- **Content Negotiation**: Support multiple response formats

## Microservices Architecture
- **Service Boundaries**: Align with business capabilities
- **Data Ownership**: Each service owns its data
- **Communication**: Prefer async messaging over sync calls
- **Fault Tolerance**: Implement circuit breaker pattern
- **Service Discovery**: Use registry for dynamic service location

## Monolithic Architecture
- **Modular Design**: Clear module boundaries
- **Layered Architecture**: Presentation, Business, Data layers
- **Shared Kernel**: Common utilities and models
- **Database Per Module**: Logical separation even in monolith

## API Versioning Strategy
- **URL Versioning**: /api/v1/resource
- **Header Versioning**: Accept: application/vnd.api+json;version=1
- **Backward Compatibility**: Support N-1 versions
- **Deprecation Policy**: 6-month notice for breaking changes
- **Documentation**: Version-specific API documentation

## Event-Driven Architecture
- **Event Sourcing**: Store events, not current state
- **CQRS**: Separate read and write models
- **Event Bus**: Centralized event distribution
- **Saga Pattern**: Manage distributed transactions
- **Event Schema Evolution**: Handle schema changes gracefully
