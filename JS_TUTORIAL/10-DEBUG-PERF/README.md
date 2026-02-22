# Debugging & Performance: Writing Better Code

Learn to debug problems and optimize JavaScript performance.

## Topics Covered

1. **[Debugging Tools](./01-debugging-tools.md)** - Browser DevTools
2. **[Console Methods](./02-console-methods.md)** - Logging and debugging
3. **[Breakpoints](./03-breakpoints.md)** - Step through code
4. **[Error Types](./04-error-types.md)** - Understanding errors
5. **[Error Handling](./05-error-handling.md)** - try/catch/finally
6. **[Performance Tips](./06-performance-tips.md)** - Optimization techniques
7. **[Memory Leaks](./07-memory-leaks.md)** - Avoiding memory issues

## Quick Reference

### Common Debugging Methods
```javascript
console.log("Basic logging")
console.error("Error message")
console.warn("Warning message")
console.table(array)        // Display as table
console.time("label")       // Start timer
console.timeEnd("label")    // End timer
console.trace()             // Stack trace
```

### Try/Catch
```javascript
try {
    // Code that might throw error
    riskyFunction();
} catch (error) {
    console.error("Error caught:", error.message);
} finally {
    // Always runs
    cleanup();
}
```

### Performance Timing
```javascript
console.time("fetch");
fetch("/api")
    .then(r => r.json())
    .finally(() => console.timeEnd("fetch"));
```

---

## Learning Path

```
Debugging Tools → Console Methods → Breakpoints 
→ Error Types → Error Handling → Performance Tips 
→ Memory Leaks
```

## Browser DevTools

### Opening DevTools
- **Chrome/Edge/Firefox**: F12 or Ctrl+Shift+I (Windows) / Cmd+Option+I (Mac)
- **Safari**: Enable in Preferences → Advanced, then Cmd+Option+I

### Key Tabs
- **Console** - Execute code and see logs
- **Sources** - Set breakpoints and step through code
- **Elements** - Inspect and modify HTML
- **Network** - Monitor HTTP requests
- **Performance** - Analyze performance
- **Memory** - Find memory leaks

---

## Debugging Workflow

1. **Reproduce the issue** - Know exactly what triggers the problem
2. **Understand the state** - Log variables and object values
3. **Use breakpoints** - Pause execution at key points
4. **Step through** - Execute code line by line
5. **Check stack trace** - See the call sequence
6. **Fix and test** - Verify the solution works

---

## Performance Tips

### Reduce Operations
```javascript
// ❌ Inefficient - recalculates length every iteration
for (let i = 0; i < array.length; i++) {
    console.log(array[i]);
}

// ✅ Better - cache length
const len = array.length;
for (let i = 0; i < len; i++) {
    console.log(array[i]);
}

// ✅ Best - use for-of
for (const item of array) {
    console.log(item);
}
```

### Minimize DOM Access
```javascript
// ❌ Inefficient - multiple DOM queries
for (let i = 0; i < 1000; i++) {
    document.querySelector("#result").innerHTML += i;
}

// ✅ Better - minimize DOM access
let html = "";
for (let i = 0; i < 1000; i++) {
    html += i;
}
document.querySelector("#result").innerHTML = html;
```

### Debounce/Throttle
```javascript
// Debounce - wait for pause
function debounce(func, delay) {
    let timeout;
    return function(...args) {
        clearTimeout(timeout);
        timeout = setTimeout(() => func(...args), delay);
    };
}

// Usage
window.addEventListener("resize", debounce(() => {
    console.log("Resized!");
}, 300));
```

---

## Common Error Types

```javascript
// SyntaxError - invalid code
const obj = { invalid syntax }

// ReferenceError - variable not defined
console.log(undefinedVariable)

// TypeError - wrong type
const num = 5;
num.toUpperCase()  // numbers don't have toUpperCase

// RangeError - invalid range
const arr = new Array(-1)

// Error - generic
throw new Error("Something went wrong")
```

---

## Memory Leaks

