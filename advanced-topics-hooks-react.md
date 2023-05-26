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
### useState Array Example:
![image](https://github.com/venkatdas/React-by-john/assets/43024084/3bb57ac4-df4c-41f6-805a-70796ff3ce20)

- We are importing above data 
```Javascript
const UseStateArray = () => {
  const [people, updatedPeople] = useState(data);
  const RemoveItem = (id) => {
    const newItem = people.filter((person) => person.id !== id);
    updatedPeople(newItem);
  };
  const ClearAllItems = () => {
    updatedPeople([]);
  };
  return (
    <div>
      {people.map((value) => {
        const { name, id } = value;
        return (
          <div key={id}>
            <h4>{name}</h4>
            <button onClick={() => RemoveItem(id)} className="btn">
              remove
            </button>
          </div>
        );
      })}
      <button
        className="btn"
        style={{ marginTop: "2rem" }}
        onClick={ClearAllItems}
      >
        Clear Items
      </button>
    </div>
  );
};
```

- The Output is 
- ![image](https://github.com/venkatdas/React-by-john/assets/43024084/56f25fa2-88aa-4682-9f6d-4827ace330d5)

- Whenever if you click on the remove button you remove it from existing content and as well as if you click on the clear all it clears the entire screen.

### Inatiall Render VS Re-render
- In a React application, the initial render is the first time that the component tree is rendered to the DOM. It happens when the application first loads, or when the root component is first rendered. This is also known as "mounting" the components.
- Re-renders, on the other hand, happen when the component's state or props change and the component needs to be updated in the DOM to reflect these changes. React uses a virtual DOM to optimize the process of updating the actual DOM so that only the necessary changes are made.
#### There are a few ways that you can trigger a re-render in a React component:
- By changing the component's state or props. When the component's state or props change, React will re-render the component to reflect these changes.
- When the parent element re-renders, even if the component's state or props have not changed.
#### General rules of hooks

- starts with "use" (both -react and custom hooks)
- component must be uppercase
- invoke inside function/component body
- don't call hooks conditionally 
- set functions don't update state immediately 

#### Automatic Batching
- In React, "batching" refers to the process of grouping multiple state updates into a single update. This can be useful in certain cases because it allows React to optimize the rendering of your components by minimizing the number of DOM updates that it has to perform.
- By default, React uses a technique called "auto-batching" to group state updates that occur within the same event loop into a single update. This means that if you call the state update function multiple times in a short period of time, React will only perform a single re-render for all of the updates.
- React 18 ensures that state updates invoked from any location will be batched by default. This will batch state updates, including native event handlers, asynchronous operations, timeouts, and intervals.

### useEffect hook

- useEffect is a hook in React that allows you to perform side effects in function components.There is no need for urban dictionary - basically any work outside of the component. Some examples of side effects are: subscriptions, fetching data, directly updating the DOM, event listeners, timers, etc.
- It is basically a hook replacement for the "old-school" lifecycle methods componentDidMount, componentDidUpdate and componentWillUnmount.


- useEffect hook
- accepts two arguments (second optional)
- first argument - cb function
- second argument - dependency array
- by default runs on each render (initial and re-render)
- cb can't return promise (so can't make it async)
- if dependency array empty [] runs only on initial render

- useEffect will only runs inintial render
- ![useeffect](https://github.com/venkatdas/React-by-john/assets/43024084/98e69e93-5b01-48b3-aea4-43f5b66a8667)
![useeffect -output](https://github.com/venkatdas/React-by-john/assets/43024084/14d39eec-17c4-4683-a746-518d257b7424)

- From the above code the main difference between use Effect and normal function is as follows
- If we have just the plan function or we invoke the function inside of the component yes, it's going to run on INTIAL RENDER AND EVERY RE-RENDER.
- However, with useEffect we can start controlling  when this functionality runs  .
- Briefly, with useEffect we provide a callback function which is going to be invoked pretty much after every render, unless we provide here a dependency array. In that case , if we have dependecy array and if it's empty , the functionality inside of the useEffect is going to run once only when the component mounts on the initial render.

### Use Effect another example by fetching data

```javascript
const DataFetch = () => {
  const [users, setUsers] = useState([]);
  useEffect(() => {
    // fetch(url).then((resp) => {
    //   resp.json().then((data) => {
    //     setUsers(data);
    //   });
    // });
    const DataFetching = async () => {
      try {
        const resp = await fetch(url);
        const listOfData = await resp.json();
        setUsers(listOfData);
      } catch (error) {
        console.log(error);
      }
    };
    DataFetching();
  }, []);

  return (
    <section>
      <h2>Github user API</h2>
      <ul className="users">
        {users.map((user) => {
          const { id, login, avatar_url, html_url } = user;
          return (
            <li key={id}>
              <img src={avatar_url} alt={login} />
              <div>
                <h5>{login}</h5>
                <a href={html_url}>Profile</a>
              </div>
            </li>
          );
        })}
      </ul>
    </section>
  );
};
```

![image](https://github.com/venkatdas/React-by-john/assets/43024084/899c545e-efbd-4d55-a848-5ffe58ab5324)


### Conditional Rendering in React

- Your components will often need to display different things depending on different conditions. In React, you can conditionally render JSX using JavaScript syntax like if statements, &&, and ? : operators.
- In React, conditional rendering is the process of displaying different content based on certain conditions or states. It allows you to create dynamic user interfaces that can adapt to changes in data and user interactions

#### Why conditional rendering is necessary in react?

- **Improved User Experience:** Conditional rendering allows you to create dynamic user interfaces that adapt to changes in data and user interactions. By showing and hiding content based on the user's actions or the application state, you can create a more intuitive and engaging user experience.
- **Improved Performance:** By conditionally rendering content, you can avoid rendering unnecessary components and improve the performance of your application. This is particularly important in larger applications where unnecessary rendering can lead to performance issues.
- **Simplified Code:** Conditional rendering can help you simplify your code and make it more readable. By using conditional statements to decide what content should be rendered, you can avoid duplicating code and create more modular components.
- **Flexibility**: Conditional rendering allows you to create more flexible and customizable components. By rendering different content based on the application state, you can create components that can be used in different contexts and adapt to different user interactions.

#### Multiple returns using conditional rendering examples.


```javascript

const MultipleReturnsFetchData = () => {
  const [isLoading, setIsLoading] = useState(true);
  const [isError, setIsError] = useState(false);
  const [data, setData] = useState([]);
  useEffect(() => {
    const fetchUser = async () => {
      try {
        const resp = await fetch(url);
        console.log(resp);
        // if (!resp.ok) {
        //   setIsError(true);
        //   setIsLoading(false);
        //   return;
        // }
        const result = await resp.json();
        setData(result);
        // setIsLoading();
        //console.log(result);
      } catch (error) {
        setIsError(true);
        console.log(error);
      }
      setIsLoading(false);
      // console.log(result);
    };
    fetchUser();
  }, []);

  if (isLoading) {
    return <h2>Loading....</h2>;
  }
  if (isError) {
    return <h2>There was an error....</h2>;
  }

  return (
    <div>
      <img
        style={{ width: "150px", borderRadius: "25px" }}
        src={data.avatar_url}
        alt={data.name}
      />
      <h2>Fetch Data</h2>
      <h2>{data.name}</h2>
      <h4>works at {data.company}</h4>
      <p>{data.bio}</p>
    </div>
  );
};
export default MultipleReturnsFetchData;
```

