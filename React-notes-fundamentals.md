# React Fundamentals

### 1.What is React


i) React is a Javascript library for building User Interfaces.

ii) Developed by Facebook in 2011.

iii) When it comes to react, it's all about components.

 - So React gives us a way to build websites and front end applications and uses in an organized way with reusable components. So components can include the output, which is the basically the HTML in react to use something called JSX. And you can think of components as independent chunks of user interfaces. Components can be as small as one html element.


## Why React?
- Easy creation of dynamic applications: React makes it easier to create dynamic web applications because it requires less coding and offers more functionality, as opposed to JavaScript, where coding often gets complex very quickly.
- Improved performance: React uses Virtual DOM, thereby creating web applications faster. Virtual DOM compares the components’ previous states and updates only the items in the Real DOM that were changed, instead of updating all of the components again, as conventional web applications do. 
- Reusable components: Components are the building blocks of any React application, and a single app usually consists of multiple components. These components have their logic and controls, and they can be reused throughout the application, which in turn dramatically reduces the application’s development time.
- Unidirectional data flow: React follows a unidirectional data flow. This means that when designing a React app, developers often nest child components within parent components. Since the data flows in a single direction, it becomes easier to debug errors and know where a problem occurs in an application at the moment in question.
- Small learning curve: React is easy to learn, as it mostly combines basic HTML and JavaScript concepts with some beneficial additions. Still, as is the case with other tools and frameworks, you have to spend some time to get a proper understanding of React’s library.
- It can be used for the development of both web and mobile apps: We already know that React is used for the development of web applications, but that’s not all it can do. There is a framework called React Native, derived from React itself, that is hugely popular and is used for creating beautiful mobile applications. So, in reality, React can be used for making both web and mobile applications.
- Dedicated tools for easy debugging: Facebook has released a Chrome extension that can be used to debug React applications. This makes the process of debugging React web applications faster and easier.

# ReactJS Advantages

- React.js builds a customized virtual DOM. Because the JavaScript virtual DOM is quicker than the conventional DOM, this will enhance the performance of apps. 
- ReactJS makes an amazing UI possible. 
- Search - engine friendly ReactJS. 
- Modules and valid data make larger apps easier to manage by increasing readability. 
- React integrates various architectures. 
- React makes the entire scripting environment process simpler. 
- It makes advanced maintenance easier and boosts output. 
- Guarantees quicker rendering 
- The availability of a script for developing mobile apps is the best feature of React.
- ReactJS is supported by a large community.


## DOM
![dom](https://user-images.githubusercontent.com/43024084/236741091-60755366-2f9e-4a14-9bf8-2d5a63d23d80.jpg)

- DOM (Document Object Model) treats an XML or HTML document as a tree structure in which each node is an object representing a part of the document.

## Virual DOM vs Real DOM

<img width="514" alt="Virtual_DOM" src="https://user-images.githubusercontent.com/43024084/236741404-e28038f5-664b-4e0d-8dc8-9ed923490772.png">

- The Virtual DOM is React's lightweight version of the Real DOM. Real DOM manipulation is substantially slower than virtual DOM manipulation. When an object's state changes, Virtual DOM updates only that object in the real DOM rather than all of them.

## How do VDOM and RDOM Interact each other?

- When the state of an object changes in a React application, VDOM gets updated. It then compares its previous state and then updates only those objects in the real DOM instead of updating all of the objects. This makes things move fast, especially when compared to other front-end technologies that have to update each object even if only a single object changes in the web application.

## The process of updating in React

1) The ReactDOM.render() renders the elements on the screen on the first load by creating the real and virtual DOM trees.

2) Any change to an element (such as a key press or button click) leads to a notification sent to the virtual nodes for a state change. If any property of the node is altered, it updates itself.

3) React compares the updated virtual DOM with the real DOM and updates the real DOM accordingly. This process is known as reconciliation. This is done using a heuristic algorithm known as the Diffing Algorithm.

4) The updated real DOM is rendered on the screen.


# Folder Strucure while creating npx create-react-app my-app

