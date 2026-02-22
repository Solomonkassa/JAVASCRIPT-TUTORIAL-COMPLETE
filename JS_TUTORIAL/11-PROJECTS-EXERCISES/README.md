# Projects & Exercises: Practice and Master JavaScript

Hands-on projects and exercises to solidify your JavaScript knowledge.

## Exercise Levels

### Beginner Level ⭐

Perfect for practicing fundamentals:

1. **Calculator**
   - Basic arithmetic operations
   - Input validation
   - Topics: functions, operators, conditionals
   - [View Exercise](#calculator)

2. **Number Guessing Game**
   - Random number generation
   - Loops and conditionals
   - Topics: while loops, if/else, Math.random()
   - [View Exercise](#number-guessing-game)

3. **To-Do List (Console)**
   - Array operations
   - Function creation
   - Topics: arrays, functions, loops
   - [View Exercise](#todo-list-console)

4. **Temperature Converter**
   - Function creation
   - Type conversion
   - Topics: functions, numbers, conditionals
   - [View Exercise](#temperature-converter)

### Intermediate Level ⭐⭐

Build real applications:

1. **To-Do List (DOM)**
   - HTML/CSS/JavaScript integration
   - DOM manipulation
   - Local storage
   - Topics: DOM, events, arrays, localStorage
   - [View Exercise](#todo-list-dom)

2. **Weather App**
   - API fetching
   - Data manipulation
   - DOM updates
   - Topics: async/await, fetch, JSON
   - [View Exercise](#weather-app)

3. **Quiz Application**
   - Array/object manipulation
   - Score calculation
   - DOM updates
   - Topics: arrays, objects, functions, events
   - [View Exercise](#quiz-application)

4. **Expense Tracker**
   - Data persistence
   - Complex calculations
   - DOM manipulation
   - Topics: arrays, objects, localStorage, events
   - [View Exercise](#expense-tracker)

### Advanced Level ⭐⭐⭐

Full-featured applications:

1. **Chat Application**
   - Real-time messaging
   - Server integration
   - Topics: async, fetch, events, DOM
   - [View Exercise](#chat-application)

2. **Shopping Cart**
   - State management
   - Complex logic
   - Payment integration
   - Topics: objects, arrays, classes, events
   - [View Exercise](#shopping-cart)

3. **Personal Finance Dashboard**
   - Charts and visualization
   - Complex calculations
   - Data visualization
   - Topics: charting libraries, data processing
   - [View Exercise](#finance-dashboard)

---

## Beginner Exercises

### Calculator

**Goal**: Create a calculator that performs basic arithmetic.

**Requirements**:
- Add, subtract, multiply, divide operations
- Input validation (handle invalid inputs)
- Display results
- Clear function

**Skills Practiced**:
- Functions
- Operators
- Conditionals
- Type conversion

**Starter Code**:
```javascript
function calculator(a, b, operation) {
    // Your code here
    // Return the result of the operation
}

console.log(calculator(10, 5, "+"));  // 15
console.log(calculator(10, 5, "-"));  // 5
console.log(calculator(10, 5, "*"));  // 50
console.log(calculator(10, 5, "/"));  // 2
```

**Full Solution**:
```javascript
function calculator(a, b, operation) {
    // Validate inputs
    if (typeof a !== "number" || typeof b !== "number") {
        return "Invalid input: numbers required";
    }
    
    switch(operation) {
        case "+":
            return a + b;
        case "-":
            return a - b;
        case "*":
            return a * b;
        case "/":
            if (b === 0) {
                return "Error: Division by zero";
            }
            return a / b;
        default:
            return "Invalid operation";
    }
}
```

**Resources**:
- [MDN: Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators)
- [Video: Calculator Tutorial](https://www.youtube.com/watch?v=sSqdmX0oxXU)

---

### Number Guessing Game

**Goal**: Create a game where user guesses a random number.

**Requirements**:
- Generate random number between 1-100
- Get user input (use prompt)
- Give hints (too high/too low)
- Count attempts
- Congratulate on correct guess

**Skills Practiced**:
- Loops
- Conditionals
- Math.random()
- Input/output

**Starter Code**:
```javascript
function guessingGame() {
    const secretNumber = Math.floor(Math.random() * 100) + 1;
    let attempts = 0;
    let guessed = false;
    
    // Your code here
}

guessingGame();
```

**Full Solution**:
```javascript
function guessingGame() {
    const secretNumber = Math.floor(Math.random() * 100) + 1;
    let attempts = 0;
    let guessed = false;
    
    while (!guessed) {
        const guess = prompt("Guess a number between 1 and 100:");
        const num = Number(guess);
        attempts++;
        
        if (isNaN(num)) {
            alert("Please enter a valid number");
            continue;
        }
        
        if (num === secretNumber) {
            alert(`Correct! You got it in ${attempts} attempts!`);
            guessed = true;
        } else if (num < secretNumber) {
            alert("Too low! Try again.");
        } else {
            alert("Too high! Try again.");
        }
    }
}
```

---

### To-Do List (Console)

**Goal**: Create a simple to-do list application.

**Requirements**:
- Add tasks
- Remove tasks
- List all tasks
- Mark as complete

**Skills Practiced**:
- Arrays
- Array methods
- Functions
- Loops

**Starter Code**:
```javascript
let todos = [];

function addTodo(task) {
    // Add task to array
}

function removeTodo(index) {
    // Remove task at index
}

function listTodos() {
    // Display all tasks
}

function markComplete(index) {
    // Mark task as complete
}
```

**Full Solution**:
```javascript
let todos = [];

function addTodo(task) {
    todos.push({
        task: task,
        completed: false
    });
    console.log(`Added: ${task}`);
}

function removeTodo(index) {
    if (index >= 0 && index < todos.length) {
        const removed = todos.splice(index, 1);
        console.log(`Removed: ${removed[0].task}`);
    }
}

function listTodos() {
    console.log("--- My To-Do List ---");
    todos.forEach((todo, index) => {
        const status = todo.completed ? "✓" : "○";
        console.log(`${index}: ${status} ${todo.task}`);
    });
}

function markComplete(index) {
    if (index >= 0 && index < todos.length) {
        todos[index].completed = true;
        console.log(`Completed: ${todos[index].task}`);
    }
}

// Usage
addTodo("Learn JavaScript");
addTodo("Build a project");
addTodo("Master async/await");
listTodos();
markComplete(0);
listTodos();
```

---

## Intermediate Exercises

### To-Do List (DOM)

**Goal**: Create an interactive to-do list with HTML interface.

**Requirements**:
- Add tasks with button
- Delete tasks
- Mark as complete
- Persist to localStorage
- Visual feedback

**Skills Practiced**:
- DOM manipulation
- Event listeners
- Array methods
- localStorage
- HTML/CSS

**Starter Code**:
```html
<!DOCTYPE html>
<html>
<head>
    <title>To-Do List</title>
    <style>
        body { font-family: Arial; padding: 20px; }
        #todoInput { padding: 10px; width: 300px; }
        button { padding: 10px 20px; cursor: pointer; }
        #todoList { margin-top: 20px; }
        li { padding: 10px; margin: 5px 0; }
        li.completed { text-decoration: line-through; opacity: 0.5; }
    </style>
</head>
<body>
    <h1>My To-Do List</h1>
    <input id="todoInput" type="text" placeholder="Add a new task">
    <button onclick="addTodo()">Add</button>
    <ul id="todoList"></ul>

    <script>
        let todos = [];

        function addTodo() {
            // Your code here
        }

        function deleteTodo(index) {
            // Your code here
        }

        function toggleComplete(index) {
            // Your code here
        }

        function renderTodos() {
            // Your code here
        }

        renderTodos();
    </script>
</body>
</html>
```

**Resources**:
- [MDN: DOM Manipulation](https://developer.mozilla.org/en-US/docs/Web/API/Document)
- [Video: Todo App Tutorial](https://www.youtube.com/watch?v=MkESyVB4oNo)

---

### Weather App

**Goal**: Fetch and display weather data from an API.

**Requirements**:
- Search for cities
- Display weather data
- Show temperature, humidity, conditions
- Format data nicely

**Skills Practiced**:
- Fetch API
- Async/await
- JSON parsing
- DOM updates
- Error handling

**Resources**:
- [OpenWeatherMap API](https://openweathermap.org/api) - Free weather data
- [MDN: Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [Video: Weather App Tutorial](https://www.youtube.com/watch?v=rRslU2jHqUw)

---

### Quiz Application

**Goal**: Create an interactive quiz.

**Requirements**:
- Multiple choice questions
- Score calculation
- Timer (optional)
- Results display
- Questions from data structure

**Skills Practiced**:
- Arrays of objects
- DOM manipulation
- Event listeners
- Calculations
- Data structures

**Resources**:
- [MDN: Events](https://developer.mozilla.org/en-US/docs/Web/Events)
- [Video: Quiz App Tutorial](https://www.youtube.com/watch?v=riDzcEQbX6k)

---

## Advanced Exercises

### Chat Application

**Goal**: Real-time messaging application.

**Requirements**:
- User login
- Message sending
- Real-time updates
- User list
- Persist messages

**Skills Practiced**:
- WebSockets or Server integration
- async/await
- Complex state management
- Real-time updates

**Resources**:
- [Socket.io](https://socket.io/) - Real-time communication
- [Express.js](https://expressjs.com/) - Server framework
- [Video: Chat App with Socket.io](https://www.youtube.com/watch?v=eQs2DJ_3UGE)

---

### Shopping Cart

**Goal**: Fully functional shopping cart system.

**Requirements**:
- Product display
- Add/remove items
- Calculate totals
- Tax calculation
- Checkout

**Skills Practiced**:
- Complex data structures
- Calculations
- DOM manipulation
- Events
- State management

**Resources**:
- [MDN: localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)
- [Video: Shopping Cart Tutorial](https://www.youtube.com/watch?v=eJZCNg5Cdhc)

---

## Exercise Resources

### Online Platforms

**Practice Coding**:
- [CodeWars](https://www.codewars.com/) - Coding challenges with JavaScript
- [HackerRank](https://www.hackerrank.com/) - Problem solving
- [LeetCode](https://leetcode.com/) - Algorithm challenges
- [Exercism](https://exercism.org/) - Structured exercises
- [Project Euler](https://projecteuler.net/) - Math problems

**Interactive Tutorials**:
- [Codecademy](https://www.codecademy.com/learn/introduction-to-javascript)
- [freeCodeCamp](https://www.freecodecamp.org/)
- [Scrimba](https://scrimba.com/learn/javascript)
- [Udemy](https://www.udemy.com/) - Full courses

### Video Resources

**Beginner Friendly**:
- [JavaScript Fundamentals by Traversy Media](https://www.youtube.com/watch?v=9WIWNJVvPEM&list=PLillGF-RfqbbnEluLjSXKSkQvWmEAl-5F)
- [JavaScript Course by freeCodeCamp](https://www.youtube.com/watch?v=PkZNo7MFNFg)
- [HTML/CSS/JS by Kevin Powell](https://www.youtube.com/user/kevinkouchner)

**Project Based**:
- [Build Real Projects by Traversy Media](https://www.youtube.com/watch?v=K8uJRVzt6MY&list=PLillGF-RfqbbQkYVKqOCJlPcxkJ_NNXxE)
- [JavaScript Projects by Ania Kubow](https://www.youtube.com/watch?v=kHz3yzRWCRY&list=PLSsABihHfucnfPb8qfqHCK6kBKVRmL5N-)

---

## Tips for Success

1. **Start Small** - Begin with beginner exercises
2. **Understand Concepts** - Don't just copy code, understand it
3. **Break it Down** - Divide complex problems into smaller parts
4. **Test Often** - Run code frequently to check progress
5. **Debug Actively** - Use console.log and browser dev tools
6. **Read Solutions** - Study how others solved problems
7. **Refactor** - Improve your code after getting it working
8. **Challenge Yourself** - Try variations and extensions

---

## Next Steps After Exercises

- Build your own projects
- Contribute to open source
- Create a portfolio
- Learn frameworks (React, Vue, Angular)
- Explore backend (Node.js)

## Your Learning Journey

```
Beginner Exercises (Foundation)
    ↓
Intermediate Projects (Application)
    ↓
Advanced Projects (Mastery)
    ↓
Portfolio Projects (Professional)
    ↓
Real-World Applications (Career)
```

## After You Master These Exercises

### Next Skills to Learn
- **Frameworks**: React, Vue, Angular - Build modern web apps
- **Backend**: Node.js, Express - Write server-side code
- **Databases**: MongoDB, PostgreSQL - Store and retrieve data
- **APIs**: REST, GraphQL - Build web services
- **DevTools**: Git, GitHub, VS Code - Professional workflow
- **Testing**: Jest, Mocha - Write reliable code
- **Build Tools**: Webpack, Vite - Optimize applications

### Building Your Portfolio
1. Complete projects from this course
2. Build personal projects solving real problems
3. Contribute to open source
4. Create GitHub portfolio
5. Share your code with others
6. Write about what you learned

### Tips for Success with These Exercises

**Before Starting**:
- Review the relevant tutorial section
- Read all requirements carefully
- Plan your approach on paper
- Identify the JavaScript concepts needed

**While Working**:
- Write code incrementally (don't write everything at once)
- Test frequently with console.log
- Break complex tasks into smaller functions
- Use browser DevTools to debug
- Reference past examples when stuck

**After Completion**:
- Refactor your code for clarity
- Add comments explaining complex logic
- Test edge cases (empty inputs, large numbers, etc.)
- Optimize for performance
- Challenge yourself with variations

## How to Approach Each Exercise

### Step 1: Understand Requirements
- Read the goal and requirements
- Know what inputs and outputs are expected
- Understand the user experience

### Step 2: Plan Your Approach
```javascript
// Example planning for To-Do List
// 1. Create data structure for todos
// 2. Create function to add todo
// 3. Create function to remove todo
// 4. Create function to display todos
// 5. Connect to HTML buttons
```

### Step 3: Implement Incrementally
- Write one small feature at a time
- Test each feature before moving on
- Don't write everything at once

### Step 4: Debug and Refine
- Use console.log to check values
- Use browser DevTools breakpoints
- Refactor for clarity
- Handle edge cases

### Step 5: Extend and Challenge
- Add new features
- Improve user interface
- Optimize performance
- Make it your own

## Common Challenges and Solutions

**Challenge**: "I don't know where to start"  
**Solution**: Look at similar completed examples, plan pseudocode first, start with smallest feature

**Challenge**: "My code works but it's messy"  
**Solution**: Refactor by extracting functions, use meaningful names, add comments

**Challenge**: "I keep getting errors"  
**Solution**: Read error message carefully, use console.log to track values, step through with debugger

**Challenge**: "I'm stuck on a feature"  
**Solution**: Take a break, review the concept in tutorials, look at similar examples, ask for help

## Grading Your Own Work

### Beginner Project Checklist
- [ ] Code runs without errors
- [ ] All requirements are met
- [ ] Variable names are meaningful
- [ ] Functions have single responsibilities
- [ ] No console errors

### Intermediate Project Checklist
- [ ] All beginner criteria met
- [ ] Code is DRY (Don't Repeat Yourself)
- [ ] Good error handling
- [ ] Clean HTML/CSS/JavaScript separation
- [ ] Code is readable and well-organized

### Advanced Project Checklist
- [ ] All intermediate criteria met
- [ ] Efficient algorithms
- [ ] No memory leaks
- [ ] Good performance
- [ ] Extensible and maintainable code
- [ ] Professional quality

## Exercise Difficulty Progression

```
Fundamentals Understanding
    ↓
Single Concept Practice (Calculator)
    ↓
Multiple Concepts (To-Do List)
    ↓
DOM Integration (Weather App)
    ↓
API Integration (Chat App)
    ↓
Complex State (Shopping Cart)
    ↓
Advanced Patterns (Finance Dashboard)
    ↓
Custom Projects (Your Ideas!)
```

## Important: Learn By Doing

The most important thing is to **actually write the code**. Reading about programming is useful, but nothing replaces the experience of:
- Typing out code
- Debugging errors
- Finding solutions
- Building something from scratch

Challenge yourself to complete at least 3 exercises from each level!

---

**Course Section**: Projects & Exercises - Practice and Master JavaScript  
**Author**: Solomon Kassa  
**Last Updated**: February 2026  
**Difficulty**: Beginner to Advanced  
**Prerequisites**: All previous sections (depending on exercise level)  
**Next**: Build your own projects and advance your career

---

[← Back to Main](../README.md)
