# Agent Skill: SOLID Principle Reference - ISP

## Principle Overview
**Name:** Interface Segregation Principle (ISP)
**Core Concept:** "A class should not be forced to implement interfaces it does not use."

---

## Identifying Violations
A violation occurs when an interface is "fat," meaning it includes methods that not all implementing classes need. This forces classes to implement methods they don't use, often with empty or placeholder implementations.

### Anti-Pattern
In this example, a single `Shape` interface includes both `area` and `perimeter`. If a shape (e.g., a line) only has a length but no area, it would be forced to implement `area()` unnecessarily.

```
abstract class Shape {
  double area();
  double perimeter();
}

class Rectangle implements Shape {
  double width;
  double height;

  double area() {
    return width * height;
  }

  double perimeter() {
    return 2 * (width + height);
  }
}

class Circle implements Shape {
  double radius;

  double area() {
    return pi * pow(radius, 2);
  }

  double perimeter() {
    return 2 * pi * radius;
  }
}
```

### Refactored Solution
To adhere to ISP, the "fat" interface is split into smaller, more specific interfaces. Classes can then implement only the interfaces they need.

```
// 1. Granular Interfaces
abstract class Area {
  double area();
}

abstract class Perimeter {
  double perimeter();
}
```

```
// 2. A class that needs both area and perimeter
class Rectangle implements Area, Perimeter {
  double width;
  double height;

  double area() {
    return width * height;
  }

  double perimeter() {
    return 2 * (width + height);
  }
}
```

```
// 3. A class that might only need area
class Circle implements Area {
  double radius;

  double area() {
    return pi * pow(radius, 2);
  }
}
```