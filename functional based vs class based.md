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
