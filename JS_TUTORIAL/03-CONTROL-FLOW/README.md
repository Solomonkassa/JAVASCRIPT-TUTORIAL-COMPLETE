# Control Flow: Making Decisions

Learn how to control program execution with conditions and loops. This is essential for writing dynamic, responsive code.

## Topics Covered

1. **[If/Else/Else If Statements](./01-if-else.md)** - Conditional execution based on true/false conditions
2. **[Loops: For, While, Do...While, For...In, For...Of](./02-loops.md)** - Repeating code multiple times
3. **[Switch Statements](./03-switch-statements.md)** - Multiple conditions using switch

## Learning Path

```
If/Else → Loops → Switch → Combine All!
```

## Quick Comparison

| Statement | Use Case | Example |
|-----------|----------|---------|
| if/else | Single or few conditions | if (age >= 18) { canVote = true } |
| switch | Many cases, same variable | switch(day) { case 1: ... } |
| for | Fixed number of iterations | for (let i = 0; i < 10; i++) |
| while | Unknown iterations | while (input !== 'exit') |
| for...in | Loop object properties | for (let key in object) |
| for...of | Loop array values | for (let item of array) |

## Key Concepts

- **Conditional execution**: Run code only when certain conditions are true
- **Loops**: Repeat code without writing it multiple times
- **Break/Continue**: Control loop flow
- **Nested structures**: Combine conditions and loops for complex logic

## Real-World Examples

- **E-commerce**: If item is in stock → show "Buy" button, else show "Out of Stock"
- **Games**: Loop through all players, for each player loop through their items
- **Validation**: If email is invalid → show error message
- **Data processing**: Loop through array and filter/transform data based on conditions

## Common Patterns

**Checking user input:**
```javascript
if (input === null || input === undefined) {
  console.log("Please provide input");
} else {
  processInput(input);
}
```

**Looping through data:**
```javascript
for (let i = 0; i < items.length; i++) {
  console.log(items[i]);
}
```

**Handling multiple cases:**
```javascript
switch (status) {
  case 'pending': handlePending(); break;
  case 'success': handleSuccess(); break;
  default: handleError();
}
```

## Key Takeaways

- **If/else** handles true/false decisions
- **Switch** is cleaner for multiple specific cases
- **For loops** when you know iteration count
- **While loops** when count is unknown
- **Break/continue** control loop flow
- **Nested structures** combine multiple conditions and loops

## Practice Exercises

1. Write a program that grades test scores (90+: A, 80+: B, 70+: C, etc.)
2. Create a loop that prints multiplication tables from 1 to 10
3. Build a simple menu system using switch statements
4. Write validation logic for email format using if/else
5. Create a nested loop to generate a pyramid pattern

## Common Mistakes to Avoid

- Forgetting break in switch statements (causes fall-through)
- Using assignment (=) instead of comparison (==, ===)
- Infinite loops (forgetting loop increment)
- Not updating loop counter variables
- Confusing for...in and for...of loops

---

**Course Section**: Control Flow - Making Decisions  
**Author**: Solomon Kassa  
**Last Updated**: February 2026  
**Difficulty**: Beginner-Intermediate  
**Prerequisites**: Fundamentals section  
**Next**: Functions section

**Start with**: [If/Else Statements](./01-if-else.md)

---

[← Back to Main](../README.md) | [Functions →](../04-FUNCTIONS/README.md)
