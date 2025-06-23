
# ✅ Conditional Rendering in React

React provides multiple ways to conditionally render components or elements based on logic or state.

---

## 1. Using `if` Statements (Outside JSX)
Use simple `if` statements before the `return`.

```jsx
function Greeting({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  }
  return <h1>Please sign in.</h1>;
}
```

---

## 2. Using `if-else` with Variables
Assign JSX to a variable based on condition.

```jsx
function Greeting({ isAdmin }) {
  let message;
  if (isAdmin) {
    message = <h1>Welcome Admin</h1>;
  } else {
    message = <h1>Welcome User</h1>;
  }
  return message;
}
```

---

## 3. Using Ternary Operator (Inline)
Great for short, simple conditions.

```jsx
function Greeting({ isLoggedIn }) {
  return (
    <div>
      {isLoggedIn ? <p>Welcome!</p> : <p>Please log in.</p>}
    </div>
  );
}
```

---

## 4. Using Logical `&&` Operator
Short-circuits rendering if the condition is false.

```jsx
function Notification({ hasUnreadMessages }) {
  return (
    <div>
      {hasUnreadMessages && <p>You have new messages.</p>}
    </div>
  );
}
```

---

## 5. Using Switch Statement
Good for multiple condition branches.

```jsx
function Status({ status }) {
  switch (status) {
    case "loading":
      return <p>Loading...</p>;
    case "success":
      return <p>Data loaded!</p>;
    case "error":
      return <p>Failed to load.</p>;
    default:
      return null;
  }
}
```

---

## 6. Conditional CSS Class
Toggle visibility or styles based on condition.

```jsx
function Box({ isVisible }) {
  return (
    <div className={isVisible ? "box show" : "box hide"}>
      Content
    </div>
  );
}
```

---

## 7. IIFE (Immediately Invoked Function Expression) in JSX
For complex logic within JSX.

```jsx
function RenderLogic({ type }) {
  return (
    <div>
      {(() => {
        if (type === "admin") return <p>Admin Panel</p>;
        if (type === "user") return <p>User Dashboard</p>;
        return <p>Guest Access</p>;
      })()}
    </div>
  );
}
```

---

## 🚀 Summary Table

| Method                  | Best For                                  |
|-------------------------|-------------------------------------------|
| `if`/`else` statements  | Simple mutually exclusive conditions      |
| Ternary operator        | Inline simple choices                     |
| Logical `&&`            | Show component only when condition is true|
| `switch`                | Multiple condition branches               |
| IIFE                    | Complex conditions inside JSX             |
| ClassName toggle        | Conditional styling/visibility            |
