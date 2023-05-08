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


