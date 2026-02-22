# Modern JavaScript: ES6+ Features

Master the modern features that make JavaScript powerful.

## Topics Covered

1. **[Let & Const](./01-let-const.md)** - Block-scoped variables
2. **[Arrow Functions](./02-arrow-functions.md)** - Concise function syntax
3. **[Template Literals](./03-template-literals.md)** - String interpolation
4. **[Destructuring](./04-destructuring.md)** - Unpacking values
5. **[Spread & Rest](./05-spread-rest.md)** - Spreading values
6. **[Default Parameters](./06-default-parameters.md)** - Function parameter defaults
7. **[Classes](./07-classes.md)** - Object-oriented programming
8. **[Modules](./08-modules.md)** - import/export
9. **[Async/Await](./09-async-await.md)** - Modern async syntax
10. **[Optional Chaining](./10-optional-chaining.md)** - Safe property access

## Quick Reference

### Destructuring
```javascript
const { name, age } = person;
const [first, second] = array;
```

### Spread Operator
```javascript
const merged = { ...obj1, ...obj2 };
const combined = [...arr1, ...arr2];
```

### Classes
```javascript
class Person {
    constructor(name) {
        this.name = name;
    }
}

const person = new Person("Alice");
```

### Async/Await
```javascript
async function getData() {
    const response = await fetch("/api");
    return response.json();
}
```

---

## Learning Path

```
Let & Const → Arrow Functions → Template Literals 
→ Destructuring → Spread/Rest → Default Parameters 
→ Classes → Modules → Async/Await → Optional Chaining
```

**ES6+ Means**:
- ES6 (2015) - Major update with classes, arrow functions, let/const
- ES7+ - Continuous updates with new features yearly

**Start with**: [Let & Const](./01-let-const.md)

---

## Why Learn Modern JavaScript?

✅ Cleaner, more readable code  
✅ Less boilerplate  
✅ Better performance  
✅ Industry standard  
✅ Enabled by all modern browsers  

---

[← Back to Main](../README.md) | [Debugging & Performance →](../10-DEBUG-PERF/README.md)
