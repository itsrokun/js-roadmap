# js-roadmap

# Complete JavaScript Roadmap & Example Guide

This guide covers everything from the absolute basics to advanced concepts and practical projects. It includes the learning strategy, core syntax, and real-world code snippets.

---

## 🚀 Recommended Learning Strategy

**"Learn-Build" Loop:** Don't just read—code.
*   **Phase 1 (Logic):** Variables, Loops, Functions. *Project: CLI Calculator.*
*   **Phase 2 (UI):** DOM, Events. *Project: Score Keeper.*
*   **Phase 3 (Data):** Objects, Arrays, LocalStorage. *Project: Todo App.*
*   **Phase 4 (Async):** Fetch API, Promises. *Project: Weather App.*

---

## 1. JavaScript Basics

### Introduction & Setup
```javascript
console.log("Hello, World!"); 
console.warn("This is a warning");
console.error("This is an error");
```

### Variables (`var` vs `let` vs `const`)
```javascript
// ❌ Avoid var (Function scoped, hoisting issues)
var oldWay = "Avoid me"; 

// ✅ Use let (Block scoped, reassignable)
let score = 10;
score = 20; 

// ✅ Use const (Block scoped, constant reference)
const PI = 3.14159;
// PI = 3.14; // ❌ Error: Assignment to constant variable
```

### Data Types
```javascript
// Primitive Types
let name = "Alice";       // String
let age = 25;             // Number
let isStudent = true;     // Boolean
let empty = null;         // Null (Intentional empty value)
let unknown;              // Undefined (Uninitialized)
let bigNum = 999999999n;  // BigInt

// Reference Types
let person = { id: 1 };   // Object
let skills = ["JS", "CSS"]; // Array
```

### Operators & Coercion
```javascript
// Coercion (Automatic Type Conversion)
console.log("5" + 5);   // "55" (String wins in +)
console.log("5" - 2);   // 3 (String parsed to number in -)

// Comparison Operators
console.log(5 == "5");  // true (Loose equality - Avoid)
console.log(5 === "5"); // false (Strict equality - Use this!)

// Ternary Operator (Short if-else)
let status = (age >= 18) ? "Adult" : "Minor";
```

### Control Flow
```javascript
// If-Else
if (score > 50) {
    console.log("Pass");
} else {
    console.log("Fail");
}

// Switch Statement
let role = "admin";
switch (role) {
    case "admin": console.log("Full Access"); break;
    case "guest": console.log("Read Only"); break;
    default: console.log("No Access");
}

// Loops
// For Loop
for (let i = 0; i < 3; i++) console.log("Count: " + i);

// For...Of (Best for Arrays)
let colors = ["Red", "Blue"];
for (let color of colors) console.log(color);
```

---

## 2. Functions

### Declaration, Expression & Arrow
```javascript
// 1. Function Declaration (Hoisted)
function add(a, b) {
    return a + b;
}

// 2. Function Expression (Not Hoisted)
const subtract = function(a, b) {
    return a - b;
};

// 3. Arrow Function (Modern ES6)
const multiply = (a, b) => a * b;

// Implicit Return (One-liners)
const square = n => n * n;
```

### Parameters
```javascript
// Default Parameters
function greet(name = "User") {
    return `Hello, ${name}`;
}
console.log(greet()); // "Hello, User"
```

### Closures & IIFE
```javascript
// IIFE (Immediately Invoked Function Expression)
(function() {
    console.log("I run immediately and only once!");
})();

// Closure (Function remembering its outer scope)
function createCounter() {
    let count = 0;
    return function() {
        count++;
        return count;
    };
}
const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

---

## 3. Objects & Arrays

### Objects
```javascript
const car = {
    brand: "Toyota",
    model: "Corolla",
    // Method inside object
    start() {
        // 'this' refers to the object itself
        console.log(`${this.brand} engine started.`);
    }
};

// Accessing Properties
console.log(car.brand);      // Dot notation
console.log(car["model"]);   // Bracket notation
car.start();
```

### Arrays & Higher Order Methods
```javascript
const numbers = [1, 2, 3, 4, 5];

// Modifying Arrays
numbers.push(6);     // Add to end
numbers.pop();       // Remove from end
numbers.shift();     // Remove from start

// ✅ Map: Transform every element
const doubled = numbers.map(num => num * 2); 

// ✅ Filter: Select specific elements
const evens = numbers.filter(num => num % 2 === 0);

// ✅ Reduce: Accumulate values
const sum = numbers.reduce((total, num) => total + num, 0);

console.log(sum); // Sum of array
```

### JSON Handling
```javascript
const data = { id: 1, title: "Learn JS" };

// Object to String (for sending to API)
const jsonString = JSON.stringify(data); 

// String to Object (reading from API)
const parsedObj = JSON.parse(jsonString); 
```

---

## 4. Strings & Numbers

### String Methods
```javascript
const text = "JavaScript is Fun";

