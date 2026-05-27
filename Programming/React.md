useMemo: Use to cache the result of heavy calculation
Composition > Inheritance: Create a composite components from other components, texts, modals

setState/state: async set, re-rendering components on React
useState() to manage the state of the updatable components. It store the components data to a List or Stack in the memory. useState can return a messy data if we use useState with conditional state or loop
useEffect() handle for the I/O call, side effects, asynchronous operations, like calling API. Does not make re-rendering components.

Functional component > Class component
useRef() synchronous, store the previous value, it's like a silent box, without changing the UI. Can use useRef to refer to the DOM component, then trigger the DOM behaviors (focus, play video, that are not managed by React)

Hooks are utility functions that allow to access advanced react features like state management, lifecycle methods directly inside functional components, that are feasible only with Class components before. 

useCallback() to store the function to avoid component re-rendering, because the function inside the Functional Component will be created newly if not using useCallback()
useCallback() must be used with memo to check and compare the heavy component with the previous rendering. 
React: Parent component changes > re-rendering the child components as well


**Redux**
Predictable state container designed for the Javascript apps. It serves as centralized store for entire application's state, making it easier to manage and debug the data flow in complex envs. It has 3 main parts.
- Slices (*in the Store*): Source of truth for global state 
- Reducers: Pure functions to describe how the state changes, create changes for new state based on the action
- Action: Just define the actions type "LOGOUT", "LOGIN". Based on that, the reducers will process based on the action type. >> re-render the component. 
useSelector: get the state, extract data from the Redux storage
useDispatch: send actions to the store to trigger update

Redux toolkit: RTK, better and mordern Redux, reduce the boilerplate codes

**Props and children props**
Props are immutable, cannot be changed by the functional components.
Children props: it's passing the components to another components, it's for component compositing.


**Key in the list**
Key is used to identify the component in the list and it can avoid the re-ordering

**Lifting state up**
A parent components and two child components are managing to the same state. The state should be brought to the parent and parent will pass the state and setter to the child.
Prop drilling: happens when have to pass the state too far, too many layers. >> Context API | Redux

**Context**
Use the useContext for low frequency update data, the data can be used anywhere in the context wrapper.