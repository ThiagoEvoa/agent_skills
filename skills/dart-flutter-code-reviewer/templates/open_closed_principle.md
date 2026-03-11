# Agent Skill: SOLID Principle Reference - OCP

## Principle Overview
**Name:** Open/Closed Principle (OCP)
**Core Concept:** "Software entities (classes, modules, functions) should be open for extension, but closed for modification."

---

## Identifying Violations
A violation occurs when adding a new feature or type requires you to open and modify an existing, tested class. This often leads to a chain reaction of bugs in existing logic.

### Anti-Pattern (The Rigid Class)
In this example, if we wanted to add a `Circle`, we would have to modify the `AreaCalculator` or the `Rectangle` class itself to handle different logic.

[Image of Open/Closed Principle violation diagram]

```
class Rectangle {
  double width;
  double height;

  // Problem: This logic is specific only to Rectangles.
  // Adding a Circle would require changing this class or 
  // creating a separate, non-standardized method.
  double area() {
    return width * height;
  }
}
```

### Refactored Solution (The OCP Way)
By using an interface or abstract class, we make the system open for extension (we can add new shapes) but closed for modification (we don't have to touch the existing shape classes to add a new one).

```
// 1. The Abstraction: Defines the contract
abstract class Shape {
  abstract double area();
}
```

```
// 2. Extension: Rectangle implements the contract
class Rectangle extends Shape {
  double width;
  double height;

  @Override
  double area() {
    return width * height;
  }
}
```

```
// 3. Extension: Circle implements the contract without modifying Rectangle
class Circle extends Shape {
  double radius;
  final double pi = 3.14159;

  @Override
  double area() {
    return pi * Math.pow(radius, 2);
  }
}
```