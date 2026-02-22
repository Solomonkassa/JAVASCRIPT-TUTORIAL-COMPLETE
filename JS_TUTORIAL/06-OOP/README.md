# Object-Oriented Programming: Building with Objects

Master OOP concepts and patterns for scalable code.

## Topics Covered

1. **[Objects Review](./01-objects-review.md)** - Object fundamentals
2. **[Factory Functions](./02-factory-functions.md)** - Creating objects dynamically
3. **[Constructors](./03-constructors.md)** - Constructor functions
4. **[Prototypes](./04-prototypes.md)** - Inheritance with prototypes
5. **[Classes](./05-classes.md)** - Modern class syntax
6. **[Inheritance](./06-inheritance.md)** - Extending classes
7. **[Encapsulation](./07-encapsulation.md)** - Private properties
8. **[Polymorphism](./08-polymorphism.md)** - Method overriding
9. **[Design Patterns](./09-design-patterns.md)** - Common patterns

## Quick Reference

### Object Literal
```javascript
const person = {
    name: "Alice",
    age: 25,
    greet() {
        console.log(`Hello, I'm ${this.name}`);
    }
};
```

### Constructor Function
```javascript
function Person(name, age) {
    this.name = name;
    this.age = age;
}

const person = new Person("Alice", 25);
```

### Class (Modern)
```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    greet() {
        console.log(`Hello, I'm ${this.name}`);
    }
}

const person = new Person("Alice", 25);
```

### Inheritance
```javascript
class Student extends Person {
    constructor(name, age, studentId) {
        super(name, age);
        this.studentId = studentId;
    }
}
```

---

## Learning Path

```
Objects Review → Factory Functions → Constructors 
→ Prototypes → Classes → Inheritance 
→ Encapsulation → Polymorphism → Design Patterns
```

## OOP Principles

1. **Encapsulation** - Bundle data and methods together
2. **Inheritance** - Extend functionality from parent classes
3. **Polymorphism** - Different objects respond to same method
4. **Abstraction** - Hide complex implementation details

---

## When to Use OOP

✅ Complex applications  
✅ Large teams  
✅ Code reusability  
✅ Maintainable structure  

❌ Simple scripts  
❌ One-time projects  
❌ Premature optimization  

## Real-World Analogy

Think of OOP like building with blueprints:

- **Class**: Blueprint for buildings
- **Object (Instance)**: Actual building built from blueprint
- **Properties**: Features of the building (floors, rooms, color)
- **Methods**: What the building can do (provide shelter, store things)
- **Inheritance**: Different building types (house, skyscraper, warehouse) extend base building features
- **Polymorphism**: Different building types respond to "provide shelter" differently

## Common Patterns

**Singleton pattern - single instance:**
```javascript
class Database {
  static instance = null;
  static getInstance() {
    if (!Database.instance) {
      Database.instance = new Database();
    }
    return Database.instance;
  }
}
```

**Strategy pattern - interchangeable algorithms:**
```javascript
class PaymentProcessor {
  constructor(strategy) {
    this.strategy = strategy;
  }
  process(amount) {
    return this.strategy.pay(amount);
  }
}
```

## Key Takeaways

- Classes are templates for creating objects
- Inheritance allows code reuse through hierarchy
- Encapsulation protects internal data
- Polymorphism enables flexible, extensible code
- Use OOP for complex applications, not simple scripts
- Modern JavaScript uses class syntax (ES6+)
- Understanding prototypes helps understand classes

## When NOT to Use OOP

- Simple utility functions
- Configuration files
- Prototypes and quick experiments
- Over-engineering small projects

## Best Practices

- Keep classes focused (Single Responsibility Principle)
- Use meaningful class and method names
- Favor composition over inheritance
- Don't create unnecessary deep hierarchies
- Use private fields for data protection
- Document public interfaces clearly

## Common Mistakes to Avoid

- Creating unnecessary deep inheritance chains
- Mixing OOP with functional approaches inconsistently
- Not using proper access modifiers (public/private)
- Creating God classes that do too much
- Not leveraging inheritance properly
- Forgetting to call super() in child constructors

## Practice Exercises

1. Create Shape classes (Rectangle, Circle) with area() methods
2. Build a Person class with Student and Employee subclasses
3. Create a Banking system with Account, SavingsAccount, CheckingAccount
4. Build a Game with Character, Player, Enemy classes
5. Create an e-commerce system with Product, Cart, Order classes

## Advanced Topics

- Abstract classes (conceptual - not enforced in JS)
- Mixins (combining multiple behaviors)
- Getters and setters
- Static methods and properties
- Private fields (#)
- Decorators (experimental feature)

---

**Course Section**: Object-Oriented Programming - Advanced Design  
**Author**: Solomon Kassa  
**Last Updated**: February 2026  
**Difficulty**: Advanced  
**Prerequisites**: Fundamentals, Control Flow, Functions, Objects & Arrays  
**Next**: Asynchronous JavaScript section

**Start with**: [Classes & Prototypes](./01-classes-prototypes.md)

---

[← Back to Main](../README.md) | [Async →](../07-ASYNC/README.md)