![Folder Structure In React10](https://user-images.githubusercontent.com/43024084/236744342-fecc2b09-8fff-461f-a8fc-28673c5b3e5c.png)

- node_modules Contains all dependencies required by the app. Main dependencies also listed in package.json

- public Contains static assets including index.html (page template)
  - index.html
    - title
    - fonts
    - css
    - favicon
    - id ="root" our entire app
    
- src In simplest form it's the brain of our app. This is where we will do all of our work. src/index.js is the JavaScript entry point.
- .gitignore Specifies which files source control (Git) should ignore
- package.json Every Node.js project has a package.json and it contains info about our project, for example list of dependencies and scripts
- package-lock.json A snapshot of the entire dependency tree
- README The markdown file where you can share more info about the project for example build instructions and summary

## Babel
- Babel is a JavaScript transpiler that converts the newest JavaScript into the good old JavaScript so we can use all the newest features of the JavaScript language. So think things like an spread operator, destructuring and all the other goodies that come with ES6. And behind the scenes babel will turn into ES5, which in turn will make sure that our app runs smoothly in the older browsers as well.

#### What is JSX and why we are using that?

- JSX stands for JavaScript XML. It's an extension of the JavaScript language based on ES6. It's translated into regular JavaScript at runtime  since browsers cannot read it.
- JSX allows us to write HTML in React which makes the process of writing HTML in your React apps much easier.

#### JSX Rules
- A React component name must be capitalized. Component names that do not begin with a capital letter are treated like built-in components.
- JSX allows you to return only one element from a given component. This is known as a parent element.
- If you want to return multiple HTML elements, simply wrap all of them in a single ```<div></div>,<React.fragments><React.fragments/>, <></>``` or any semnatic tag.

```Javascript
const App = () => {
  return (
    <div>
      <h1>Hello World!</h1>
      <p>Tanishka here!</p>
    </div>
  );
}
```
- In JSX, every tag, including self closing tags, must be closed. In case of self closing tags you have to add a slash at the end (for example <img/>, <hr/>, and so on).
- "class" and "for" are reserved keywords in JavaScript, so use "className" and "forHTML" instead, respectively.

### What are components  in react?

- Components are independent and reusable blocks of code which work in isolation. The main advantage of components is that they help reduce redundancy.
- We can classify components into two types: class components and functional components. 
- Let's look into functional components
- Functional components are JavaScript functions. There are two ways of creating them. The first is by using the function keyword:

```Javascript
function MyComponent(props) {
  return (
    <div>
      <p>Hello, World</p>
      <p>Have a nice day!</p>
    </div>
  );
}
```
- You can also use the arrow function syntax to create functional components:

```Javascript
const MyComponent = (props) => {
  return (
    <div>
			<p>Hello, World</p>
      <p>Have a nice day!</p>
    </div>
  );
}
```
## What are the props in react?

- Props stand for properties. Props are like function arguments, and you send them into the component as attributes.

```Javascript
const Book = (props) => {
  const {bookName, author} = props;
  return (
    <div>
      <h1>Book name : {bookName}</h1>
      <h2>Author : {author}</h2>
    </div>
  );
};
```

### Props Vs State
- There are two types of “model” data in React: props and state. The two are very different:
- Props are like arguments you pass to a function. They let a parent component pass data to a child component and customize its appearance. For example, a Form can pass a color prop to a Button.
- State is like a component’s memory. It lets a component keep track of some information and change it in response to interactions. For example, a Button might keep track of isHovered state.
- Props and state are different, but they work together. A parent component will often keep some information in state (so that it can change it), and pass it down to child components as their props


```
import { RESTDataSource } from '@apollo/datasource-rest';
import { handleGraphqlError } from '../../utils/graphqlError.js';
import { ERROR_DATASOURCES } from '../../utils/constants.js';

import {
  CSO_ACCOUNT_QUERY,
  CSO_DETAILS_QUERY,
  CSO_GROUP_QUERY,
  CSO_NAME_QUERY
} from '../Teradata/Alerts/queries.js';

class getCSOData extends RESTDataSource {
  baseURL =
    'https://gehealthcare-amer--uat.sandbox.my.salesforce.com/services/data/v39.0/query/?q=';

  constructor(options) {
    super(options);
    this.token = options.token;
  }

  willSendRequest(_path, request) {
    request.headers['Authorization'] = this.token;
  }

  async getAPIData(queryURL) {
    const apiURL = `${this.baseURL}${queryURL}`;
    console.log('apiURL', apiURL);
    console.log('typeof apiURL', typeof apiURL);
    try {
      const data = await this.get(apiURL);
      console.log('data', data);
      return data;
    } catch (error) {
      return handleGraphqlError(error, ERROR_DATASOURCES.CSODATA);
    }
  }

  async getCSOData({ type, list }) {
    if (type === 'CSO_Account') {
      const param = list.join(',');
      const queryURL = CSO_ACCOUNT_QUERY(param);
      await this.getAPIData(queryURL);
    } else if (type === 'CSO_Group') {
      const queryURL = CSO_GROUP_QUERY(list);
      await this.getAPIData(queryURL);
    } else if (type === 'CSO_Name') {
      const queryURL = CSO_NAME_QUERY(list);
      await this.getAPIData(queryURL);
    } else {
      const queryURL = CSO_DETAILS_QUERY(list);
      await this.getAPIData(queryURL);
    }
  }
}

export default getCSOData;



//resolver
import { ERROR_DATASOURCES, STATUS_CODES } from '../../utils/constants.js';
import { handleCommonError } from '../../utils/graphqlError.js';

export const getCSODataAPIResolver = {
  async getCSOData(_, { type, list }, { dataSources }) {
    try {
      return dataSources.getCSO.getCSOData({ type, list });
    } catch (error) {
      return handleCommonError({
        message: STATUS_CODES.INVALID_PAYLOAD,
        status: 400,
        description: error?.message,
        source: ERROR_DATASOURCES.CSODATA
      });
    }
  }
};


export const getCSODataAPISchema = `
type GetCSOResponse {
  totalSize: Int
  done: Boolean
  records: [String]
}
`;

export const getCSODataQueries = `
getCSOData(type: String, list: [String]): GetCSOResponse
`;
```

