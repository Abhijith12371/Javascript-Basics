# ⚛️ The Complete React.js Learning Guide

Welcome to the **Complete React Guide**! This document is designed to take you from a React beginner to building complex applications.

## Table of Contents
1. [Introduction](#1-introduction)
2. [Project Setup (Vite)](#2-project-setup-vite)
3. [JSX & Components](#3-jsx--components)
4. [Props & State](#4-props--state)
5. [Hooks (The Core)](#5-hooks-the-core)
6. [Handling Events](#6-handling-events)
7. [Conditional Rendering & Lists](#7-conditional-rendering--lists)
8. [Forms](#8-forms)
9. [React Router](#9-react-router)
10. [Context API (State Management)](#10-context-api)
11. [API Calls](#11-api-calls)

---

## 1. Introduction
React is a JavaScript library for building user interfaces, developed by Facebook.
- **Single Page Applications (SPA)**: React loads a single HTML file and dynamically updates content.
- **Virtual DOM**: React updates a lightweight copy of the DOM specifically for performance.

---

---

## 2. Project Setup (Vite)

Value Ease and Speed? Use Vite!

### Step 1: Create Project
Open terminal and run:
```bash
npm create vite@latest my-app -- --template react
```

### Step 2: Install & Run
```bash
cd my-app
npm install
npm run dev
```
Open `http://localhost:5173` to see your app!

---

## 3. JSX & Components

### JSX (JavaScript XML)
Allows us to write HTML-like syntax inside JavaScript.
```jsx
const element = <h1>Hello, React!</h1>;
```

### Components
Building blocks of UI. We prioritize **Functional Components**.

```jsx
// Functional Component
function Welcome() {
  return <h1>Hello World</h1>;
}

export default Welcome;
```

---

## 4. Props & State

### Props (Properties)
Read-only data passed from parent to child.
```jsx
// Parent
<Greeting name="Alice" />

// Child
function Greeting(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

### State
Data managed *within* the component that can change over time.
```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0); // Initial value 0

  return (
    <button onClick={() => setCount(count + 1)}>
      Count: {count}
    </button>
  );
}
```

---

## 5. Hooks (The Core)

### `useState`
Manages state in functional components.
```jsx
const [age, setAge] = useState(25);
```

### `useEffect`
Handles side effects (fetching data, subscriptions, manual DOM changes).
Runs after every render by default.
```jsx
import { useEffect } from 'react';

useEffect(() => {
  console.log("Component mounted or updated");

  return () => {
    console.log("Cleanup (like ComponentWillUnmount)");
  };
}, [dependency]); // Runs only when 'dependency' changes
```

### `useRef`
Access DOM elements directly or store mutable values without re-rendering.
```jsx
const inputRef = useRef(null);
// <input ref={inputRef} />
inputRef.current.focus();
```

---

## 6. Handling Events
React events are camelCase (`onClick` instead of `onclick`).
```jsx
function Button() {
  const handleClick = (e) => {
    e.preventDefault();
    alert("Clicked!");
  };

  return <button onClick={handleClick}>Click Me</button>;
}
```

---

## 7. Conditional Rendering & Lists

### Conditionals
Use Ternary Operators or `&&`.
```jsx
{isLoggedIn ? <LogoutButton /> : <LoginButton />}
{hasMessages && <p>You have new messages!</p>}
```

### Lists
Use `.map()` to render arrays. **Always** provide a unique `key`.
```jsx
const users = ['Alice', 'Bob', 'Charlie'];

return (
  <ul>
    {users.map((user, index) => (
      <li key={index}>{user}</li>
    ))}
  </ul>
);
```

---

## 8. Forms
Controlled components: React controls the input value.
```jsx
const [name, setName] = useState("");

<input 
  value={name} 
  onChange={(e) => setName(e.target.value)} 
/>
```

---

## 9. React Router
Standard routing library for React.
`npm install react-router-dom`

```jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link> | <Link to="/about">About</Link>
      </nav>
      
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

## 10. Context API
Avoids "Prop Drilling" (passing props down many levels).

1. **Create Context**
```jsx
const UserContext = React.createContext();
```

2. **Provide Context**
```jsx
<UserContext.Provider value="Alice">
  <ChildComponent />
</UserContext.Provider>
```

3. **Consume Context**
```jsx
import { useContext } from 'react';
const user = useContext(UserContext); // "Alice"
```

---

## 11. API Calls (Best Practice)
Combine `useState` and `useEffect`.
```jsx
const [data, setData] = useState(null);

useEffect(() => {
  fetch('https://api.example.com/data')
    .then(res => res.json())
    .then(data => setData(data));
}, []); // Empty dependency array = run once
```

---
*Happy Hacking! ⚛️*
