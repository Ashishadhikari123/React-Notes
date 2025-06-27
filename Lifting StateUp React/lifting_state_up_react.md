
# 🔼 Lifting State Up in React (Simplified)

## 🧠 What is "Lifting State Up"?

**Lifting state up** means **moving the state from a child component to their common parent**, so **multiple components can share and access the same data**.

---

## 🎯 Why Do We Need It?

React uses **one-way data flow** (parent → child).  
If two or more components need the **same data**, we **lift** the state to a common parent to:

- Avoid duplication
- Keep things in sync
- Have one "source of truth"

---

## 🧪 Example Scenario

You want:
- A component where you **type a name**
- Another that shows a **greeting** using that name

These components must share the `name` state.

---

## ✅ Example Code

```jsx
import React, { useState } from 'react';

function App() {
  const [name, setName] = useState('');

  return (
    <div>
      <NameInput name={name} setName={setName} />
      <Greeting name={name} />
    </div>
  );
}

function NameInput({ name, setName }) {
  return (
    <input
      type="text"
      value={name}
      onChange={(e) => setName(e.target.value)}
      placeholder="Enter your name"
    />
  );
}

function Greeting({ name }) {
  return <h2>Hello, {name || "Stranger"}!</h2>;
}
```

---

## 🔍 How It Works

- `App` holds the shared state (`name`)
- `NameInput` updates the name using `setName`
- `Greeting` uses the same state to display a message

✅ Both components stay in sync!

---

## 📌 Summary

| Concept           | Explanation                                     |
|-------------------|-------------------------------------------------|
| Lifting state up  | Move state to common parent                     |
| Use case          | Shared data between multiple children           |
| Benefit           | Single source of truth and consistent UI        |

---

## ✅ Use Lifting State Up When...

- You want to sync data between components
- You want to avoid having duplicate state logic
- You want a centralized control point for related data
