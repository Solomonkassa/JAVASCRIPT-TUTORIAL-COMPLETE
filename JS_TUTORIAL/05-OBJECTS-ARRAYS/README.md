# Objects & Arrays: Data Structures

Master working with JavaScript's most important data structures. Arrays and objects are foundational to every JavaScript application.

## Topics Covered

1. **[Objects](./01-objects.md)** - Creating objects, properties, methods, destructuring, Object utilities
2. **[Arrays](./02-arrays.md)** - Creating arrays, methods (map, filter, reduce), iteration, destructuring

## Learning Path

```
Objects → Arrays → Master Data Structures!
```

## Key Concepts

### Objects - Store related data with keys
- Object literal syntax: `{ key: value }`
- Accessing properties: dot notation `obj.key` and bracket `obj['key']`
- Adding/modifying properties dynamically
- Methods: Functions stored in objects
- The `this` keyword in methods
- Destructuring: Extract properties cleanly
- Object.keys(), Object.values(), Object.entries()
- Spread operator: `{ ...obj1, ...obj2 }`
- Freezing and sealing objects

### Arrays - Store ordered collections
- Array literal syntax: `[1, 2, 3]`
- Accessing by index: `arr[0]`
- Adding/removing elements: push, pop, shift, unshift, splice
- Finding elements: indexOf, includes, find, findIndex
- Transforming: map, filter, reduce
- Iterating: forEach, for...of, map, filter
- Sorting and reversing
- Joining and slicing
- Destructuring: Extract elements cleanly
- Spread operator: `[...arr1, ...arr2]`

## Common Array Methods

| Method | Purpose | Example |
|--------|---------|---------|
| `map()` | Transform each element | `arr.map(x => x * 2)` |
| `filter()` | Keep matching elements | `arr.filter(x => x > 5)` |
| `reduce()` | Accumulate into single value | `arr.reduce((sum, x) => sum + x, 0)` |
| `forEach()` | Loop through elements | `arr.forEach(x => console.log(x))` |
| `find()` | Get first matching element | `arr.find(x => x.id === 1)` |
| `sort()` | Sort elements | `arr.sort((a, b) => a - b)` |
| `includes()` | Check if element exists | `arr.includes(5)` |
| `slice()` | Get portion of array | `arr.slice(1, 3)` |

## Quick Code Reference

```javascript
// Objects
const person = { name: 'John', age: 30 };
person.city = 'NYC';               // Add property
const { name, age } = person;      // Destructure
Object.keys(person);               // ['name', 'age', 'city']

// Arrays
const numbers = [1, 2, 3, 4, 5];
numbers.push(6);                   // [1,2,3,4,5,6]
const doubled = numbers.map(x => x * 2);  // Transform
const evens = numbers.filter(x => x % 2 === 0);  // Filter
const sum = numbers.reduce((a, b) => a + b, 0);  // Reduce

// Destructuring
const [first, second, ...rest] = numbers;  // first=1, second=2, rest=[3,4,5]

// Spread
const merged = { ...person, job: 'Developer' };
const combined = [...[1, 2], ...[3, 4]];  // [1,2,3,4]
```

**Start with**: [Objects](./01-objects.md)

---

[← Back to Main](../README.md) | [OOP →](../06-OOP/README.md)
