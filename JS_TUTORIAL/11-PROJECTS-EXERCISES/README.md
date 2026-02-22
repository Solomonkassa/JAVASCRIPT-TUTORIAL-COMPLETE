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

---

[← Back to Main](../README.md)
