# Clean Architecture

> **📚 Part of the [Awesome AI Architect](../README.md) knowledge base** - 10x your AI Architect journey with plain-language, hands-on guides

![clean architecture](/img/clean-architecture.png)

## TL;DR

**Clean Architecture is a design pattern that organizes code into concentric circles with dependencies flowing inward.** The core principle: business logic stays independent of external concerns like databases, UI, or frameworks. Think of it as an onion - the center contains your most important business rules, and outer layers handle implementation details. This makes your code testable, maintainable, and adaptable to change.

**Key takeaway:** Your business logic should never know about databases, web frameworks, or external services. Instead, define interfaces in the core and implement them in outer layers.

## Overview

Clean Architecture, also known as Hexagonal Architecture or Onion Architecture, is a software design pattern that emphasizes separation of concerns and dependency inversion. It was popularized by Robert C. Martin (Uncle Bob) and builds upon decades of architectural thinking from Alistair Cockburn, Jeffrey Palermo, and others.

![Clean Architecture](/img/diagrams/clean-architecture.png)

## The Problem with Traditional N-Tier Architecture

Most applications use the classic N-Tier architecture (UI Layer → Business Logic Layer → Data Layer), but this approach has significant limitations:

### N-Tier Architecture Issues

- **Presentation**
- **Application**
- **Domain**
- **Infrastructure**

**Problems with N-Tier:**
- **Rigid Dependencies**: Each layer can only communicate with the layer below it
- **Excessive Mapping**: Different models for each layer result in too much mapping code
- **Tight Coupling**: Business logic becomes dependent on infrastructure concerns
- **Testing Difficulties**: Hard to test business logic in isolation
- **Change Resistance**: Modifying one layer often requires changes across multiple layers

## Clean Architecture Solution

Clean Architecture solves these problems by inverting the dependency flow and organizing code into concentric circles:

### The Dependency Rule

**All dependencies must point inward.** Nothing in an inner circle can know about anything in an outer circle. This is the fundamental rule that makes Clean Architecture work.

### The Four Layers

#### 1. **Entities (Domain Layer)**
- **Purpose**: Enterprise-wide business rules and core business objects
- **Contains**: Business entities, value objects, domain services, domain events
- **Dependencies**: None (innermost layer)
- **Example**: User, Order, Product entities with business logic

#### 2. **Use Cases (Application Layer)**
- **Purpose**: Application-specific business rules and use case orchestration
- **Contains**: Application services, use case implementations, application interfaces
- **Dependencies**: Only on Entities layer
- **Example**: CreateUserUseCase, ProcessOrderUseCase

#### 3. **Interface Adapters (Infrastructure Layer)**
- **Purpose**: Convert data between use cases and external systems
- **Contains**: Controllers, presenters, repositories, external service adapters
- **Dependencies**: Use Cases and Entities layers
- **Example**: UserController, UserRepository, EmailService

#### 4. **Frameworks & Drivers (Presentation Layer)**
- **Purpose**: External frameworks and tools
- **Contains**: Web frameworks, databases, external APIs, UI frameworks
- **Dependencies**: All inner layers
- **Example**: ASP.NET Core, Entity Framework, React, Angular

## Key Principles

### 1. **Dependency Inversion Principle**
- High-level modules should not depend on low-level modules
- Both should depend on abstractions (interfaces)
- Abstractions should not depend on details

### 2. **Separation of Concerns**
- Each layer has a single, well-defined responsibility
- Business logic is isolated from infrastructure concerns
- UI logic is separate from business logic

### 3. **Testability**
- Business logic can be tested without external dependencies
- Use dependency injection to provide test doubles
- Unit tests focus on business rules, not implementation details

### 4. **Independence**
- **Framework Independence**: Can swap frameworks without changing business logic
- **Database Independence**: Can change data storage without affecting core
- **UI Independence**: Can change user interface without touching business logic
- **External Agency Independence**: Business rules don't know about external systems

