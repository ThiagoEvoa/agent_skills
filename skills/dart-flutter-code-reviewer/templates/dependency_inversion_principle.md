# Agent Skill: SOLID Principle Reference - DIP

## Principle Overview
**Name:** Dependency Inversion Principle (DIP)
**Core Concept:** "High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions."

---

## Identifying Violations
A violation occurs when a high-level component (e.g., a business logic service) depends directly on a low-level component (e.g., a specific database implementation).

### Anti-Pattern
In this example, `UserService` is tightly coupled to the concrete `UserRepository` class. This makes it difficult to change the database implementation later.

```
class UserRepository {
  void save(User user) {
    // save user to a specific database
  }
}

class UserService {
  UserRepository userRepository;

  UserService(this.userRepository);

  void saveUser(User user) {
    userRepository.save(user);
  }
}
```

### Refactored Solution
To adhere to DIP, both the high-level and low-level modules depend on an abstraction (`UserRepository` interface). This inverts the dependency, making the system more flexible.

```
// 1. The Abstraction: Defines the contract for persistence
abstract class UserRepository {
  void save(User user);
}
```

```
// 2. The Low-Level Implementation: A concrete implementation of the repository
class FirebaseUserRepository implements UserRepository {
  void save(User user) {
    // save user to Firebase
  }
}
```

```
// 3. The High-Level Module: Depends on the abstraction, not the concrete class
class UserService {
  UserRepository userRepository;

  UserService(this.userRepository);

  void saveUser(User user) {
    userRepository.save(user);
  }
}
```