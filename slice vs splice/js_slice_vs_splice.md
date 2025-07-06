# 📘 JavaScript `slice()` vs `splice()` Explained

## 🔹 Overview Table

| Feature         | `slice()`                            | `splice()`                             |
|-----------------|----------------------------------------|-----------------------------------------|
| Purpose         | Extracts a section of an array         | Adds/removes/replaces elements in array |
| Returns         | A **new array**                        | The **removed elements** (as array)     |
| Modifies Array? | ❌ No (non-destructive)                | ✅ Yes (destructive)                    |
| Original Array  | Remains unchanged                      | Gets modified                           |

---

## 🔸 `slice()` – Non-Destructive Array Extractor

### 🔹 Syntax

```javascript
array.slice(start, end)
```

- `start` (required): Index to start extraction (inclusive).
- `end` (optional): Index to stop before (exclusive).
- Returns a **new array**.

### 🔹 Example

```javascript
const fruits = ["apple", "banana", "cherry", "date", "fig"];

const sliced = fruits.slice(1, 4);

console.log(sliced);       // [ 'banana', 'cherry', 'date' ]
console.log(fruits);       // [ 'apple', 'banana', 'cherry', 'date', 'fig' ]
```

✅ Original array stays the same.

---

## 🔸 `splice()` – Destructive Array Modifier

### 🔹 Syntax

```javascript
array.splice(start, deleteCount, item1, item2, ...)
```

- `start`: Index at which to start modifying the array.
- `deleteCount`: Number of elements to remove.
- `item1, item2, ...`: Items to add (optional).
- Returns the **deleted items**.

---

### 🔹 Example 1: Remove elements

```javascript
const fruits = ["apple", "banana", "cherry", "date", "fig"];

const removed = fruits.splice(2, 2); // remove 2 items starting at index 2

console.log(removed);     // [ 'cherry', 'date' ]
console.log(fruits);      // [ 'apple', 'banana', 'fig' ]
```

---

### 🔹 Example 2: Add elements

```javascript
const fruits = ["apple", "banana", "fig"];

fruits.splice(2, 0, "cherry", "date"); // add without deleting

console.log(fruits); // [ 'apple', 'banana', 'cherry', 'date', 'fig' ]
```

---

### 🔹 Example 3: Replace elements

```javascript
const fruits = ["apple", "banana", "cherry", "date"];

fruits.splice(1, 2, "mango", "kiwi");

console.log(fruits); // [ 'apple', 'mango', 'kiwi', 'date' ]
```

---

## 🔸 Use Case Comparison

| Task                            | Use `slice()` | Use `splice()` |
|----------------------------------|---------------|----------------|
| Copy a portion of an array       | ✅ Yes         | ❌ No           |
| Remove elements from array       | ❌ No          | ✅ Yes          |
| Add/replace elements in array    | ❌ No          | ✅ Yes          |
| Keep original array unchanged    | ✅ Yes         | ❌ No           |

---

## ✅ Summary

- `slice()` = **non-destructive** → returns a subarray without changing the original.
- `splice()` = **destructive** → directly modifies the array by removing/replacing/adding elements.