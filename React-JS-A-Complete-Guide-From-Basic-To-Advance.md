# React JS : A Complete Guide From Basic To Advance

![React JS](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*erKx_vOF0PtVR5LTmbHY0w.png)

### INTRODUCTION -

React JS is a free and open-source front-end JavaScript library used for building user interfaces with a component based architecture. It was created by Jordan Walke at Facebook in 2011.

It is used to create Single Page Application (SPAs). It uses Virtual DOM for efficient and optimized DOM Manipulation and faster performance.

---

### COMPONENTS -

A Component is re-usable piece of code that serves as a building block of the user interface.

Components are of two types :-

- Class Components : use ES6 classes, extends React.Component, manage their own state using this.state and this.setState(), use in-built lifecycle methods (componentDidMount, componentDidUpdate, componentWillUnmount) and render() method to return JSX.
- Functional Components : introduced in React 16.8, use Hooks to manage state, side effects and lifecycle methods, pass data between components through props and return JSX directly without render method.

---

### JSX -

JSX stands for JavaScript XML. It is a syntax extension that allows us to write HTML like code directly into a JavaScript file. But browsers cannot directly understand JSX. So, it gets compiled into regular JavaScript code through a compiler called Babel. Babel uses a JavaScript function called React.createElement(), which converts the JSX code into a JavaScript object that represents the UI structure. React then uses these objects to create the virtual DOM, which allows it to efficiently update and render the UI.

---

### VIRTUAL DOM -

Virtual DOM is light weight (in memory) copy of the real DOM. It is used to optimize the process of updating the browser’s UI.

- When the page first loads, React creates a Virtual DOM tree that mirrors the actual DOM structure (HTML elements).
- Whenever the state or props of any components changes, instead of directly manipulating the real DOM, it creates a new Virtual DOM tree with that updated component.
- React then compares this new Virtual DOM with the previous one using a Diffing algorithm.
- Then, it finally update only those components in the real DOM through a process called Reconciliation.

> ***Diffing** is the algorithm that React uses to compare the current Virtual DOM with the previous one to detect changes (such as addition, removal, updation of DOM elements or components).*

> ***Reconciliation** is the process of updating the real DOM based on the differences found in the Virtual DOM through the Diffing algorithm.*

---

### REACT FIBRE -

React Fibre is the re-implementation of React’s core algorithm (Diffing), which is responsible for rendering and updating the UI. It was introduced in React 16.

It is asynchronous and splits the rendering work into chunks, called fibres. This enables React to pause, work on other tasks (like responding to user input), and then continue rendering.

It also prioritize the updates. Some updates might be urgent (user interactions like clicks and typing), while others can be lower priority (less critical state changes).

---

### CONTROLLED AND UN-CONTROLLED COMPONENTS -

- Controlled Components : Controlled Components are the input elements whose values are managed through React State, using hooks like useState() (in functional components) and this.state (in class components). These components update their value through event handlers and React state, making the state the single source of truth.
- Un-Controlled Components : Un-Controlled Components are the input elements that manage their own State internally (within the DOM). React access and updates their value using hooks like useRef (in functional components) and React.createRef() (in class components). React does not manage their state. Instead, it reads the value directly from the DOM when needed (like form submission) without triggering re-renders on every input change.

---

### HIGH ORDER COMPONENTS -

High Order Components are components (functions) that take a Component (function) as an argument and returns a new Component (function) with additional props, functionalities or behaviour.

Essentially, it’s a way to wrap a component with extra functionality without modifying the original component directly.

---

### PROPS AND STATE -

- Props : Props (short for Properties) are objects that contain data which is passed from a Parent component to a Child component. They are immutable, meaning the child component receiving Props cannot modify them.
- State : State are objects that contain the internal data of a component, which can be changed over time by the component itself (user interaction, lifecycle events, etc.). When State changes, the component re-renders to reflect the updated data. State is local and cannot be accessed directly by child components unless passed down as props.

Key Differences (Summary) :-

- Ownership : Props are owned by the parent; State is owned by the component itself.
- Mutability : Props are immutable (read-only); State is mutable (can be updated).
- Data Flow : Props are for external communication (Parent → Child); State is for internal management.

---

### FRAGMENTS -

Fragments are a feature that allows us to group multiple elements without adding any extra node to the DOM, i.e., no unnecessary wrapper elements like < div >. So, instead of wrapping elements in < div >…< /div >, you can wrap them with empty tags (<>…</>) or React.Fragment Component (< React.Fragment >…</ React.Fragment >).