### Common Causes
```javascript
// ❌ Forgotten timer
const timer = setInterval(() => {
    // This never stops!
}, 1000);

// ✅ Clear it when done
clearInterval(timer);

// ❌ Forgotten event listener
element.addEventListener("click", handler);

// ✅ Remove when done
element.removeEventListener("click", handler);

// ❌ Circular references in closure
let data = new Array(1000000);
setTimeout(() => {
    console.log(data);  // Reference kept alive
}, 10000);

// ✅ Clear references
setTimeout(() => {
    console.log(data);
    data = null;  // Clear reference
}, 10000);
```

## Advanced Debugging

### Conditional Breakpoints
Set breakpoints that only trigger when condition is true
```javascript
// In DevTools, right-click breakpoint, add condition:
i > 5  // Only break when i is greater than 5
```

### Logging Best Practices
```javascript
// Use console.group for organization
console.group("User Data");
console.log("Name:", user.name);
console.log("Email:", user.email);
console.groupEnd();

// Use console.time for performance
console.time("API Call");
await fetch("/api/data");
console.timeEnd("API Call");

// Use console.assert for testing
console.assert(value > 0, "Value should be positive");
```

## Performance Metrics

### Key Metrics
- **FCP** (First Contentful Paint) - When content first appears
- **LCP** (Largest Contentful Paint) - When largest element loads
- **FID** (First Input Delay) - Time to respond to user input
- **CLS** (Cumulative Layout Shift) - Visual stability
- **TTFB** (Time to First Byte) - Server response time

### Measuring Performance
```javascript
// Using Performance API
const mark1 = performance.now();
doSomething();
const mark2 = performance.now();
console.log(`Took ${mark2 - mark1}ms`);

// Using PerformanceObserver
const observer = new PerformanceObserver((list) => {
    for (const entry of list.getEntries()) {
        console.log(`${entry.name}: ${entry.duration}ms`);
    }
});
observer.observe({ entryTypes: ["measure"] });
```

## Optimization Techniques

### Code Optimization
- Minimize function call overhead
- Use native methods (they're optimized)
- Avoid try/catch in loops
- Cache DOM queries and calculations
- Use string concatenation carefully (use array.join() for many strings)

### Network Optimization
- Minify code
- Compress images
- Use CDN for static files
- Lazy load content
- Code splitting for large apps

### Memory Optimization
- Clean up event listeners
- Remove unused timers
- Avoid global variables
- Be careful with closures
- Use proper data structures

## Key Takeaways

- **Debugging is a skill** - Practice makes it easier
- **Read error messages** - They usually tell you what's wrong
- **Use the console** - Your best friend for troubleshooting
- **Understand stack traces** - Shows the call sequence
- **Performance matters** - Small optimizations add up
- **Test your code** - Catch problems early
- **Monitor in production** - Real-world usage reveals issues

## Common Issues and Solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| Infinite loop | Loop condition always true | Check loop condition |
| Undefined error | Variable not declared | Check variable name, scope |
| Slow page | Inefficient code | Profile, optimize hot spots |
| Memory leak | Forgotten references | Clean up listeners, timers |
| CORS error | Cross-origin request | Configure CORS headers |

## Debugging Checklist

- [ ] Open DevTools (F12)
- [ ] Check Console for errors
- [ ] Log key variables
- [ ] Set breakpoints at suspicious code
- [ ] Step through execution
- [ ] Check Network tab for API issues
- [ ] Verify data before/after operations
- [ ] Check Performance tab for bottlenecks

## Practice Exercises

1. Debug a script with intentional errors
2. Find and fix a memory leak
3. Optimize a slow algorithm using profiling
4. Locate bugs in complex code using breakpoints
5. Fix a CORS issue
6. Resolve a timing-related bug
7. Optimize DOM manipulation

---

**Course Section**: Debugging & Performance - Writing Better Code  
**Author**: Solomon Kassa  
**Last Updated**: February 2026  
**Difficulty**: Advanced  
**Prerequisites**: All previous sections  
**Next**: Projects & Exercises

**Start with**: [Debugging Tools](./01-debugging-tools.md)

---

[← Back to Main](../README.md) | [Projects & Exercises →](../11-PROJECTS-EXERCISES/README.md)
