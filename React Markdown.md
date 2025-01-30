

**1. core-react-concepts.md**
```markdown
# Core Concepts of React.js

## 1. Components
The fundamental building block of React applications. Components can be functional (preferred) or class-based.

```jsx
const Greeting = ({ name }) => {
  return <h1>Hello, {name}!</h1>;
};
```

## 2. JSX
- Syntax extension for JavaScript that looks like HTML
- Allows you to write HTML-like code in JavaScript
- Gets transformed into regular JavaScript during build

## 3. Props
Props are used to pass data from parent to child components.

```jsx
// Parent component
const Parent = () => {
  return <Child name="John" age={25} />;
};

// Child component
const Child = (props) => {
  return (
    <div>
      <p>Name: {props.name}</p>
      <p>Age: {props.age}</p>
    </div>
  );
};
```

## 4. State
Internal data storage for components using useState hook.

```jsx
const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};
```

## 5. Hooks
Common hooks include:
- useState: For managing state
- useEffect: For side effects and lifecycle events
- useContext: For consuming context
- useRef: For maintaining mutable references

## 6. Virtual DOM
- React's way of optimizing rendering
- Creates a lightweight copy of the actual DOM
- Efficiently updates only what needs to change

## 7. Component Lifecycle
- Mounting: Component is created and inserted into DOM
- Updating: Component is re-rendered due to state/prop changes
- Unmounting: Component is removed from DOM

## 8. Event Handling
```jsx
const Button = () => {
  const handleClick = (event) => {
    console.log("Button clicked!", event);
  };

  return <button onClick={handleClick}>Click me</button>;
};
```

## 9. Conditional Rendering
```jsx
const ConditionalComponent = ({ isLoggedIn }) => {
  return (
    <div>{isLoggedIn ? <UserDashboard /> : <LoginPrompt />}</div>
  );
};
```

## 10. Lists and Keys
```jsx
const List = ({ items }) => {
  return (
    <ul>
      {items.map((item) => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
};
```

## Learning Path Suggestion
1. Start with JSX and components
2. Move on to props and state management
3. Learn about hooks (especially useState and useEffect)
4. Study component lifecycle and effects
5. Practice with events and forms
6. Learn about context and more advanced state management
7. Study performance optimization and best practices

## Additional Important Topics
- React Router for navigation
- State management solutions (Redux, Context API)
- Component composition patterns
- Error boundaries
- Performance optimization techniques
- Testing React applications
```

**2. advanced-react-concepts.md**
```markdown
# Advanced Concepts of React.js

## 1. Advanced Hooks
### Custom Hooks
```jsx
const useCustomHook = (initialValue) => {
  const [value, setValue] = useState(initialValue);
  
  useEffect(() => {
    // Custom logic
  }, [value]);
  
  return [value, setValue];
};
```

### Performance Hooks
```jsx
// useMemo
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);

// useCallback
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]);
```

## 2. Higher-Order Components (HOC)
```jsx
const withAuth = (WrappedComponent) => {
  return function WithAuthComponent(props) {
    const isAuthenticated = checkAuth();
    return isAuthenticated ? (
      <WrappedComponent {...props} />
    ) : (
      <Navigate to="/login" />
    );
  };
};
```

## 3. Render Props Pattern
```jsx
const MouseTracker = ({ render }) => {
  const [position, setPosition] = useState({ x: 0, y: 0 });

  const handleMouseMove = (event) => {
    setPosition({
      x: event.clientX,
      y: event.clientY
    });
  };

  return (
    <div onMouseMove={handleMouseMove}>
      {render(position)}
    </div>
  );
};
```

## 4. Context API
```jsx
const ThemeContext = createContext();

const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState("light");

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};
```

## 5. Error Boundaries
```jsx
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    logErrorToService(error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    return this.props.children;
  }
}
```

## 6. Portals
```jsx
const Modal = ({ children }) => {
  return ReactDOM.createPortal(
    children,
    document.getElementById("modal-root")
  );
};
```

## 7. Performance Optimization
### React.memo
```jsx
const MemoizedComponent = React.memo(({ prop1, prop2 }) => {
  return (
    <div>
      <h1>{prop1}</h1>
      <p>{prop2}</p>
    </div>
  );
});
```

## 8. Refs and ForwardRef
```jsx
const FancyButton = React.forwardRef((props, ref) => (
  <button ref={ref} className="fancy-button">
    {props.children}
  </button>
));
```

## 9. Suspense and Lazy Loading
```jsx
const LazyComponent = React.lazy(() => import('./LazyComponent'));

function App() {
  return (
    <Suspense fallback={<Loading />}>
      <LazyComponent />
    </Suspense>
  );
}
```

## 10. Custom Hooks for Reusable Logic
```jsx
const useLocalStorage = (key, initialValue) => {
  const [storedValue, setStoredValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      return initialValue;
    }
  });

  return [storedValue, setStoredValue];
};
```

## Additional Advanced Topics
- Server-Side Rendering (SSR)
- Advanced State Management Patterns
- Component Composition Patterns
- Advanced Testing Techniques
- Performance Optimization Strategies
- Advanced Routing Concepts

## Learning Recommendations
1. Master one concept at a time
2. Build small projects implementing each concept
3. Combine multiple concepts in larger applications
4. Study real-world applications
5. Practice optimization techniques
6. Learn testing methodologies
7. Understand when to use each pattern
```

These markdown files provide a structured way to learn and reference both core and advanced React concepts. You can save them with `.md` extension and use them as documentation or learning materials.
