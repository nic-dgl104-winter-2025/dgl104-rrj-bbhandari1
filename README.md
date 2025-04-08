[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/MMj2nZMu)
# Rsearch and Reflection Journal
Research and Reflection Journal for DGL 104 course

## Introduction

My journey through DGL 104 has been a deep dive into software development principles, from user requirements to architectural patterns and programming paradigms. This journal begins with functional user requirements (Week 8), progresses through design patterns and MV star architectures (Weeks 9-10), and culminates in object-oriented and functional programming concepts (Weeks 11-12). Each entry reflects my efforts to connect theory to practice, supported by examples and external resources, with an arc that traces my growing confidence in applying these ideas.

---

## Week 8: Functional User Requirements

### Research Summary

Week 8 introduced functional user requirements and user stories as tools to bridge user experience (UX) and technical implementation in app development. A video by Ashley emphasized understanding both perspectives—how users interact with an app and how it’s structured programmatically. User stories, written in natural language (e.g., "As a user, I can…"), foster team communication but often lack technical details like performance criteria. Technical Design Documents (TDDs) complement them by outlining architecture and specifications, while functional requirements define features via inputs and outputs.

### Key Takeaways
- **Holistic Perspective**: Developers must balance UX with technical frameworks for reliable apps.
- **User Stories’ Limits**: They clarify intent but need TDDs or functional requirements for execution.
- **Dynamic Documentation**: Early-stage TDDs guide development but must evolve with the project.

### Reflection

This week shifted my view of app critique from purely aesthetic to technical. I used to focus on how an app *feels*, but now I see how frameworks and data structures underpin that experience.

### Example: User Registration Functional Requirement
**User Story**: "As a new user, I want to register an account so I can access personalized features."  
**Functional Requirement**:  
- **Input**: Name, email, password (min. 8 characters, 1 uppercase, 1 number, 1 special character).  
- **Output**: Confirmation email sent, user redirected to homepage, or error if email is in use.  
- **Acceptance Criteria**: Email validation, duplicate check, secure redirect.

---

## Week 9: Design Patterns

### Research Summary

Week 9 explored design patterns—reusable solutions to common coding problems in object-oriented programming (OOP). The "Gang of Four" popularized them in the 1990s, advocating two principles: "Program to an interface, not an implementation" and "Favor object composition over class inheritance." Interfaces decouple systems for flexibility, while composition avoids brittle inheritance chains. Patterns fall into creational (e.g., Singleton), structural (e.g., Adapter), and behavioral (e.g., Observer) categories, though misapplying them risks anti-patterns.

For instance, the Singleton pattern ensures one instance (e.g., a config manager), while Observer supports dynamic updates (e.g., YouTube notifications). A video highlighted how inheritance can overcomplicate code, pushing me to rethink rigid hierarchies.

### Key Takeaways
- **Pattern Benefits**: They enhance maintainability and reusability.
- **Interface Power**: Shared contracts simplify testing and swapping implementations.
- **Composition vs. Inheritance**: Composing behaviors is more flexible than deep inheritance trees.

### Reflection

Design patterns feel like a cheat code for coding smarter, not harder. The Singleton example clicked when I imagined a single database connection—why create multiples? But the Observer pattern really excited me; I can see it in action for UI updates. I struggled with inheritance’s downsides at first—why avoid something so intuitive?—but seeing how composition keeps code cleaner (e.g., mixing `move` and `honk` behaviors) convinced me. I’m still wary of overusing patterns, though—could they bloat my code if I’m not careful?

### Example: Strategy Pattern (Python)
```python
class PaymentStrategy:
    def pay(self, amount):
        pass

class CreditCard(PaymentStrategy):
    def pay(self, amount):
        print(f"Paid {amount} via credit card")

class PayPal(PaymentStrategy):
    def pay(self, amount):
        print(f"Paid {amount} via PayPal")

class Checkout:
    def __init__(self, strategy: PaymentStrategy):
        self.strategy = strategy
    def process(self, amount):
        self.strategy.pay(amount)

checkout = Checkout(CreditCard())
checkout.process(100)  # Output: Paid 100 via credit card
```

---

## Week 10: MV Patterns

### Research Summary

Week 10 covered MV star architectural patterns (e.g., MVC, MVVM) for user interfaces, separating concerns between Model (data/logic), View (UI), and a mediator (e.g., Controller). MVC, born in Smalltalk in the 1970s, powers web frameworks like Django, while MVVM dominates modern mobile apps (e.g., SwiftUI). A video traced MVC’s Apple roots and MVVM’s rise with reactive frameworks, emphasizing testability and modularity.

For a to-do list app, MVC splits tasks (Model), UI (View), and user actions (Controller). MVVM, conversely, uses a ViewModel to bind data to the UI dynamically.

