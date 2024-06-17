React JS

- As React runs over a server and returns a virtual DOM request while browsing, it makes the web pages light for the search engine crawlers to crawl through the web pages and ultimately makes it easier to rank.

- React is known for its component-based architecture which allows you to create reusable UI elements, 

FEATURE OF REACT

1.JSX(Javascript Syntax Extension):
* JSX combines HTML and JavaScript, allowing you to embed JavaScript objects within HTML elements.

2. Virtual DOM (Document Object Model):
* When there are modifications in the web application, React updates the virtual DOM first and then computes the differences between the real DOM and the virtual DOM.

3. One-way Data Binding:
* React follows one-way data binding, where data flows from parent components to child components.

4. Conditional Statements in JSX:
* JSX allows writing conditional statements directly.


React virtual DOM:
- process of comparing the current Virtual DOM tree with the previous one(pre-update) is known as ‘diffing’. 

-React uses something called batch updates to update  the real DOM. It just means that the changes to the real DOM are sent in batches instead of sending any update for a single change in the state of a component. 

ReactDOM package:

1. ReactDOM.render(): takes two arguments, HTML code and an HTML element. 
     -The render() method is the only required method in a class component. When called, it should examine this.props and this.state and return one of the following types: React elements. Typically created via JSX.


Component type
1. functional component : The functional component is also known as a stateless component because they do not hold or manage state. They use props (properties) to receive data and return JSX to render the component. 

2. Class Component : Class components are stateful components that are written as a JavaScript class. They have the ability to manage their own internal state, and can respond to user events.

Class Component lifecycle

->Initialisation 

-> Mounting Phase
- Mounting means putting elements into the DOM.    
1. constructor()
2. static getDerivedStateFromProps(props, state)
3. render()
4. componentDidMount():  where you run statements that requires that the component is already placed in the DOM.

-> update Phase : 
- A component is updated whenever there is a change in the component's state or props.
1. static getDerivedStateFromProps(props, state)
2. shouldComponentUpdate(currProp, prevProp)
3. render()
4. getSnapshotBeforeUpdate(prevProps, prevState)
5. componentDidUpdate(prevProps, prevState, snapshot)


[NOTE :- It can also be triggered when a component consists of the following methods:
static getDerivedStateFromProps(), shouldComponentUpdate(), render(), getSnapshotBeforeUpdate(), and componentDidUpdate().]

-> unmounting phase:
- The next phase in the lifecycle is when a component is removed from the DOM, or unmounting as React likes to call it.

1. componentWillUnmount()


STATE Object

- The state object is where you store property values that belongs to the component.
- When the state object changes, the component re-renders.
- component properties should be kept in an object called state. 


PROPs
- Props are like function arguments, and you send them into the component as attributes
- If your component has a constructor function, the props should always be passed to the constructor and also to the React.Component via the super() method.
- React Props are read-only! You will get an error if you try to change their value.

Events
- onClick={shoot}  instead of onclick="shoot()".
- To pass an argument to an event handler, use an arrow function.

Conditional Rendering:
- If-Else
- Ternary
- If cars.length > 0 is equates to true, the expression after && will render.


HOOKS
function component does not have option to manipulate lifecycle events of a component. To enable state and lifecycle events in the function component, React introduced a new concept called Hooks.
* Hooks can only be called inside React function components.
* Hooks can only be called at the top level of a component.
* Hooks cannot be conditional

1. useState(): the useState Hook to keep track of the application state.    
	 -useState hook is simple and easy way to do state management in the function 			   component	
	e.g. const [color, setColor] = useState("");
	   -  value, color, is our current state.
	   - The second value, setColor, is the function that is used to update our state.
- The useState Hook can be used to keep track of strings, numbers, booleans, arrays, objects, and any combination of these!
- [Note: Do not mutate state object directly, instead replace it with new updated state object]

2. useEffect(<setup function>, <dependency>): 

- A setup function with setup code that connects to that system.
    * It should return a cleanup function with cleanup code that disconnects from that system.
- Dependency is a list of values that the effect depends on. When any of these dependencies change, the effect is re-run. If the array is omitted or is empty, the effect will run on every render. 
             - Run on every render: No dependencies array provided.
	     -	Run only once on mount and cleanup on unmount: Empty dependencies array.
	     - Run when specific dependencies change: Non-empty dependencies array.

	After every re-render:-
    * First, your cleanup code runs with the old props and state.
    * Then, your setup code runs with the new props and state.

- https://dev.to/jahid6597/why-useeffect-is-running-twice-in-react-18c6

3. useContext(contextName) :
- The createContext function returns a context object. The returned object has the Provider and Consumer properties. These properties are React components and are usually referred to as context providers and consumers respectively.

- https://refine.dev/blog/usecontext-and-react-context/#what-is-prop-drilling


4. useReducer(): useReducer(<reducer function>, <initial argument>, <init function>);

- const [state, dispatch] = useReducer(reducer, initialState);
	state: The current state of the component.
	dispatch: A function that you call to send an action to the reducer.
	reducer: A function that takes the current state and an action, and returns a new state.
	initialState: The initial state of the component.

- useReducer returns an array with exactly two items:
            1. The current state of this state variable, initially set to the initial state you provided.
            2. The dispatch function that lets you change it in response to interaction.

5. useCallback(<callback_fn>, <dependency_array>):
- The useCallback hook is similar to useMemo hook and provides the functionality of        memoizing the function instead of values
    * callback_fn − Callback function to be memorized.
    * dependency_array − Hold variables, upon which the callback function depends.
[Note − The useCallback(callback_fn, dependency_array) is equivalent to useMemo(() => callback_fn, dependency_array).]


6. React.memo & useMemo() :-
- React.memo memoizes a functional component and its props. 
- Doing so helps prevent unnecessary re-renderings that originate from the re-renderings of the component's parent / ancestors.
- Memoization :- Memoization lets us bypass the function's costly computations when the function is called with the same parameters repeatedly.
- Caching function values is done using useMemo() hook. And callback functions are memoized with the useCallback() hook.

- React.memo() is a Higher Order Component (HOC) that memoizes the passed in component along with the value of its prop
- It produced a new component that re-renders only when its props and internal state is changed.
- So, typically we should use React.memo when we want to prevent re-renderings due to state changes that do not concern our component and only allow re-renderings due to prop changes that happen often or are driven by an event.
- We Can add custom dependencies in React.memo(component,  dependency_Logic)

- useMemo() hook is a function that caches the value produced from an expensive function used inside a React component.
- In React, data processing, transformation and manipulation utilities like sorting functions, filters and mappers are commonly used costly functions.
-  it is important that we leverage useMemo when the execution of the utility function depends on relevant state changes. 
- useMemo should be used only to memoize the value returned from a function, not the function itself this is main difference btw useMemo & useCallback
  
- https://refine.dev/blog/react-memo-guide/#expensive-utilities
