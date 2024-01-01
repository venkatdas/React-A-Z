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

![image](https://github.com/venkatdas/React-A-Z/assets/43024084/94128247-c1df-4e92-9500-691d3db88c4a)