### Key Takeaways
- **Separation of Concerns**: Keeps code organized and testable.
- **MVC Legacy**: Still vital in web development despite mobile shifts.
- **MVVM Modernity**: Reactive binding suits dynamic UIs.

### Reflection

MV patterns clarified why my past projects felt chaotic—mixing logic and UI is a mess! MVC makes sense for web apps I’ve tinkered with, but MVVM’s reactivity blew my mind for mobile. Implementing a weather app with MVVM could auto-update the UI when data changes—no manual refreshes! I’m still wrapping my head around when to pick one over the other, but I see how they streamline collaboration across teams.

### Example: MVC To-Do List (Python)
```python
class Task:
    def __init__(self, title):
        self.title = title
        self.completed = False

class TaskView:
    def display(self, task):
        status = "✓" if task.completed else " "
        print(f"[{status}] {task.title}")

class TaskController:
    def __init__(self, task, view):
        self.task = task
        self.view = view
    def complete(self):
        self.task.completed = True
        self.view.display(self.task)

task = Task("Submit assignment")
view = TaskView()
controller = TaskController(task, view)
controller.complete()  # Output: [✓] Submit assignment
```

---

## Week 11: Object-Oriented Programming (OOP)

### Research Summary

Week 11 split into two parts: OOP basics and SOLID principles. OOP revolves around objects (data + behavior) via classes, with encapsulation (data protection), inheritance (code reuse), and polymorphism (flexible behavior). SOLID—Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, and Dependency Inversion—refines OOP for maintainability. A video stressed SRP (one job per class), OCP (extend, don’t modify), and ISP (tailored interfaces), alongside DRY (no duplication).

For example, a `Car` class encapsulates speed, while SOLID splits `UserManager` and `FileManager` for clarity.

### Key Takeaways
- **OOP Core**: Objects model real-world entities intuitively.
- **SOLID Power**: Principles prevent spaghetti code.
- **DRY Simplicity**: One source of truth cuts bugs.

### Reflection

OOP clicked as a way to mimic reality—cars have attributes and actions! But SOLID was a revelation; I’ve written messy classes with too many roles before. SRP feels like decluttering my code, and OCP’s "extend, don’t tweak" mindset will save me future headaches. I tested this with a small project and saw cleaner, testable code emerge. Still, I wonder if SOLID overcomplicates simple apps—finding that balance is my next challenge.

### Example: Open/Closed Principle (Python)
```python
class Shape:
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    def area(self):
        return 3.14 * self.radius ** 2

class Square(Shape):
    def __init__(self, side):
        self.side = side
    def area(self):
        return self.side ** 2

def total_area(shapes):
    return sum(shape.area() for shape in shapes)

shapes = [Circle(2), Square(3)]
print(total_area(shapes))  # Output: 21.56 (12.56 + 9)
```

---

## Week 12: Functional Paradigm

### Research Summary

Week 12 contrasted functional programming (declarative) with imperative programming (OOP’s domain). Functional programming, integrated into languages like Kotlin, uses immutable data, higher-order functions (e.g., `filter`), and recursion to reduce side effects. A video compared extracting even numbers: imperative loops vs. functional `filter`, showing the latter’s clarity and predictability.

### Key Takeaways
- **Declarative Clarity**: Focus on *what*, not *how*.
- **Side Effect Reduction**: Predictable code is easier to debug.
- **Tool Power**: `filter`, `map`, etc., streamline data tasks.

### Reflection

Functional programming feels like a breath of fresh air after OOP’s complexity. The `filter` example was a lightbulb moment—why loop manually when I can declare intent? I tried it in a small script and loved the readability, though I missed OOP’s structure for bigger systems. Blending both paradigms in multi-paradigmatic languages like Python excites me—I can pick the best tool for the job.


---
## Conclusion

This journal traces my evolution from Week 8’s user-focused requirements to Week 12’s paradigm explorations. I started unsure how UX and code connect, but now I see user stories feeding into functional specs and patterns like MVC or SOLID shaping robust systems. Reflecting on each topic—whether wrestling with inheritance or embracing `filter`—has deepened my understanding and confidence. Moving forward, I aim to blend OOP’s structure with functional clarity in my projects, guided by principles like SOLID.

---

## Bibliography

- Ashley. (2025). *Week 8 Video: Functional User Requirements*. DGL 104 Course Materials.
- Ashley. (2025). *Week 9 Video: Design Patterns*. DGL 104 Course Materials.
- Ashley. (2025). *Week 10 Video: MV Patterns*. DGL 104 Course Materials.
- Ashley. (2025). *Week 11 Video: OOP Part 1 & 2*. DGL 104 Course Materials.
- Ashley. (2025). *Week 12 Video: Functional Paradigm*. DGL 104 Course Materials.
- Gamma, E., et al. (1994). *Design Patterns: Elements of Reusable Object-Oriented Software*. Addison-Wesley.
