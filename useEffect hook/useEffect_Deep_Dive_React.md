# Deep Dive into useEffect Hook in React

## Table of Contents

1. [What is `useEffect`](#what-is-useeffect)
2. [Syntax](#syntax)
3. [Behavior Based on Dependency Array](#behavior-based-on-dependency-array)
4. [Real-World Use Cases](#real-world-use-cases)
   - [1. Fetching Data on Component Mount](#1-fetching-data-on-component-mount)
   - [2. Updating Document Title Dynamically](#2-updating-document-title-dynamically)
   - [3. Setting and Clearing Timers](#3-setting-and-clearing-timers)
   - [4. Listening to Window Resize](#4-listening-to-window-resize)
5. [Cleanup in useEffect](#cleanup-in-useeffect)
6. [Pro Tips](#pro-tips)
7. [Summary](#summary)

---

## What is `useEffect`

`useEffect` is a React Hook that allows you to perform **side effects** in functional components.

**Side effects include:**

- Fetching data
- DOM manipulation
- Setting up subscriptions
- Timers (e.g., `setInterval`, `setTimeout`)
- Logging
- Cleanup logic

---

## Syntax

```jsx
useEffect(() => {
  // Code to run on mount or update

  return () => {
    // Optional cleanup code
  };
}, [dependencies]);
```

---

## Behavior Based on Dependency Array

| Dependency Array | When It Runs                              |
| ---------------- | ----------------------------------------- |
| `undefined`      | Runs **after every render**               |
| `[]`             | Runs **only once** after the first render |
| `[var1, var2]`   | Runs **when `var1` or `var2` change**     |

---

## Real-World Use Cases

### 1. Fetching Data on Component Mount

```jsx
import React, { useEffect, useState } from 'react';
import axios from 'axios';

function UserProfile() {
  const [user, setUser] = useState(null);

  useEffect(() => {
    axios.get('https://jsonplaceholder.typicode.com/users/1')
      .then(response => setUser(response.data))
      .catch(error => console.error('Error fetching data', error));
  }, []);

  if (!user) return <p>Loading...</p>;

  return (
    <div>
      <h2>{user.name}</h2>
      <p>{user.email}</p>
    </div>
  );
}
```

---

### 2. Updating Document Title Dynamically

```jsx
import React, { useState, useEffect } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

---

### 3. Setting and Clearing Timers

```jsx
import React, { useEffect, useState } from 'react';

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setSeconds(prev => prev + 1);
    }, 1000);

    return () => clearInterval(interval);
  }, []);

  return <p>Timer: {seconds}s</p>;
}
```

---

### 4. Listening to Window Resize

```jsx
import React, { useEffect, useState } from 'react';

function WindowSizeTracker() {
  const [width, setWidth] = useState(window.innerWidth);

  useEffect(() => {
    const handleResize = () => setWidth(window.innerWidth);

    window.addEventListener('resize', handleResize);

    return () => {
      window.removeEventListener('resize', handleResize);
    };
  }, []);

  return <p>Window width: {width}px</p>;
}
```

---

## Cleanup in useEffect

```jsx
useEffect(() => {
  const subscription = someStream.subscribe(data => {
    // handle data
  });

  return () => {
    subscription.unsubscribe();
  };
}, []);
```

---

## Pro Tips

- Avoid using `async` directly in `useEffect` because the function you pass to useEffect must return either undefined or a cleanup function, not a Promise. Use an internal async function instead:

```jsx
useEffect(() => {
  const fetchData = async () => {
    const response = await axios.get('/api');
    // do something
  };
  fetchData();
}, []);
```

- You can have multiple `useEffect` calls in a component for separation of concerns.
- Omitting dependency array causes effect to run after every render — which may lead to infinite loops.

---

## Summary

| Feature            | useEffect Role                        |
| ------------------ | ------------------------------------- |
| Data fetching      | After mount                           |
| DOM manipulation   | After render                          |
| Cleanup            | Before unmount / on dependency change |
| Watching variables | Via dependency array                  |
