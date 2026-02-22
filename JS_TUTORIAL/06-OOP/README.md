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

---

**Start with**: [Objects Review](./01-objects-review.md)

---

[← Back to Main](../README.md) | [Async →](../07-ASYNC/README.md)
