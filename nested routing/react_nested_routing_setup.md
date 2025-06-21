# React Routing with createBrowserRouter and Nested Routes

## 🧰 Step 1: Project Setup

### ✅ Create a React project

```bash
npx create-react-app react-router-demo
cd react-router-demo
```

### ✅ Install React Router

```bash
npm install react-router-dom
```

---

## 🗂️ Step 2: Folder Structure

```
src/
├── components/
│   ├── Layout.jsx
│   ├── Home.jsx
│   ├── About.jsx
│   ├── Contact.jsx
│   └── NotFound.jsx
├── main.jsx
└── App.jsx
```

---

## 🧱 Step 3: Create Page Components

### Home.jsx

```jsx
function Home() {
  return <h2>Welcome to Home Page</h2>;
}
export default Home;
```

### About.jsx

```jsx
function About() {
  return <h2>About Us</h2>;
}
export default About;
```

### Contact.jsx

```jsx
function Contact() {
  return <h2>Contact Page</h2>;
}
export default Contact;
```

### NotFound.jsx

```jsx
function NotFound() {
  return <h2>404 - Page Not Found</h2>;
}
export default NotFound;
```

---

## 🧩 Step 4: Create Layout Component

### Layout.jsx

```jsx
import { Link, Outlet } from 'react-router-dom';

function Layout() {
  return (
    <div>
      <h1>My Website</h1>
      <nav style={{ marginBottom: '20px' }}>
        <Link to="/">Home</Link> |{" "}
        <Link to="/about">About</Link> |{" "}
        <Link to="/contact">Contact</Link>
      </nav>
      <hr />
      <Outlet />
    </div>
  );
}

export default Layout;
```

---

## 🌐 Step 5: Configure Routes with createBrowserRouter

### main.jsx

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import { createBrowserRouter, RouterProvider } from 'react-router-dom';

import Layout from './components/Layout';
import Home from './components/Home';
import About from './components/About';
import Contact from './components/Contact';
import NotFound from './components/NotFound';

const router = createBrowserRouter([
  {
    path: '/',
    element: <Layout />,
    children: [
      { index: true, element: <Home /> },
      { path: 'about', element: <About /> },
      { path: 'contact', element: <Contact /> },
    ]
  },
  { path: '*', element: <NotFound /> }
]);

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <RouterProvider router={router} />
  </React.StrictMode>
);
```

---

## 🚦 Output Behavior

| Route         | Layout Renders | Component         |
|---------------|----------------|-------------------|
| `/`           | ✅              | Home              |
| `/about`      | ✅              | About             |
| `/contact`    | ✅              | Contact           |
| `/anything`   | ❌              | NotFound          |

---

## 🧠 Key Concepts

| Concept             | Purpose                                  |
|---------------------|------------------------------------------|
| `createBrowserRouter` | Defines route objects                   |
| `RouterProvider`    | Injects the router into the app          |
| `Layout`            | Common UI layout wrapper                 |
| `Outlet`            | Placeholder for nested route content     |
| `Link`              | Navigate without full reload             |
| `index: true`       | Default child route                      |

---

## ✅ Optional Extensions

- Protect routes using auth logic
- Use `loader`/`action` for data fetching
- Implement code splitting with `React.lazy`
