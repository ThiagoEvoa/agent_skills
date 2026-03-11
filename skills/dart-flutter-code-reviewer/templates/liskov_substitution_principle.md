# Agent Skill: SOLID Principle Reference - LSP

## Principle Overview
**Name:** Liskov Substitution Principle (LSP)
**Core Concept:** "Objects of a superclass should be able to be replaced with objects of a subclass without affecting the correctness of the program."

---

## Identifying Violations
A violation typically occurs when a subclass overrides a superclass method in a way that is incompatible with the superclass's behavior, breaking the "is-a" relationship.

### Anti-Pattern
In this example, `Square` extends `Rectangle`, but it changes the behavior of setters in a way that a function expecting a `Rectangle` would not anticipate.

```
class Rectangle {
  double width;
  double height;

  double area() {
    return width * height;
  }
}

class Square extends Rectangle {
  double side;

  @override
  double set width(double value) => side = value;

  @override
  double set height(double value) => side = value;
}
```

### Refactored Solution
To adhere to LSP, we should ensure that `Square` and `Rectangle` are not in a parent-child relationship if their behaviors are not substitutable. Instead, they can both implement a common interface.

```
// 1. The Abstraction: A contract that both shapes can fulfill.
abstract class Shape {
  double area();
}
```

```
// 2. Concrete Implementation
class Rectangle implements Shape {
  double width;
  double height;

  double area() {
    return width * height;
  }
}
```

```
// 3. Another Concrete Implementation
class Square implements Shape {
  double side;

  double area() {
    return pow(side, 2);
  }
}
```