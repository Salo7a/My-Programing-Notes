# React Notes

## Hooks

* useState \
  `Create states for components, when using setState, the state is changed instantaneously rather it is scheduled, although it usually happens very fast it could be delayed if the event loop is busy with more intensive tasks, thus when we want to updated a state based on its current state e.g. incrementing the state, we give the setState a callback function that handles this update where the first argument will be the latest state, changes of the same state are always processed in-order, useEffect doesn't have this problem since it is always rerun when the state actually changes so it's safe to directly setState without functions in them, multiple updates will be processed together if they are in the same sync code block.`

* useReducer \
  `Allows for more complex state management, requires a function that handles updating the state`

* useEffect \
  `Run side effects when given states change or once when given an empty array as the second argument, 'side effects' might be sending HTTP requests, changing other states and applying animations, basically run the callback function when this changes, on re-render or -not regularly used- every re-evaluation of the component, state setting functions don't need to be added as React ensures that they are always the same, all other used states should be added to the dependencies array`

* useContext \
  `Used to access a context`

* useRef \
  `Get a reference to the actual DOM element it refers to, can be used to directly access the value of an input without storing it in a state, or possibly modifying it though it is usually not recommend to directly change elements circumventing react, it is possibly for simpler things such as resetting an input`

* useCallback \
 `Useful with memo function, stores a function across component executions so that it doesn't get re-created, the first argument is the function, the second is its dependencies which are important because since functions are closure in JS thus when it is defined all variables defined outside it is locked in and don't change, so in that case we want to recreate the function`

* useMemo \
 `Similar to useCallback, but memoize objects e.g arrays`

## Functions

### Enveloping Functional Components

* memo \
  `OPTIMIZATION: Prevents re-evaluation of children when parent is re-evaluated, useful in larger apps to cut off larger component trees as it has its own performance cost as it stores and compares prev and current props, doesn't work with non-primitive prop values as technically the reference changes, for functions pair it with useCallback`

* forwardRef \
  `Used to pass on a ref to the parent component`

## General Knowledge

* Controlled vs Uncontrolled Components \
  `Controlled: Component that all of its state & behavior is controlled by its parent passing them using props and notifies of changes using callbacks such as onChange e.g. a form input where its value is stored in a state and updated through onChange, also called a dumb component` 

  `Uncontrolled: Component that manages its own state internally, and you access its values by directly accessing the DOM using refs e.g. form input that doesn't use state or onChange to store its values `

* Functional Components Return Value \
  `They should always return one element, which may contain multiple children element, either wrap all elements with a parent element or to avoid unnecessary elements use fragments <></> or <React.Fragment>`  
