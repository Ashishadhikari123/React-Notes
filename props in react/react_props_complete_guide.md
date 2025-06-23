
# 📦 React Props – Complete Guide

In React, **props** (short for **properties**) are a fundamental concept for **passing data** from one component to another, typically from **parent to child**.

---

## ✅ 1. What Are Props?

- Props are **read-only objects** that hold values passed to components.
- They allow components to be **dynamic and reusable**.

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

```jsx
<Welcome name="Ashish" />
```

> Output: `Hello, Ashish`

---

## ✅ 2. Passing Multiple Props

```jsx
function Student(props) {
  return (
    <div>
      <p>Name: {props.name}</p>
      <p>Age: {props.age}</p>
    </div>
  );
}
```

```jsx
<Student name="Keshav" age={21} />
```

---

## ✅ 3. Destructuring Props

You can simplify access to props by destructuring.

### Traditional way:
```jsx
function Info(props) {
  return <p>{props.name}</p>;
}
```

### Destructured:
```jsx
function Info({ name }) {
  return <p>{name}</p>;
}
```

---

## ✅ 4. Props Are Read-Only

Props **cannot be modified** inside a component.

```jsx
function Example(props) {
  props.name = "New Name"; // ❌ This will throw an error
}
```

---

## ✅ 5. Default Props

You can set default values for props using `defaultProps`.

```jsx
function Message({ text }) {
  return <p>{text}</p>;
}

Message.defaultProps = {
  text: "Default Message"
};
```

```jsx
<Message /> // Output: Default Message
```

---

## ✅ 6. PropTypes (Type Checking)

Helps you define the **expected type** of props (works in development mode).

```jsx
import PropTypes from 'prop-types';

function Profile({ name, age }) {
  return <div>{name} - {age}</div>;
}

Profile.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number
};
```

---

## ✅ 7. Passing Functions as Props (Callback Props)

You can pass functions to handle events or child-to-parent communication.

```jsx
function Child({ onGreet }) {
  return <button onClick={onGreet}>Greet</button>;
}

function Parent() {
  const greet = () => alert("Hello from child");
  return <Child onGreet={greet} />;
}
```

---

## ✅ 8. Conditional Rendering with Props

```jsx
function Status({ isLoggedIn }) {
  return <p>{isLoggedIn ? "Welcome back!" : "Please log in."}</p>;
}
```

```jsx
<Status isLoggedIn={true} />
```

---

## ✅ 9. Spreading Props

Useful for passing all props at once.

```jsx
const user = { name: "Ashish", age: 25 };

function UserProfile(props) {
  return <div>{props.name} - {props.age}</div>;
}

<UserProfile {...user} />
```

---

## ✅ 10. Props in Class Components

```jsx
class Greeting extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

```jsx
<Greeting name="Ashish" />
```

---

## ✅ Summary

| Feature                    | Description                                      |
|----------------------------|--------------------------------------------------|
| Props                     | Pass data from parent to child                   |
| Read-only                 | Cannot be changed inside the child component     |
| Destructuring             | Simplifies code                                  |
| Default Props             | Fallback values                                  |
| PropTypes                 | Type safety in development                       |
| Function Props            | Enables parent-child communication               |
| Conditional Rendering     | Dynamic content display                          |
| Spread Operator           | Pass props efficiently                          |
| Class Component Props     | Accessed via `this.props`                        |

---

Props are essential to build **flexible and dynamic** React applications.
