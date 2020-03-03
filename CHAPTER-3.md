# Using a Build Workflow

Recommended for SPAs and MPAs

- Optimize code
- Use Next-Gen JavaScript Features(ES6 vs ES5)
- Be More Productive.

- Use Dependency Management Tool npm or Yarn
- Use Bundler -> Recommended: webpack
- Use Compiler(Next-Gen JavaScript) Babel + Presets
- Use a Development Server.

# Create React App

- Visit, https://github.com/facebook/create-react-app
- Install Node -> https://nodejs.org/en/download/
- Cmd Prompt -> For Windows, npm install create-react-app -g and For Mac, sudo npm install create-react-app -g
- Required Folder -> Open Cmd Prompt -> create-react-app react-complete-guide --scripts-version 1.1.5
- Project path -> Cmd Prompt -> npm start
- ctrl+c -> Close

# Understanding JSX

- JSX stands for JavaScript XML. With React, it's an extension for XML-like code for elements and components.
- In Other words, JavaScript extension, or more commonly JSX, is a React extension that allows us to write JavaScript that looks like HTML.
- The JSX is translated to regular JavaScript at runtime.

```ruby
import React, { Component } from 'react';
import './App.css';

class App extends Component {
  render() {
    // return (
    //   <div className="App">
    //    <h1>Hello World</h1>
    //   </div>
    // );
    return React.createElement('div', {className:'App'}, React.createElement ('h1',null, 'Hello World'))
  }
}
```

export default App;

# Components

- A Component is one of the core building blocks of React. 
- In other words, we can say that every application you will develop in React will be made up of pieces called components. 
- Components make the task of building UIs much easier. 
- You can see a UI broken down into multiple individual pieces called components and work on them independently and merge them all in a parent component which will be your final UI.
- In React we mainly have two types of components(i.e) Functional Components, Class Components.

# Functional Components

- Functional components are simply javascript functions. 
- We can create a functional component in React by writing a javascript function. 
- These functions may or may not receive data as parameters

```ruby
function Democomponent()
{
    return <h1>Welcome Message!</h1>;
}
```

# Class Components

- The class components are little more complex than the functional components. 
- The functional components are not aware about the other components in your program where as the class components can work with each other. 
- We can pass data from one class component to other class component. 
- We can use javascript ES6 classes to create class based components in React.

```ruby
class Democomponent extends React.Component
{
    render(){
          return <h1>Welcome Message!</h1>;
    }
}
```

# Rendering Components

- React is also capable of rendering user-defined components. 
- To render a component in React we can initialize an element with a user-defined component and pass this element as the first parameter to ReactDOM.render() or directly pass the component as first argument to the ReactDOM.render() method.
- Below syntax shows how to initialize a component to an element

```ruby
const elementName = <ComponentName />;
```

- In the above syntax the ComponentName is the name of the user-defined component.
- Note: The name of a component should always start with a capital letter.
- This is done to differentiate a component tag with html tags.

# Sample

In App.js

```ruby
import React, { Component } from 'react';
import './App.css';
import Person from './Person/Person.js'

class App extends Component {
  render() {
    return (
      <div className="App">
       <h1>Hello World</h1>
       <p>This is Working!!!</p>
       <Person />
       <Person />
       <Person />
      </div>
    );
  }
}

export default App;
```
Create a Person.js

```ruby
import React from 'react'

const person = () => {
    return <p>I am a Developer</p>
}

export default person;
``` 

