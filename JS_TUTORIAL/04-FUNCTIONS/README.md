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

## Common Function Patterns

**Higher-order functions (functions that return functions):**
```javascript
function createMultiplier(multiplier) {
  return function(number) {
    return number * multiplier;
  };
}
const double = createMultiplier(2);
console.log(double(5)); // 10
```

**Callback functions (functions passed as arguments):**
```javascript
function processArray(arr, callback) {
  for (let i = 0; i < arr.length; i++) {
    callback(arr[i]);
  }
}
processArray([1, 2, 3], (item) => console.log(item * 2));
```

**IIFE (Immediately Invoked Function Expression):**
```javascript
(function() {
  console.log("This runs immediately!");
})();
```

## Why Functions Matter

- **DRY Principle**: Don't Repeat Yourself - write once, use many times
- **Modularity**: Break complex problems into smaller pieces
- **Testability**: Easier to test individual functions
- **Reusability**: Use same function in different parts of code
- **Maintainability**: Update logic in one place

## Key Takeaways

- Functions are fundamental building blocks of JavaScript
- Always use arrow functions or function declarations (avoid `var` functions)
- Understand scope to avoid variable conflicts
- Closures are powerful for data privacy and callbacks
- The `this` keyword refers to the calling context
- Hoisting affects how you can use functions

## Practice Exercises

1. Create a calculator function with add, subtract, multiply, divide operations
2. Write a function that returns another function (closure)
3. Create a function that accepts variable number of arguments
4. Build a function composition utility
5. Write callback-based functions for array operations

## Common Mistakes to Avoid

- Forgetting to return values from functions
- Confusing function declaration and arrow function syntax
- Not understanding variable scope properly
- Returning undefined when values are needed
- Using `this` incorrectly in arrow functions (no binding)

## Performance Tips

- Functions create scope (slight performance cost)
- Arrow functions are generally faster
- Avoid deep nesting of functions
- Cache function results if computing expensive values
- Use memoization for frequently-called pure functions

---

**Course Section**: Functions - Reusable Code Blocks  
**Author**: Solomon Kassa  
**Last Updated**: February 2026  
**Difficulty**: Intermediate  
**Prerequisites**: Fundamentals, Control Flow  
**Next**: Objects & Arrays section

**Start with**: [Function Basics](./01-function-basics.md)

---

[← Back to Main](../README.md) | [Objects & Arrays →](../05-OBJECTS-ARRAYS/README.md)
