# Functions: Reusable Code Blocks

Master function declarations, parameters, and best practices.

## Topics Covered

1. **[Function Basics](./01-function-basics.md)** - Declaring, calling, parameters, return values, arrow functions
2. **[Closures and Scope](./02-closures-scope.md)** - Scope chain, lexical scope, closures, this keyword, hoisting

## Learning Path

```
Function Basics → Closures & Scope → Ready for OOP!
```

## Key Concepts

- **Function Declaration**: Traditional way to define functions
- **Arrow Functions**: Modern ES6+ syntax with implicit returns
- **Parameters & Arguments**: How to pass data to functions
- **Return Values**: How functions return data
- **Scope**: Where variables are accessible
- **Closures**: Functions that remember their environment
- **This Keyword**: Context reference in functions
- **Hoisting**: How JavaScript moves declarations to top

## Quick Reference

```javascript
// Function declaration
function greet(name) {
    return `Hello, ${name}!`;
}

// Arrow function
const greet = (name) => `Hello, ${name}!`;

// Function with default parameter
function add(a = 0, b = 0) {
    return a + b;
}
```

**Start with**: [Function Basics](./01-function-basics.md)

---

[← Back to Main](../README.md) | [Objects & Arrays →](../05-OBJECTS-ARRAYS/README.md)
