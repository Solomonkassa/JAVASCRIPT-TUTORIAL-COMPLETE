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

## Real-World Use Cases

**Objects for user data:**
```javascript
const user = {
  id: 1,
  name: 'Alice',
  email: 'alice@example.com',
  greet() {
    return `Hello, I'm ${this.name}`;
  }
};
```

**Arrays for collections:**
```javascript
const products = [
  { id: 1, name: 'Laptop', price: 999 },
  { id: 2, name: 'Mouse', price: 25 },
  { id: 3, name: 'Keyboard', price: 75 }
];
const total = products.reduce((sum, p) => sum + p.price, 0);
```

**Complex data structures:**
```javascript
const company = {
  name: 'TechCorp',
  departments: [
    { name: 'Engineering', employees: ['Alice', 'Bob'] },
    { name: 'Sales', employees: ['Carol', 'David'] }
  ]
};
```

## Key Takeaways

- Objects store data as key-value pairs (like real-world entities)
- Arrays store ordered lists of items
- Both are passed by reference (modifications affect original)
- Destructuring makes code cleaner and more readable
- Array methods like map, filter, reduce are essential
- Understanding these structures is critical for any JavaScript work

## Advanced Patterns

- **Immutability**: Use spread operator to avoid modifying original data
- **Method chaining**: Chain array methods for powerful transformations
- **Deep cloning**: Use `JSON.parse(JSON.stringify(obj))` or spread deeply
- **Object composition**: Build complex objects from simpler ones
- **Factory functions**: Create objects with default properties

## Common Mistakes to Avoid

- Using `const` but then modifying object properties (const prevents reassignment, not mutation)
- Confusing `map()` and `forEach()` - map returns new array, forEach doesn't
- Not understanding that arrays/objects are passed by reference
- Using `===` to compare objects (always false, compare properties instead)
- Forgetting that spread operator does shallow copy, not deep copy

## Performance Considerations

- Array methods: map, filter, reduce create new arrays (memory cost)
- Object property access is fast, even with many properties
- Avoid very large arrays if possible
- Use `for` loops for simple iterations if performance matters
- Object lookup is O(1), array access is O(1), finding items is O(n)

## Practice Exercises

1. Create a student object with properties and methods
2. Write functions to add, remove, and find items in an array
3. Transform array of objects using map
4. Filter products by price range
5. Combine reduce with map/filter for complex transformations
6. Use destructuring to extract nested data
7. Clone objects and arrays properly
8. Create a shopping cart with add/remove/calculate total

## Exercises - Data Transformation

1. Convert array of names to array of objects with id and name
2. Filter array of numbers and get only even numbers
3. Calculate sum, average, min, max of array values
4. Group array items by a property
5. Sort objects by multiple criteria
6. Create lookup object from array for fast searching

---

**Course Section**: Objects & Arrays - Essential Data Structures  
**Author**: Solomon Kassa  
**Last Updated**: February 2026  
**Difficulty**: Intermediate  
**Prerequisites**: Fundamentals, Control Flow, Functions  
**Next**: Object-Oriented Programming section

**Start with**: [Objects](./01-objects.md)

---

[← Back to Main](../README.md) | [OOP →](../06-OOP/README.md)
