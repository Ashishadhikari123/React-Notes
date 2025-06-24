
# React.js Interview Questions: Props

### **1. Basic Concepts**  
1. **What are props in React?**  
   - Props (properties) are read-only data passed from a parent to a child component. They make components reusable and dynamic.  
   - Example:  
     ```jsx
     function Parent() {
       return <Child message="Hello" />;
     }
     function Child(props) {
       return <p>{props.message}</p>; // Output: "Hello"
     }
     ```  

2. **How do you pass props from a parent to a child component?**  
   - By adding attributes to the child component in JSX (e.g., `<Child color="blue" />`).  

3. **Can props be modified inside the child component?**  
   - No, props are immutable (read-only).  

4. **What’s the difference between props and state?**  
   - **Props** are external (passed to a component), while **state** is internal (managed within a component).  

5. **How do you access props in class vs. functional components?**  
   - Functional: Directly via `props` or destructuring (`{ propName }`).  
   - Class: Via `this.props`.  

---

### **2. PropTypes & Defaults**  
6. **How do you define the type of props a component should receive?**  
   - Using `PropTypes` (or TypeScript).  
   - Example:  
     ```jsx
     import PropTypes from 'prop-types';
     Component.propTypes = {
       name: PropTypes.string.isRequired
     };
     ```  

7. **What is `PropTypes` and why is it useful?**  
   - A type-checking library to catch bugs early by validating prop types.  

8. **How do you set default values for props?**  
   - Using `defaultProps`:  
     ```jsx
     Component.defaultProps = { color: 'red' };
     ```  

9. **What happens if a required prop is not passed?**  
   - React logs a warning in development mode.  

---

### **3. Dynamic Props & Children**  
10. **How do you pass dynamic props?**  
    - Example:  
      ```jsx
      <UserProfile {...userData} /> // Spread operator
      ```  

11. **What is `props.children`?**  
    - A special prop that contains content between a component’s opening/closing tags.  
    - Example:  
      ```jsx
      <Modal> <h1>Title</h1> </Modal> // Accessed via props.children
      ```  

12. **Can you pass a component as a prop?**  
    - Yes (e.g., `<Layout header={<Header />}`).  

---

### **4. Advanced Props Handling**  
13. **How do you spread props (`{...props}`)?**  
    - Useful for forwarding props to nested components.  

14. **What is prop drilling? How to avoid it?**  
    - Passing props through multiple layers. Solutions: Context API or state management (Redux).  

15. **How to pass a function as a prop?**  
    - Example:  
      ```jsx
      <Button onClick={() => alert('Clicked!')} />
      ```  

16. **What are render props?**  
    - A pattern where a prop is a function that returns JSX (e.g., `<DataProvider render={(data) => <p>{data}</p>} />`).  

---

### **5. Performance & Best Practices**  
17. **How do props affect re-rendering?**  
    - Changing props triggers a re-render of the child component.  

18. **How to pass many props cleanly?**  
    - Group them into an object and use spread: `<Component {...props} />`.  

19. **How to memoize props?**  
    - Use `React.memo()` or `useMemo` to prevent unnecessary re-renders.  

20. **When to avoid inline functions in props?**  
    - When they cause unnecessary re-renders (use `useCallback` instead).  
