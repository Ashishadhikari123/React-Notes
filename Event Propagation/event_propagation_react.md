
# 🧠 Event Propagation and Bubbling in React (Simplified)

## 🎯 What is Event Propagation?

**Event propagation** is how events like `onClick` move through the DOM tree when you interact with elements.

React follows this process automatically.

---

## 🔁 Two Types of Event Propagation

1. **Event Bubbling** (Default in React)
   - Event starts at the clicked element (target)
   - Then bubbles **upward** to its parent elements

2. **Event Capturing** (Less common)
   - Event starts from the **top-level parent**
   - Then moves **down** to the target

---

## 🧪 Simple Example – Event Bubbling in React

```jsx
function App() {
  const handleParentClick = () => {
    console.log("Parent clicked");
  };

  const handleChildClick = () => {
    console.log("Child clicked");
  };

  return (
    <div onClick={handleParentClick}>
      <button onClick={handleChildClick}>Click Me</button>
    </div>
  );
}
```

### 🖱️ Output when you click the button:
```
Child clicked
Parent clicked
```

This is because the event bubbles **from the button to the parent div**.

---

## 🛑 How to Stop Bubbling

You can **prevent the parent from reacting** to a child’s event using `event.stopPropagation()`:

```jsx
function App() {
  const handleParentClick = () => {
    console.log("Parent clicked");
  };

  const handleChildClick = (e) => {
    e.stopPropagation(); // stops bubbling
    console.log("Child clicked");
  };

  return (
    <div onClick={handleParentClick}>
      <button onClick={handleChildClick}>Click Me</button>
    </div>
  );
}
```

### 🖱️ Output now:
```
Child clicked
```

✅ The parent click doesn't run anymore!

---

## 📌 Summary Table

| Term                    | Meaning                                                  |
|-------------------------|----------------------------------------------------------|
| **Event Bubbling**      | Event goes from **child to parent**                      |
| **event.stopPropagation()** | Stops the event from reaching parent handler         |
| **Use case**            | Prevent unwanted parent reactions (e.g. closing modals)  |
