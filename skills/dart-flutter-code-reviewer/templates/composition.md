# Agent Skill: Architectural Principle Reference - Composition over Inheritance

## Principle Overview
**Name:** Composition over Inheritance
**Core Concept:** "Favor composition over inheritance." This means that it's often better to build classes by combining simpler classes (composition) rather than inheriting from a complex class (inheritance).

---

## Comparison

### Inheritance
Inheritance lets one class inherit the properties and methods of another class. For example, if you have a `Car` class that inherits from a `Vehicle` class, you're saying that a car **is a** type of vehicle. The `Car` class gets all the behavior of the `Vehicle` class.

**Drawbacks:**
*   **Flexibility:** Inheritance locks your class into a rigid hierarchy, making it harder to make changes.
*   **Complexity:** Inheritance can lead to complex class hierarchies, making your code harder to understand and maintain.
*   **Reusability:** With inheritance, you are forced to reuse entire class hierarchies, which may include unnecessary or unwanted behavior.

### Composition
Composition involves creating classes by combining objects from other classes. Instead of inheriting from a parent class, your class **has a** relationship with other objects to add functionality. For example, a `Car` class might have an `Engine` object and a `Wheels` object.

**Benefits:**
*   **Flexibility:** Composition lets you easily swap out or modify parts of your class without affecting its entire structure.
*   **Reduced Complexity:** Composition keeps things simple by focusing on small, independent classes that work together.
*   **Better Reusability:** With composition, you can reuse individual components across different classes.

---

## Example: Robot Behaviors

### Inheritance (Less Flexible)

A common anti-pattern is to use inheritance to define different types of robots. This leads to a rigid class hierarchy. For example, a `FlyingRobot` can't easily gain the ability to swim without multiple inheritance, which isn't supported in Dart.

### Composition (More Flexible)

With composition, we can define behaviors and then create a `Robot` that can use any combination of those behaviors.

```dart
// 1. Define the behaviors (interfaces)
abstract class MoveBehaviour {
  void move();
}

abstract class AttackBehaviour {
  void attack();
}

// 2. Create concrete implementations of the behaviors
class FlyBehaviour implements MoveBehaviour {
  @override
  void move() {
    print('Flying high!');
  }
}

class SwimBehaviour implements MoveBehaviour {
  @override
  void move() {
    print('Swimming deep!');
  }
}

class LaserAttack implements AttackBehaviour {
  @override
  void attack() {
    print('Firing lasers! Pew pew!');
  }
}

// 3. Compose the Robot class 🧱
class Robot {
  // The Robot "has-a" move behaviour and "has-a" attack behaviour
  MoveBehaviour moveBehaviour;
  AttackBehaviour attackBehaviour;

  // The constructor requires the components the robot is built from
  Robot({required this.moveBehaviour, required this.attackBehaviour});

  // It delegates the work to its components
  void performMove() {
    moveBehaviour.move();
  }

  void performAttack() {
    attackBehaviour.attack();
  }

  // We can even swap behaviors at runtime for ultimate flexibility!
  void changeMoveBehaviour(MoveBehaviour newBehaviour) {
    print('--- Swapping move behaviour ---');
    moveBehaviour = newBehaviour;
  }
}

void main() {
  // Now we can create any robot we want by combining components
  final flyingLaserRobot = Robot(
    moveBehaviour: FlyBehaviour(),
    attackBehaviour: LaserAttack(),
  );

  print('Flying Laser Robot:');
  flyingLaserRobot.performMove(); // "Flying high!"
  flyingLaserRobot.performAttack(); // "Firing lasers! Pew pew!"

  print('\n---');

  final swimmingLaserRobot = Robot(
    moveBehaviour: SwimBehaviour(),
    attackBehaviour: LaserAttack(),
  );

  print('Swimming Laser Robot:');
  swimmingLaserRobot.performMove(); // "Swimming deep!"

  // Let's make our flying robot able to swim instead!
  print('Making the flying robot swim...');
  flyingLaserRobot.changeMoveBehaviour(SwimBehaviour());
  flyingLaserRobot.performMove(); // "Swimming deep!"
}
```