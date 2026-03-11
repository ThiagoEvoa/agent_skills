# Agent Skill: SOLID Principle Reference - SRP

## Principle Overview
**Name:** Single Responsibility Principle (SRP)
**Core Concept:** "A class should have one, and only one, reason to change."

---

## Identifying Violations
A violation occurs when a single class is tasked with multiple logic domains. Common "extra" responsibilities include:
* Database persistence.
* Notification/Email logic.
* Validation logic.

### Anti-Pattern (The "God" Class)
In this example, the `User` class is bloated because it handles its own data, its own storage, and its own notifications.

```
class User {
  int id;
  String name;

  void save() {
    // Problem: Persistence logic inside the data model
  }

  void sendEmail() {
    // Problem: Notification logic inside the data model
  }
}
```

### Refactored Solution
To adhere to SRP, the responsibilities are decoupled into specialized classes. This allows each part of the system to evolve independently.

```
// 1. The Domain Model: Only manages user data
class User {
  int id;
  String name;
}
```

```
// 2. The Persistence Layer: Handles database interactions
class UserRepository {
  void save(User user) {
    // save user to database
  }
}
```

```
// 3. The Infrastructure Service: Handles external communications
class EmailService {
  void sendEmail(User user) {
    // send email to user
  }
}
```