## Functional Based vs Class Based

- Functional based is javascript functional component and it returns a piece of JSX code

```  javascipt

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