---

### KEYS -

Keys are special props that acts as unique identifiers which are assigned to elements in a list to help React identify which items have been added, changed or removed during re-renders.

Keys are important to optimize the process of re-rendering and prevents unnecessary re-renders. Without Keys, React would re-render the entire list whenever the data changes, even if only one item was added, updated or removed.

> *Keys must be unique and stable, and that’s why, you shouldn’t use **Index / Indices** as Keys. It is not recommended because when the list is changed dynamically (items are added, reordered or removed), it will change the value of Keys. This will lead to performance issues and the element may loose their internal State.*

---

### REACT HOOKS -

React Hooks are special functions introduced in React 16.8 that allows us to use state, side effects, context, and other React features directly in functional components (without writing class components).

Rules Of Hooks :-

- Hooks can only be called at the top level of React function components, not inside loops, conditionals or normal JavaScript functions.
- Hooks must always start with the word “use”.

Core React Hooks :-

- useState() : used for State management.
- useEffect() : used for side effects (API calls, subscriptions, etc.).
- useContext() : used to access React Context (global state) without prop drilling.
- useReducer() : used as an alternative of useState(), for managing complex state logic.
- useRef() : used for accessing mutable values from un-controlled components / inputs without causing re-renders.
- useCallback() : used for memoizing a function so that it is not re-created on every re-render (unless its dependencies change).
- useMemo() : used for memoizing a computed value so that it is not re-calculated on every re-render (unless its dependencies change).

---

### useState() AND useEffect() HOOK -

The useState() and useEffect() are the most fundamental hooks in React for managing state and side effects in functional components.

- useState() : useState() acts as an internal memory and allows components to maintain local, mutable state. Any time this data changes, React will automatically re-render the component to reflect the new value. It takes one argument — initial state value, and returns an array with two elements — the current state value and a setter function to update this state.

> *It is important to remember that **React update state in Batches**. If you need to use the previous state value to calculate the new state, you can pass a function to setState().*

> *setCount((prevCount) => prevCount + 1);*

- useEffect() : useEffect() is used to perform side effects (API calls, subscriptions, DOM updates, timers, etc.) after the component has rendered. It is a replacement for lifecycle methods like componentDidMount(), componentDidUpdate() and compoentWillUnmount() in class components. It takes two arguments — a function (effect) and a dependency array (optional). The function will only run if the dependencies change, i.e., the dependencies control the effect.

> *If there is no **dependency array**, the function will run every time the component re-renders.*

> *If the dependency array is empty, the function will run only once after the initial render.*

> *If there are dependencies (values in the array), the function will run once after the initial render, and then, every time the dependencies change.*

> *The **Cleanup Function** is an optional function that you can return inside your effect function to handle cleanup tasks when the component un-mounts or before the effect runs again.*

> *It is used to prevent memory leaks, cancel subscriptions or timers, remove event listeners and manual DOM manipulation.*

> ***useEffect() and useLayoutEffect()** are hooks in React that allow you to perform side effects in functional components. However, there is a key difference in timing and behavior between the two, which can impact how your application behaves and performs.*

> *useEffect() run after the component is rendered and the DOM is painted. It run asynchronously and does not block the browser’s painting process. It should be used for non-DOM related / non-visual logic like data fetching, event listeners, logging, etc.*

> *useLayoutEffect() run after the component is rendered but before the DOM is painted. It run synchronously and blocks browser’s painting process until the function (effect) is executed. It should be used for handling DOM mutations before the user sees it like reading dimensions, positioning, animations, etc.*

---

### LIFTING STATE UP -

Lifting State Up refers to the practice of moving state from child components to their nearest common parent / ancestor component, so that multiple components can share and synchronize that state.

Sometimes two or more child components need to interact with the same data. To avoid duplication of state or inconsistent updates, it’s often better to “lift” the state to their common parent.

When you lift state up, the parent component holds the state and passes it down to the child components via props. The child components can interact with it through Callback Functions.

The common ancestor becomes the single source of truth for the shared data.

---

### CUSTOM HOOK -

A Custom Hook is a reusable JavaScript function whose name begins with “use” and that uses built-in React hooks (like useState, useEffect, useContext, etc.) within its body.

React’s built-in hooks ( useState(), useEffect(), useContext(), etc.) allow you to manage state and side effects in functional components, but sometimes the logic that handles this state or side effect is complex and needs to be shared across multiple components (data fetching, timers, form handling, etc.). Rather than repeating the same code in multiple places, you can encapsulate this logic inside a custom hook, making it easier to maintain and reuse.

