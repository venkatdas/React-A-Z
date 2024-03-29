## Functional Based vs Class Based

- Functional based is javascript functional component and it returns a piece of JSX code

```Javascipt
import React from 'react'
const User=()=>{
    return (
      <div className="user-card">
        <h2>Name: Das</h2>
        <h2>Location: HYD</h2>
      </div>
    );
}

export default User
```
- Where as Class Based components  which needs render method that returns piece of JSX code

```Javascript
import React from "react"
class UserClass extends React.Component{
    render(){
return (
 <div className="user-card">
          <h2>Name: Das</h2>
          <h2>Location: HYD</h2>
        </div>
)
         }
}
export default UserClass

```
- React.Component is a class which comes fromm the ` import React from "react"`
- To use the class ased component in other Components just use `<UseClass/>`

### If you Want to props in child components 
- There are some other code to implemet that
  
```Javascript
import User from "./User"
import UserClass from "./UserClass"
const About =()=>{
    return (
        <div>
            <h1>This is regarding the About Component</h1>
            <User name="venkat das" location="Hyderabad"/>
            <UserClass name="venkatdas" location="USA"/>
        </div>
    )
}

export default About
```
- I've written the code that send props to the children of UserClass
- To recrive the Props to Children
Simply

```Javascript
import React from "react";

class UserClass extends React.Component {
  constructor(props) {
    super(props);
    console.log(props);
  }
  render() {
    return (
      <div className="user-card">
        <h2>Name: {this.props.name}</h2>
        <h2>Location: {this.props.location}</h2>
      </div>
    );
  }
}

export default UserClass;
```
- The log result will receive the object that has properties of both Name and Location
- We are using constrctore that reads props and to use the props we define like 'this.props.name'
- There is alternative way to receive them using destructuring
```Javascript
const {name,location}= this.props
```

## How to update state in class based components


```Javascript
import React from "react";

class UserClass extends React.Component {
  constructor(props) {
    super(props);
  this.state={
    count:0,
  }
  }
  render() {
    const{name,location} = this.props
    return (
      <div className="user-card">
        <h2>Count:{this.state.count}</h2>
        <button onClick={()=>{
          // Never update state variables directly this is a wrong method
          // this.state.count= this.state.count+1;
          this.setState({
            count:this.state.count+1,
          })
        }}>Class Increasr</button>
        <h2>Name: class {name}</h2>
        <h2>Location: {location}</h2>
      </div>
    );
  }
}

export default UserClass;
```
- Output
![image](https://github.com/venkatdas/React-A-Z/assets/43024084/063ff31e-cfdf-4f6d-95a6-6f6765f7a4eb)

- From above we can note the few points
- Never update state variables directly
- 'this.state' is object it can contain any number of state variables , even if you dont define all state variables in setState fucntion it will necessary variables that you are declared in the setState fucntion
- Whenever if we click on the button react will trigger the reconsilation algorithm Then it will render the component.

### Life Cycle Methods of Class based component
-  Meta Data
- We have two Class based components
- Parent and Child and let's write the code and see how the those components will be rendered on the screen

```Javascript
// About Parent class
import User from "./User";
import UserClass from "./UserClass";
import React from "react";
class About extends React.Component {
  constructor(props) {
    super(props);
    console.log("Parent Constructor");
  }

  componentDidMount() {
    console.log("Parent Component Did Mount");
  }
  render() {
    console.log("Parent Render");
    return (
      <div>
        <h1>This is regarding the About Component</h1>
        <UserClass name="venkatdas" location="USA" />
      </div>
    );
  }
}
export default About;
```


- Child Class based component



```Javascript
import React from "react";

class UserClass extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
    };
    console.log("Child Constructor called");
  }

  componentDidMount(){
    console.log("Child Component Did Mount");
  }
  render() {
    const { name, location } = this.props;

    console.log("Child Render called");
    return (
      <div className="user-card">
        <h2>Count:{this.state.count}</h2>
        <button
          onClick={() => {
            this.setState({
              count: this.state.count + 1,
            });
          }}
        >
          Class Increase
        </button>
        <h2>Name: class {name}</h2>
        <h2>Location: {location}</h2>
      </div>
    );
  }
}

export default UserClass;
```

From above code snipperrs we will geet the output as follows and This is the relationship between parent and child class based components of life cycle.

![image](https://github.com/venkatdas/React-A-Z/assets/43024084/4a02dd89-5c5d-45d4-a43c-7223e31c14f1)

Explanation
1) Parent constructor will be called
2)Parent render Method will be called
3) Noew It's looking for any child components inside the parent If it is,
4) Then, Child constructor will be called
5) Child render will be called After that if child component has successfully loaded then
6) Child componentDidMount will be called
7) Finallly parent componentDidMount will be called.