console.log(text.length);             // 17
console.log(text.toUpperCase());      // "JAVASCRIPT IS FUN"
console.log(text.includes("Script")); // true
console.log(text.slice(0, 10));       // "JavaScript"
console.log(text.split(" "));         // ["JavaScript", "is", "Fun"]
```

### Template Literals
```javascript
const item = "Coffee";
const price = 2.5;
// Use backticks ` ` for interpolation
console.log(`One ${item} costs $${price}`); 
```

### Math Object
```javascript
console.log(Math.max(10, 5, 20));  // 20
console.log(Math.floor(4.9));      // 4
console.log(Math.random());        // Random 0-1
```

---

## 5. DOM (Document Object Model)

### Selecting Elements
```javascript
const title = document.getElementById("main-title");
const buttons = document.querySelectorAll(".btn"); // Returns NodeList
const input = document.querySelector("input[name='email']");
```

### Modifying Elements
```javascript
title.textContent = "Welcome Back";
title.style.color = "blue";
title.classList.add("highlight"); // Add CSS class
input.value = "user@example.com";
```

### Event Handling
```javascript
const btn = document.querySelector("#save-btn");

btn.addEventListener("click", (event) => {
    event.preventDefault(); // Prevents form submit/refresh
    console.log("Button clicked!");
    event.stopPropagation(); // Stops event bubbling
});
```

### Creating Elements
```javascript
const list = document.querySelector("ul");
const newItem = document.createElement("li");
newItem.textContent = "New List Item";
list.appendChild(newItem);
```

---

## 6. ES6+ Modern JavaScript

### Destructuring
```javascript
// Object Destructuring
const user = { username: "dev1", country: "USA" };
const { username, country } = user;

// Array Destructuring
const coords = [10, 20];
const [x, y] = coords;
```

### Spread & Rest Operators
```javascript
// Spread (Expanding)
const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4]; // [1, 2, 3, 4]

// Rest (Gathering arguments)
const sumAll = (...args) => args.reduce((a, b) => a + b);
console.log(sumAll(1, 2, 3, 4)); // 10
```

### Classes
```javascript
class Animal {
    constructor(name) {
        this.name = name;
    }
    speak() {
        console.log(`${this.name} makes a noise.`);
    }
}

const dog = new Animal("Rex");
dog.speak();
```

---

## 7. Advanced Topics

### Recursion
```javascript
function factorial(n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
console.log(factorial(5)); // 120
```

### Call, Apply, Bind
```javascript
const person = { name: "John" };
function say(greeting) { console.log(`${greeting}, ${this.name}`); }

say.call(person, "Hello"); // Runs immediately
const sayLater = say.bind(person, "Hi"); // Returns function
sayLater();
```

---

## 8. Asynchronous JavaScript

### Promises
```javascript
const myPromise = new Promise((resolve, reject) => {
    const success = true;
    setTimeout(() => {
        if (success) resolve("Data fetched!");
        else reject("Error fetching data");
    }, 1000);
});

myPromise
    .then(data => console.log(data))
    .catch(err => console.error(err));
```

### Async / Await & Fetch API
This is the modern standard for network requests.
```javascript
async function getUserData() {
    try {
        const response = await fetch("https://jsonplaceholder.typicode.com/users/1");
        
        if (!response.ok) throw new Error("Network error");
        
        const data = await response.json();
        console.log("User:", data.name);
    } catch (error) {
        console.error("Failed:", error.message);
    }
}
getUserData();
```

---

## 9. Browser APIs

### Local Storage
```javascript
// Save
localStorage.setItem("theme", "dark");

// Retrieve
const theme = localStorage.getItem("theme");

// Remove
localStorage.removeItem("theme");
```

### Geolocation
```javascript
if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(pos => {
        console.log(`Lat: ${pos.coords.latitude}, Lon: ${pos.coords.longitude}`);
    });
}
```

---

## 10. Testing & Debugging

### Console Methods
```javascript
const users = [{id:1, name:"A"}, {id:2, name:"B"}];
console.table(users); // Displays array of objects as a table
console.time("timer");
// ... run code ...
console.timeEnd("timer"); // Checks how long code took
```

### Error Handling
```javascript
try {
    // Code that might fail
    let result = unknownFunction();
} catch (error) {
    console.error("Caught error:", error.message);
} finally {
    console.log("This runs regardless of error.");
}
```

---

## 11. Projects Logic

### 1. To-Do App Logic
```javascript
let todos = [];

function addTodo(text) {
    const todo = {
        id: Date.now(),
        text: text,
        completed: false
    };
    todos.push(todo);
    saveLocal();
}

function saveLocal() {
    localStorage.setItem("todos", JSON.stringify(todos));
}
```

### 2. Simple Calculator Logic
```javascript
function calculate(num1, num2, operator) {
    switch(operator) {
        case '+': return num1 + num2;
        case '-': return num1 - num2;
        case '*': return num1 * num2;
        case '/': return num2 !== 0 ? num1 / num2 : "Error";
        default: return null;
    }
}
```

### 3. Weather App (API Consumer)
```javascript
const apiKey = "YOUR_KEY_HERE";

async function getWeather(city) {
    const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}`;
    try {
        const res = await fetch(url);
        const data = await res.json();
        return {
            temp: data.main.temp,
            desc: data.weather[0].description
        };
    } catch (err) {
        console.log("City not found");
    }
}
```

---

## 12. Additional Resources

*   **MDN Web Docs (Reference):** [developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
*   **JavaScript.info (Tutorial):** [javascript.info](https://javascript.info)
*   **W3Schools (Examples):** [w3schools.com/js](https://www.w3schools.com/js/)