Rules For Creating A Custom Hook :-

- Name Convention : It must start with the word “use”. This is how React identifies it as a Hook and applies all the rules of Hooks.
- Calls Hooks : It typically calls one or more built-in React Hooks to manage state or side effects.
- Returns Data : It usually returns an array or an object containing values and/or functions needed by the components that use it.

Custom hooks do not render UI. They are only responsible for providing logic to the component.

---

### PERFORMANCE OPTIMIZATION -

Optimizing a React App involves reducing load time, minimizing re-renders, lowering memory usage and improving runtime performance.

- Memoization : helps in preventing un-necessary component re-rendering, un-necessary re-calculation and memorises calculated data.
- Code Splitting & Lazy Loading : breaks javascript bundles into smaller chunks and loads them when required.
- Debouncing & Throttling : minimize API calls and network requests.
- Pagination, Infinite Scrolling & Virtualization : helps in loading large list of data efficiently.
- Server Side Rendering (SSR) & Static Site Generation (SSG) : renders pages on server for fast loading and improves SEO.
- Context API : helps in efficient state management at global level, preventing prop drilling.

> *Use Context API with Memoization for better performance.*

---

### MEMOIZATION -

Memoization is an optimization technique that caches the result of expensive function calls and returns the cached result when the same inputs occur again. This avoids unnecessary re-calculations and re-renders, thus improving performance.

Memoization Techniques In React :-

- React.memo : A high order component that memoizes a functional component. It prevents the component from re-rendering unless its props have changed.
- useMemo() : A hook that memoizes the calculated value / result inside a functional component. It takes a function and a dependency array and re-calculate the value only if the dependencies change and helps preventing un-necessary re-calculations on every render.
- useCallback() : A hook that memoizes the function (reference) and returns the same function (reference) between renders unless it’s dependencies change.

External Libraries :-

- Lodash
- React Memoize

---

### CODE SPLITTING AND LAZY LOADING -

- Code Splitting : Code Splitting is a performance optimization technique that lets you break your javascript bundle into smaller chunks that can be loaded on demand. Lazy Loading is a form of code splitting where only the needed parts are loaded dynamically. This is done with the help of bundlers like Webpack, which detect dynamic import() calls and create separate bundles for those modules.
- Lazy Loading : Lazy Loading uses code splitting to load components on demand where certain parts of your app (components, images, data, etc.) are loaded only when needed, instead of loading everything upfront. This helps reduce the initial load time and speeds up the application, making it more responsive, especially for larger apps.

Lazy Loading is implemented using two features provided by React :-

1. React.lazy() : A function that imports a lazy-loaded component.
2. Suspense : A component that wraps the lazy-loaded component and show a fallback UI until it loads.

---

### DEBOUNCING AND THROTTLING -

Debouncing and Throttling are rate-limiting techniques used to limit the rate at which a function is executed, especially when it is triggered frequently (user input events like typing, scrolling, or resizing). They are commonly used to improve performance, reduce unnecessary computations, and optimize user experience.

- Debouncing : Debouncing is a technique used to delay the execution of a function until after a certain period of inactivity. It is typically used when you want to wait until the user stops performing an action, such as typing, before executing the function. This means only the final event will trigger the function after the user stops interacting.
- Throttling : Throttling ensures that a function is executed at most once in a given period of time, regardless of how many times the event is triggered. The function operates at regular intervals, making throttling ideal for continuous events like scrolling or mouse movement, where you want the function to run at a fixed rate and not overload the browser.

---

### PAGINATION, INFINITE SCROLLING AND VIRTUALIZATION -

Pagination, Infinite Scrolling, and Virtualization are techniques used to handle large data sets (lists) efficiently in React applications by controlling how much data is rendered and when, improving web application performance.

- Pagination : Pagination is the traditional method of dividing the large set of data into a series of pages and loading one page at a time, showing a limited sub-set at a time. Users can navigate between these pages using controls like “Previous”, “Next” or specific “Page Numbers” to view different sub-sets of the data. Common Libraries — React Paginate, Material UI Pagination, etc.

- Infinite Scrolling : Infinite Scrolling is a technique where new data is loaded automatically as the user scrolls down the page, creating a continuous flow of content. It is often implemented using scroll event listeners or libraries detecting when the user nears the viewport bottom. Common Libraries — React Infinite Scroll Component, React Infinite Scroller, etc.