This is about  the Mounting Phase.

**The Purpose of the componentDidMount is to make the API calls.** But How
Here is the Explanation

- Page Loading -> Render the UI -> Make an API call -> Re- render the component.

**
- When There is a more than one child components in a parent component the Life cycle method will work as **

![image](https://github.com/venkatdas/React-A-Z/assets/43024084/fe3a5959-50cd-4521-9956-7d744e30ed19)

![image](https://github.com/venkatdas/React-A-Z/assets/43024084/840c2eaa-0dbf-44b6-8adc-4b045435fa2c)

- From above two images we can considered as
Render phase is like it will take constructor and render once all nested components loaded React optimizes the rendering 
- The nested child are batching to Dom and then reloaded onto the screen.



![image](https://github.com/venkatdas/React-A-Z/assets/43024084/6631bd92-a408-43c3-be67-90a293ef30f9)


## Now Let's see How Update cycle works

- To update the lifecycle componentDidMount where we can write the API call to fetch data

```Javascript
import User from "./User";
import UserClass from "./UserClass";
import React from "react";
class About extends React.Component {
  constructor(props) {
    super(props)
    console.log("Parent Constructor");
  }

  componentDidMount() {
    console.log( "Parent Component Did Mount");
  }
  render() {
    console.log("Parent Render");
    return (
      <div>
        <h1>This is regarding the About Component</h1>
        <UserClass />
      </div>
    );
  }
}


export default About;
```
- Above code is a parent code

- Now we are writing the code to fetch data from api in child component

```Javascript
import React from "react";

class UserClass extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      userInfo: {
        name: "dummy",
        location: "Dummy location",
        avatar_url:"",
      },
    };
    console.log("  Child Constructor called");
  }

  async componentDidMount() {
    console.log("  Child Component Did Mount");
    const data = await fetch("https://api.github.com/users/venkatdas");
    const json = await data.json();
    console.log(json);

    this.setState({
      userInfo: json,
    });
  }
  componentDidUpdate() {
    console.log("Component did update");
  }
  render() {
    const { name, location,avatar_url } = this.state.userInfo;
    // debugger;
    console.log("  Child Render called");
    return (
      <div className="user-card">
        <h2>Name:{name}</h2>
        <h2>Location: {location}</h2>
        <img src={avatar_url}/>
        <h2></h2>
      </div>
    );
  }
}

export default UserClass;

```

This is the live output for the update cycle
![image](https://github.com/venkatdas/React-A-Z/assets/43024084/482c4641-76a8-4a84-97a2-f612be677e39)


- From above code and image we can validate the conclusions of as follows

1) We are in the parent component so **Parent constructor is called**
2) Then Parent render is called
3) After that if will check for child components if it is then,
4) Child render component called and it will load local state variable data as known as dummy data
5) Child componentDidMount is called
6) After the child component is mounted, the parent's "Parent Component Did Mount" is logged, indicating that the About component has finished mounting all its content, including its child components, onto the DOM.
7) 
8) Child ComponentDidMount: The componentDidMount lifecycle method of the child component is triggered after the child is mounted on the DOM. If there's an asynchronous operation (like data fetching), it starts but does not necessarily finish immediately. The actual operation is non-blocking, meaning it is set in motion and then control is immediately returned to the JavaScript runtime.
9) 
10) Parent ComponentDidMount: While the asynchronous operation is pending (the data is still being fetched), the React framework continues its lifecycle operations and calls the parent's componentDidMount. At this point, React considers the parent component to be mounted, even though the child's asynchronous data fetching has not yet completed.



11) ONce it is successfully completed the Parent ComponentDidMount is called
12) After that ChildComponent willhave API data and it will update the live API from the github after that again it wil re-render the **child Render **
13) Finally componentDidUpdate called
![image](https://github.com/venkatdas/React-A-Z/assets/43024084/94128247-c1df-4e92-9500-691d3db88c4a)
## componentWillUnmount:

- This will call when component is detached or disabled from the DOM or UI let's say example from the same code we can add the below snippet after the componentDidUpdate

```Javascript
  componentWillUnmount(){
    console.log("Compoonent will unmount is called");
  }
```

- The component is unmounted when you navigating to other external pages and it will automatically unmounted and this is the final phase of life cycle methods.

Snippet

![image](https://github.com/venkatdas/React-A-Z/assets/43024084/c8b60a7b-94b3-4625-b264-d9ac90b06774)










