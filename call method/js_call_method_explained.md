# 📘 JavaScript `call()` Method Explained

## 🔹 What is `call()` in JavaScript?

The **`call()`** method is a built-in JavaScript method that belongs to **functions**. It allows you to:

> **Call a function with a specific `this` value and individual arguments.**

---

## 🔹 Syntax

```javascript
functionName.call(thisArg, arg1, arg2, ..., argN)
```

- `functionName`: The function you want to call.
- `thisArg`: The object you want to use as `this` inside the function.
- `arg1, arg2, ...`: Arguments passed to the function.

---

## 🔹 Why is `call()` Used?

It is mainly used to:

1. **Set the value of `this` explicitly**.
2. **Borrow methods from other objects**.
3. **Invoke functions with arguments**.

---

## 🔹 Example 1: Setting `this` Manually

```javascript
function greet() {
  console.log(\`Hello, my name is \${this.name}\`);
}

const person = {
  name: 'Ashish'
};

greet.call(person); // Hello, my name is Ashish
```

✅ Here, `call()` tells JavaScript to treat `person` as `this` inside `greet()`.

---

## 🔹 Example 2: Function Borrowing

```javascript
const person1 = {
  name: "Rahul",
  greet: function(city) {
    console.log(\`\${this.name} lives in \${city}\`);
  }
};

const person2 = {
  name: "Anjali"
};

person1.greet.call(person2, "Delhi"); // Anjali lives in Delhi
```

✅ `person2` doesn't have a `greet` method, but we "borrowed" it using `call()`.

---

## 🔹 Difference between `call()`, `apply()`, and `bind()`

| Method   | Invokes Immediately | Arguments Format            | Purpose                        |
|----------|---------------------|-----------------------------|--------------------------------|
| `call()` | ✅ Yes              | List of arguments           | Set `this` + pass arguments   |
| `apply()`| ✅ Yes              | Array of arguments          | Set `this` + pass args as array|
| `bind()` | ❌ No               | List of arguments           | Returns a new function with `this` bound |

---

## 🔹 Real-World Scenario

```javascript
function updateStyle(color) {
  this.style.backgroundColor = color;
}

const button = document.getElementById("myButton");

// Call with `this` set to button
updateStyle.call(button, "blue");
```

✅ You use `call()` to directly manipulate the style of an element by assigning `this` context dynamically.

---

## ✅ Summary

- `call()` is a method of functions.
- It allows you to invoke a function while specifying the `this` context.
- Helps with method borrowing and dynamic function calls.