## When to Use Clean Architecture

### ✅ **Use Clean Architecture When:**
- Building complex business applications
- Multiple teams working on the same codebase
- High testability requirements
- Need to swap external dependencies
- Long-term maintainability is critical
- Working with domain-driven design (DDD)

### ❌ **Avoid Clean Architecture When:**
- Simple CRUD applications
- Prototypes or proof-of-concepts
- Small teams with simple requirements
- Performance is the primary concern
- Tight deadlines with minimal complexity

## Common Pitfalls

### ❌ **Anemic Domain Models**
- **Problem**: Entities are just data containers without behavior
- **Solution**: Put business logic in entities, not services
- **Example**: `user.CalculateAge()` instead of `userService.CalculateAge(user)`

### ❌ **Leaking Infrastructure Concerns**
- **Problem**: Business logic depends on database or framework details
- **Solution**: Use interfaces and dependency injection
- **Example**: Don't use `DbContext` directly in use cases

### ❌ **Over-Engineering**
- **Problem**: Creating unnecessary abstractions for simple operations
- **Solution**: Start simple, add complexity when needed
- **Example**: Don't create interfaces for every single service

### ❌ **Circular Dependencies**
- **Problem**: Layers depending on each other
- **Solution**: Follow the dependency rule strictly
- **Example**: Use events or interfaces to break cycles

### ❌ **Fat Controllers**
- **Problem**: Business logic in controllers
- **Solution**: Move logic to use cases
- **Example**: Controller should only handle HTTP concerns

### ❌ **Tight Coupling Between Layers**
- **Problem**: Layers know too much about each other
- **Solution**: Use DTOs and interfaces
- **Example**: Don't pass entities directly between layers

## Real-World Examples

### 1. **eShopOnWeb** (Microsoft)
- **Repository**: [ardalis/cleanarchitecture](https://github.com/ardalis/cleanarchitecture)
- **Description**: ASP.NET Core reference application using Clean Architecture
- **Features**: CQRS, DDD, Entity Framework, MediatR

### 2. **Buckpal** (Tom Hombergs)
- **Repository**: [thombergs/buckpal](https://github.com/thombergs/buckpal)
- **Description**: Java/Spring Boot implementation with Hexagonal Architecture
- **Features**: Domain-driven design, testing strategies, architectural boundaries

### 3. **Domain-Driven Hexagon** (Sairyss)
- **Repository**: [Sairyss/domain-driven-hexagon](https://github.com/Sairyss/domain-driven-hexagon)
- **Description**: TypeScript/Node.js implementation
- **Features**: Modern JavaScript patterns, testing, documentation

## Resources

- [Clean Architecture by Robert C. Martin](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
- [Hexagonal Architecture by Alistair Cockburn](https://alistair.cockburn.us/hexagonal-architecture/)
- [Onion Architecture by Jeffrey Palermo](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/)
- [Microsoft's Clean Architecture Guide](https://docs.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures)
- [Clean Architecture Solution Template](https://github.com/ardalis/cleanarchitecture)
- [Buckpal Example](https://github.com/thombergs/buckpal)

## Related Topics

- [Architecture Decision Records](architecture-decision-records.md) - Documenting architectural decisions
- [AI Architecture Patterns](../ai-architecture-topics/ai-architecture-patterns.md) - AI-specific architectural patterns
- [Serving & Scaling](../ai-architecture-topics/serving-and-scaling.md) - Scalability considerations
- [Safety & Security](../ai-architecture-topics/safety-and-security.md) - Security in clean architecture
- [Career Guide](../career.md) - Solution architect career development
- [Interview Prep](../interview-prep.md) - System design interview preparation

---

*Clean Architecture is not about following rules blindly—it's about creating maintainable, testable, and adaptable software that can evolve with your business needs. Start simple, add complexity when justified, and always prioritize business value over architectural purity.*