- Virtualization : Virtualization (also called Windowing) is a technique where only a small subset of items is rendered on the screen / user’s window / viewport at any given time, plus a small buffer before and after the visible area. As the user scrolls, the items that are out of view are un-mounted from the DOM, and new items are mounted to fit within the viewable area. Common Libraries — React Virtualized, React Window, etc.

Libraries For Combining Pagination, Infinite Scrolling & Virtualization :-

- React Query
- React Table

---

### ERROR BOUNDARIES -

Error Boundaries are React components (class based) that catch JavaScript errors anywhere in their child component tree, log those errors, and display a Fallback UI to show errors on page, instead of crashing the entire application.

They act like try-catch blocks for React components and protect the rest of your UI from being destroyed by a single component failure.

> *It is important to note that Error Boundaries **only catch** errors that happen during rendering, lifecycle methods and in constructors of the whole tree below them. They **do not catch** errors in event handlers, asynchronous code, server-side rendering and the error boundary itself. For that, you have to use traditional try-catch method.*

The main difference between **Error Boundaries and try-catch** is that try-catch cannot catch errors in the rendering process, lifecycle methods and mounting & un-mounting of components.

Error boundaries are created by defining lifecycle methods like static getDerivedStateFromError() — to render fallback UI and componentDidCatch() — to log the error.

To use these error boundary component, you can wrap the components that may throw error inside the < ErrorBoundary >…</ ErrorBoundary > component.

---

### PROP DRILLING -

Prop Drilling in React is the process of passing data (props) from a parent component down through multiple layers of intermediate components until it reaches a deeply nested child component that actually needs the data. The intermediate components do not use the data themselves but still have to pass it along, which can make the code harder to manage and less maintainable.

How To Avoid :-

1. React Context API : The Context API allows you to share data “globally” across the component tree without passing props at every level. Components that need that data can directly consume the context.
2. State Management Libraries : Use state management libraries like Redux, Zustand, Recoil, Jotai, MobX, etc.
3. Component Composition : Component Composition is a React design pattern where you combine smaller components to build more complex UIs, instead of passing props deeply down the component tree.
4. Custom Hooks : Custom Hooks help avoid prop drilling by encapsulating shared stateful logic and side effects in reusable functions that can be independently called by any component that needs the data or behavior, thus eliminating the need to pass props through many intermediary components.

---

### CONTEXT API -

Context API is a feature in React that allows you to share data across the component tree without passing props manually at every level, solving the problem of prop drilling.

How It Works :-

- Create A Context : Using React.createContext(), you create a Context object that contains two main components — a Provider and a Consumer.
- Provider : The < Context.Provider >…</ Context.Provider > component wraps the part of the component tree that need access to the shared data. It accepts a “value” prop that holds the data or state to be shared. Any component within the Provider’s boundary can access the shared data. When the value passed to the Provider changes, all the components consuming the shared data re-render.
- Consumer : Descendant components can access the Context value using useContext() Hook (functional components) or < Context.Consumer >…</ Context.Consumer > (class components).

---

### REDUX -

Redux is a State Management Library for JavaScript web applications. It provides a single source of truth by storing the entire application state in a single centralized store, making state predictable and easier to manage.

Redux Workflow :-

- Store : Store is a single object that stores the immutable State (globally) of the entire web application.
- Action : Action is a plain object with a “type” property which tells the reducer what changes or events has occurred, i.e., why the state needs to be changed. It also has a “payload” property (optional) which tells the reducer what data is needed to update the state.
- Reducer : Reducer is a pure function that takes an action and the current state as an argument and create a new state based on the action. It never mutates the existing state.
- Dispatch : Dispatch is the function that is used to send (dispatch) an action to the store and trigger the state update via reducer.

> *Redux Toolkit (RTK) is now the official, recommended way to write Redux logic.*

---

### HANDLING FORMS-

In React, handling Forms involves managing the form’s state and handling user input. The state acts as the “single source of truth” for the input’s value.

Controlled Components : In Controlled Components, form data is managed by React state using hooks like useState() (in functional components) and this.state (in class components). The onChange() event handler updates the state on each input change.

If you have multiple fields, you can either create individual states for each field or store them in an object.

- Use useState() to create a single state variable that holds an object. Each property in this object will correspond to an input field in your form, with its initial value.
- Ensure each input field has a unique “name” attribute that matches the corresponding property in your state object. This name attribute is crucial for dynamically updating the correct state property.
- Define a single function that will be attached to the onChange() event listener of all your input fields. This function will use object destructuring to extract the name and value from event.target .

