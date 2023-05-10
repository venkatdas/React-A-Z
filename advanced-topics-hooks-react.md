# Advanced topics of React


## How we setup Vite with React
- ```npm create vite@latest my-vue-app -- --template vue```
- Instead of vue replace it with react like
- ```npm create vite@latest my-react-app -- --template react ```
After that
- ```npm install```
- ```npm run dev```

### Table of content React hooks
- useState Hook.
- useEffect Hook.
- useRef Hook.
- useCallback Hook.
- useMemo Hook.
- useContext Hook.
- useReducer Hook.

## What is React Hooks?
- React Hooks are simple JavaScript functions that we can use to isolate the reusable part from a functional component. Hooks can be stateful and can manage side-effects.
- Hooks are a new addition in React 16.8. They let you use state and other React features without writing a class.

### useState Hook
- return an array with two elements : the current state value , and a funcion that we can use to update the state 
- accepts default value as an argument 
- state updates triggers re-render

![image](https://github.com/venkatdas/React-by-john/assets/43024084/905e56bc-b866-4a11-b8c0-bc9a1f6f0732)

![image](https://github.com/venkatdas/React-by-john/assets/43024084/c33114dc-6dd0-4230-afd2-773ea69c2ddb)

- When ever you click the button it's keep on increasing the count.

