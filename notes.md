# 🚀 Complete Setup Guide: React + Axios

Follow these steps to set up a new React project and implement the data fetching code using Axios.

---

## 🛠️ 1. Create the Project
First, we need to create a React application using Vite. Open your terminal and run:

```bash
# 1. Create the project (named 'my-axios-app')
npm create vite@latest my-axios-app -- --template react

# 2. Navigate into the folder
cd my-axios-app

# 3. Install standard dependencies
npm install
```

---

## 📦 2. Install Axios
We are using `axios` to fetch data, so we must install it separately.

```bash
npm install axios
```

---

## 📝 3. Create the Component
1.  Inside the `src` folder, create a new folder named `components`.
2.  Inside `components`, create a file named `Card.jsx`.
3.  Paste the following code (Optimized for React best practices):

```jsx
// src/components/Card.jsx
import React, { useEffect } from 'react'
import axios from "axios"

const Card = () => {
    // We define the async function *inside* to avoid React warnings
    useEffect(() => {
        const fetchData = async () => {
            try {
                const response = await axios.get("https://fakestoreapi.com/products")
                console.log(response.data) // Log the actual data
            } catch (error) {
                console.error("Error fetching data:", error)
            }
        }

        fetchData()
    }, []) // Empty array = run once on mount

    return (
        <div>
            This is a card (Check your console for data!)
        </div>
    )
}

export default Card
```

---

## 🔗 4. Use the Component in App.jsx
Now we need to display the `Card` component. Open `src/App.jsx` and replace its content with:

```jsx
// src/App.jsx
import Card from './components/Card'
import './App.css'

function App() {
  return (
    <div className="App">
      <h1>Axios Data Fetching</h1>
      <Card />
    </div>
  )
}

export default App
```

---

## ▶️ 5. Run the Project
Start the development server:

```bash
npm run dev
```

1.  Open the link shown in the terminal (usually `http://localhost:5173`).
2.  **Right-click** on the page and select **Inspect**.
3.  Go to the **Console** tab.
4.  You should see an array of products logged there! 🎉