Un-Controlled Components : In Un-Controlled Components, form data is not managed by React itself. Instead, form values are accessed using hooks like useRef() (in functional components) and React.createRef() (in class components), which directly reference DOM elements (like traditional HTML forms). It does not need React state or onChange() event handler.

Form Submission : To Submit a form, a function is attached to the onSubmit() event listener of the < Form > element. This function receives an event object, which allows us to call event.preventDefault() to stop the browser’s default form submission behavior, which would cause a full page reload. Finally, you can collect and process (perform actions like API calls) the form data from your component’s state (for controlled components) or using refs (for uncontrolled components).

Form Validation : Form Validation can be done at either Field Level Validation (validating each field’s value immediately when the user interacts with it) or at Form Level Validation (on form submission).

- Create a function for form validation. You can pass this function on events like onChange() or onBlur() of all input fields (field level validation) or onSubmit() of <Form> element (form level validation).
- Create a state that tracks Errors during the process. You can conditionally display that error messages under the input fields.
- You can use validation methods like built-in HTML validation attributes (required, type, minLength, etc.) or create a Regex (Regular Expression).

External Form Libraries : Using External Form Libraries significantly reduce the amount of boilerplate code, handle complex state and validation logic, and often improve performance.

Form Libraries :-

- React Hook Form
- Formik
- React Final Form

You can also use Schema Validation Libraries along with these form libraries. Their core purpose is to define rules (schemas) for data and validate that data at runtime.

Schema Validation Libraries :-

- Yup
- Zod
- Joi

---

### HANDLING NAVIGATION -

React is a Single Page Application (SPA) and doesn’t rely on the browser’s default page reloads for Navigation. Since React doesn’t include routing by default, we use external libraries (React Router DOM, TanStack Router, Wouter, etc.) that manage the transition between views or screens within an application.

React Router DOM is the industry practice for React (web) and React Navigation for React Native (app).

A. Common Navigation Setup :-

1. Defining Routes :-
- < BrowserRouter >…</ BrowserRouter > : a high-level component that wraps entire application routing.
- < Routes >…</ Routes > : a collection of < Route >…</ Route > elements.
- < Route >…</ Route > : a component used to define individual routes (“path” attribute) for individual components (“element” attribute).

2. Creating Links :-

- < Link >…</ Link > : acts as < a >…</ a > (but prevents page reload), has “to” attribute instead of “href”.
- < NavLink >…</ NavLink > : works same as < Link >, but has “active” class.

> *< NavLink > is often preferred over < Link > for main navigation as it automatically applies “**active**” class when the link’s “to” attribute matches the current URL, making it easy to style the active link.*

B. Programmatic Navigation :- Sometimes, you need to trigger navigation based on an event like a form submission, a successful API call or clicking a button that isn’t a link. For this, you use the useNavigate() hook.

> *Key Differences Between **useNavigate() and < Navigate />** :-*

> *Programming Style : useNavigate() is for imperative navigation (you tell it when to navigate), while < Navigate /> is for declarative navigation (you declare what the navigation should be).*

> *Context : useNavigate() is ideal for triggering navigation based on events (button clicks, form submissions, useEffect() hooks). < Navigate /> is well-suited for conditional rendering and redirects within the component’s JSX.*

> *Class Components : The < Navigate /> component can be used in class-based components, whereas hooks like useNavigate() are exclusively for functional components.*

C. Handling Dynamic Data & Rendering Components (URL Parameters) :-

To handle dynamic data, such as viewing details for a specific user or product, you use URL parameters.

- Use a colon “:” followed by the parameter name in the path.
- Inside the component, you use the useParams() hook to extract the values.
- Based on the parameter value, you can dynamically render different components or data.

D. Nested Routes :-

Nested Routes allow you to define routes within other routes, enabling component layouts to be composed in a hierarchical manner / multi-level navigation.

1. Defining Parent & Child Routes : Inside your < Routes > component, define a < Route > for the parent path, and nest child < Route > components inside it representing sub-paths. Use < Route index /> for default child when parent path matches exactly.
2. Use < Outlet /> in parent component where child route components should be displayed. It acts as a placeholder for rendering whichever child route matches the URL under /parent.

E. Protected Routes :-

Protected Routes are a crucial security mechanism that require the user to be authenticated (and optionally authorized) before they can access them. They help ensure that sensitive or private parts of your app are protected.

- Implementing protected routes involves creating a wrapper component that checks the user’s authorization before rendering the requested child component, which can be done based on state, context , token, etc.
- If the user is authorized, the protected route renders its child components (or an < Outlet /> for nested routes).
- If the user is not authorized, the component redirects the user to a login page or another public route using react router’s < Navigate /> component.

