# 📘 JavaScript Spread (`...`) vs Rest (`...`) Operators

## 🔹 What is the `...` (Spread / Rest) Operator?

The `...` syntax is used for **two different things** in JavaScript:

| Name           | Purpose                               | Usage Context             |
|----------------|----------------------------------------|---------------------------|
| **Spread**     | Spreads elements of an array/object    | Function calls, literals  |
| **Rest**       | Collects multiple elements into one    | Function parameters, destructuring |

---

## 🔸 1. SPREAD OPERATOR (`...`) — Expands Values

### ✅ Use Case: **Copying / Merging Arrays**

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5];

const combined = [...arr1, ...arr2];
console.log(combined); // [1, 2, 3, 4, 5]
```

---

### ✅ Use Case: **Copying Objects**

```javascript
const user = { name: 'Ashish', age: 25 };
const updatedUser = { ...user, age: 26 };

console.log(updatedUser); // { name: 'Ashish', age: 26 }
```

---

### ✅ Use Case: **Passing Array to Function**

```javascript
const nums = [4, 7, 2];
console.log(Math.max(...nums)); // 7
```

---

## 🔸 2. REST OPERATOR (`...`) — Gathers Values

### ✅ Use Case: **Variable Function Parameters**

```javascript
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4)); // 10
```

---

### ✅ Use Case: **Destructuring Objects**

```javascript
const { name, ...rest } = {
  name: 'Ashish',
  age: 25,
  country: 'India'
};

console.log(name); // Ashish
console.log(rest); // { age: 25, country: 'India' }
```

---

### ✅ Use Case: **Destructuring Arrays**

```javascript
const [first, ...others] = [10, 20, 30, 40];

console.log(first);  // 10
console.log(others); // [20, 30, 40]
```

---

## 🔄 Difference Between Spread and Rest

| Feature         | Spread                                | Rest                                |
|-----------------|----------------------------------------|-------------------------------------|
| Purpose         | Expands values into individual items   | Collects values into one            |
| Usage           | Arrays, Objects, Function Calls        | Function parameters, Destructuring  |
| Output          | List of items                          | Single array/object                 |

---

## 🌍 Real-World Use Cases

### ✅ Spread in React Props

```javascript
const props = { id: 1, name: "Ashish" };
<MyComponent {...props} />
```

---

### ✅ Rest in Event Handlers

```javascript
function handleEvent(type, ...details) {
  console.log(type, details);
}

handleEvent("click", 10, 20, "extra");
// click [10, 20, "extra"]
```

---

### ✅ Merging Redux State (Spread)

```javascript
return {
  ...state,
  user: action.payload
};
```

---

## ✅ Summary

| Operator | Used For                           | Main Purpose                                  |
|----------|------------------------------------|------------------------------------------------|
| Spread   | Function calls, literals, copying  | Expands arrays/objects into individual parts  |
| Rest     | Function args, destructuring       | Gathers elements into an array or object      |