F. 404 Pages :-

A 404 Page is a special web page shown when a user tries to access a route or resource that does not exist on your website or app. The number 404 is an HTTP status code meaning “Page Not Found”.

Creating a 404 Page :-

- Create a 404 Component that shows the fallback UI.
- Create < Route path="*" element={< Page_Not_Found />} /> and place it at the end of the route list to catch all the un-matched routes.

---

### HANDLING EVENTS -

- Default attributes in HTML DOM like onclick(), onchange(), onsubmit(), etc. are written in camel case in JSX as onClick(), onChange(), onSubmit(), etc.
- Don’t call the function inside event handlers, just pass the reference.
- If you want to pass arguments to the event handler, you can use Arrow Functions in the JSX.

> ***SyntheticEvent** object is a cross-browser wrapper that ensures event’s properties and behaviours are consistent across all the browsers.*

---

### PASSING DATA BETWEEN COMPONENTS -

Data flow between components in React is primarily Uni-Directional, meaning data moves down the component tree. However, there are several patterns and mechanisms to transfer data, depending on the relationship between the components and the scope of the data.

1. Parent To Child : Props
2. Child To Parent : Callback Functions
3. Sibling Components : Lifting State Up
4. Un-Related Components / Global : React Context API, State Management Libraries and Custom Hooks
5. URL Parameters : Components rendered by a Router can share data via URL Params.

---

### STYLING A COMPONENT -

Styling a React component can be done by the following methods :-

1. Inline Style : Use the style prop with a JavaScript object containing camelCased CSS properties.
2. CSS Stylesheets : Write CSS in separate .css files and import them.
3. CSS Modules : Write CSS in .module.css files to scope CSS locally to components, avoiding global class name conflicts.
4. CSS-in-JS : Use libraries like Styled Components, Emotion CSS, JSS, etc. to write CSS directly into JavaScript.
5. CSS Frameworks & UI Libraries : Bootstrap, Tailwind CSS, Material UI, Ant Design, etc. for pre-built classes and components.

---

### PORTALS -

Portals are a feature in React that allows us to render a component outside the DOM hierarchy of it’s parent component, into a different part of the DOM tree.

You can create a portal using ReactDOM.createPortal() method. It takes two arguments — child (component you want to render) and container (a DOM node where you want to render).

> *Portals does not change hierarchy in the React tree. The component rendered inside the portal is still the part of the default parent component, regardless of where it is rendered in the DOM tree. Therefore Events fired inside the portal still bubble up through the React component tree normally. It also does not affect context in the tree.*

Use Cases :-

- Modals and Portals
- Dropdowns and Menus
- Notifications and Hover Cards

Benefits :-

- Flexible placement of UI components in the DOM.
- Avoid CSS conflicts like z-index, overflow: hidden, etc.

---

### LIFECYCLE METHODS IN REACT -

React Components go through three main phases from creation to removal :-

- Mounting : when a component is being created and inserted into the DOM.
- Updating : when a component is being re-rendered due to changes in props or state.
- Un-Munting : when a component is being removed from the DOM.

> *While Functional Components primarily use the **useEffect() Hook** to manage lifecycle logic, Class Components rely on specific methods called **Lifecycle Methods**. These methods allow you to execute code at specific moments in a component’s life.*

Mounting Phase :-

- constructor() : initialize state, bind event handlers.
- static getDerivedStateFromProps() : sync state with props, static method.
- render() : returns JSX to render the UI.
- componentDidMount() : after component is mounted, runs once, side effects (API calls, subscriptions, etc.).

Updating Phase :-

- static getDerivedStateFromProps() : can update the state based on props, static method.
- shouldComponentUpdate() : returns true / false to allow / prevent re-render.
- render() : returns JSX to render the UI.
- getSnapshotBeforeUpdate() : capture DOM info before it changes.
- componentDidUpdate() : after component is updated, runs after every update, side effects (API calls, subscriptions, etc.).

Un-Mounting Phase :-

- componentWillUnmount() : cleanup tasks — timers, event listeners, network requests, etc., before un-mounting.

> *In Functional Components, useEffect() Hook works the same as componentDidMount() and componentDidUpdate(), i.e., side effects, combined as useEffect(callback, [ dependencies ]). It also returns a cleanup function, which works the same as componentWillUnmount().*

---

### AUTHOR - HITARTH PATHAK