# 3.1. Using a Build Workflow

Recommended for SPAs and MPAs

- Optimize code
- Use Next-Gen JavaScript Features(ES6 vs ES5)
- Be More Productive.

- Use Dependency Management Tool npm or Yarn
- Use Bundler -> Recommended: webpack
- Use Compiler(Next-Gen JavaScript) Babel + Presets
- Use a Development Server.

# 3.2. Create React App

- Visit, https://github.com/facebook/create-react-app
- Install Node -> https://nodejs.org/en/download/
- Cmd Prompt -> For Windows, npm install create-react-app -g and For Mac, sudo npm install create-react-app -g
- Required Folder -> Open Cmd Prompt -> create-react-app react-complete-guide --scripts-version 1.1.5
- Project path -> Cmd Prompt -> npm start
- ctrl+c -> Close

# 3.3. Understanding JSX

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

# 3.4 Components

- A Component is one of the core building blocks of React. 
- In other words, we can say that every application you will develop in React will be made up of pieces called components. 
- Components make the task of building UIs much easier. 
- You can see a UI broken down into multiple individual pieces called components and work on them independently and merge them all in a parent component which will be your final UI.
- In React we mainly have two types of components(i.e) Functional Components, Class Components.

# 3.5. Functional Components

- Functional components are simply javascript functions. 
- We can create a functional component in React by writing a javascript function. 
- These functions may or may not receive data as parameters

```ruby
function Democomponent()
{
    return <h1>Welcome Message!</h1>;
}
```

# 3.6. Class Components

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

# 3.7. Rendering Components

- React is also capable of rendering user-defined components. 
- To render a component in React we can initialize an element with a user-defined component and pass this element as the first parameter to ReactDOM.render() or directly pass the component as first argument to the ReactDOM.render() method.
- Below syntax shows how to initialize a component to an element

```ruby
const elementName = <ComponentName />;
```

- In the above syntax the ComponentName is the name of the user-defined component.
- Note: The name of a component should always start with a capital letter.
- This is done to differentiate a component tag with html tags.

# 3.8. Sample

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
# 3.9. Working with Props

- Props are arguments passed into React components.
- Props are passed to components via HTML attributes.
- React Props are like function arguments in JavaScript and attributes in HTML.
- props.children -> refers to any elements that includes plain text as we have it here between the opening and closing tag of our component and you can nest complex html code in-between too.

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
       <Person name='Gauthy'/>
       <Person name='Gowthy'>My Hobbies: Coding</Person>
       <Person name='Gowtham'/>
      </div>
    );
  }
}

export default App;
```
In Person.js

```ruby
import React from 'react'

const person = (props) => {
    return (
        <div>
            <p>I am a {props.name} and I am { Math.floor( Math.random()*20 ) } years Old</p>
            <p>{props.children}</p>
        </div>
    );
    
}

export default person;
```

# 3.10. Using State

- React components has a built-in state object.
- The state object is where you store property values that belongs to the component.
- When the state object changes, the component re-renders.
- The set state property allows us to update this special state property here and it will then ensure that React gets to know about this update and updates the DOM.
- set state takes an object as an argument and it will merge whatever we define here with our existing state.

```ruby
import React, { Component } from 'react';
import './App.css';
import Person from './Person/Person.js'

class App extends Component {
  state = {
    persons: [
      {name: 'Gauthy', age: 22},
      {name: 'Gowthy', age: 24},
      {name: 'Gowtham', age: 26}
    ]
  }

  SwitchNameHandler = () => {
    // Don't do like this -> this.state.persons[0].name = 'Ram';
    this.setState({persons: [
      {name: 'Ram', age: 22},
      {name: 'Gowthy', age: 24},
      {name: 'Gowtham', age: 26}
    ]})
  }

  render() {
    return (
      <div className="App">
       <h1>Hello World</h1>
       <p>This is Working!!!</p>
       <button onClick={this.SwitchNameHandler}>Switch Name</button>
       <Person name={this.state.persons[0].name} age = {this.state.persons[0].age}/>
       <Person name={this.state.persons[1].name}>My Hobbies: Coding</Person>
       <Person name={this.state.persons[2].name}/>
      </div>
    );
  }
}

export default App;
```
# 3.11. Using the useState() Hook for State Manipulation

- In React 16.8, there also is a way for us to manage state in functional components with a feature called react hooks.
- React Hooks are functions that let us hook into the React state and lifecycle features from function components.
- In other words, React Hooks is basically a collection of functions exposed to you by React which you can use in functional components.
- By this, we mean that hooks allow us to easily manipulate the state of our functional component without needing to convert them into class components.
- Hooks don’t work inside classes(because they let you use React without classes).
- By using them, we can totally avoid using lifecycle methods, such as componentDidMount, componentDidUpdate, componentWillUnmount.

# 3.12. Basic Built-in Hooks

- Returns a stateful value and a function to update it — useState.
- Lets you perform side effects in function components — useEffect.
- Accepts a context object (the value returned from React.createContext) and returns the current context value, as given by the nearest context provider for the given context — useContext.

# 3.13. Rules of Hooks

- Don’t call Hooks inside loops, conditions, or nested functions — Only call Hooks at the top level.
- Don’t call Hooks from regular JavaScript functions — Only call Hooks from React function components.

```ruby
import React, { useState } from 'react';
import './App.css';
import Person from './Person/Person.js'

const app = props => {

  const [personState, setPersonState] = useState({
      persons: [
        {name: 'Gauthy', age: 22},
        {name: 'Gowthy', age: 24},
        {name: 'Gowtham', age: 26}
      ],
      otherState: 'some other values'
    }
  );

  const [otherState, setOtherState] = useState('some other values');
  console.log(personState, otherState)

  const SwitchNameHandler = () => {
    // Don't do like this -> this.state.persons[0].name = 'Ram';
    setPersonState({persons: [
      {name: 'Ram', age: 22},
      {name: 'Gowthy', age: 24},
      {name: 'Gowtham', age: 26}
    ],
    otherState: personState.otherState
  })
  }

    return (
      <div className="App">
       <h1>Hello World</h1>
       <p>This is Working!!!</p>
       <button onClick={SwitchNameHandler}>Switch Name</button>
       <Person name={personState.persons[0].name} age = {personState.persons[0].age}/>
       <Person name={personState.persons[1].name}>My Hobbies: Coding</Person>
       <Person name={personState.persons[2].name}/>
      </div>
    );
  }


export default app;
```
# 3.14. Stateless vs Stateful components

- Stateful component is a component that manage state, no matter if it's using the useState hook or a class-based approach with the state property.
- A component is like the person.js so this person component is a stateless component because it has no internal state management.
- It is a good practice to create as many of these stateless components, also called dumb, presentational components because they have no internal logic or presentational components.
- The Stateful components, so either class-based with state or functional with useState are also called smart components or conatiner components because they contain the state of your application, of these components.

# Passing Method References Between Components

In App.js

```ruby
import React, { Component } from "react";
import "./App.css";
import Person from "./Person/Person.js";

class App extends Component {
  state = {
    persons: [
      { name: "Gauthy", age: 22 },
      { name: "Gowthy", age: 24 },
      { name: "Gowtham", age: 26 }
    ]
  };

  SwitchNameHandler = () => {
    // Don't do like this -> this.state.persons[0].name = 'Ram';
    this.setState({
      persons: [
        { name: "Ram", age: 22 },
        { name: "Gowthy", age: 24 },
        { name: "Gowtham", age: 26 }
      ]
    });
  };

  render() {
    return (
      <div className="App">
        <h1>Hello World</h1>
        <p>This is Working!!!</p>
        <button onClick={this.SwitchNameHandler}>Switch Name</button>
        <Person
          name={this.state.persons[0].name}
          age={this.state.persons[0].age}
        />
        <Person
          name={this.state.persons[1].name}
          click={this.SwitchNameHandler}
        >
          My Hobbies: Coding
        </Person>
        <Person name={this.state.persons[2].name} />
      </div>
    );
  }
}

export default App;
```
In Person.js

```ruby
import React from 'react'

const person = (props) => {
    return (
        <div>
            <p onClick = {props.click}>I am a {props.name} and I am { Math.floor( Math.random()*20 ) } years 		Old</p>
            <p>{props.children}</p>
        </div>
    );
    
}

export default person;
```

# 3.15. Binding functions

- Bounded function in JavaScript is a function that is bounded to a given context. 
- That means no matter how you call it, the context of the call will stay the same. 
- The only exception is the new operator which always return a new context.
- To create a bounded function out of the regular function, the bind method is used. bind method take context to which you want to bind your function as a first argument. 
- The rest of arguments are arguments that will be always passed to such function. It returns a bounded function as a result

In App.js

```ruby
import React, { Component } from "react";
import "./App.css";
import Person from "./Person/Person.js";

class App extends Component {
  state = {
    persons: [
      { name: "Gauthy", age: 22 },
      { name: "Gowthy", age: 24 },
      { name: "Gowtham", age: 26 }
    ]
  };

  SwitchNameHandler = (newName) => {
    // Don't do like this -> this.state.persons[0].name = 'Ram';
    this.setState({
      persons: [
        { name:  newName, age: 22 },
        { name:  newName, age: 24 },
        { name: "Gowtham", age: 26 }
      ]
    });
  };

  render() {
    return (
      <div className="App">
        <h1>Hello World</h1>
        <p>This is Working!!!</p>
        <button onClick={this.SwitchNameHandler.bind(this, 'Android')}>Switch Name</button>
          {/* Alternative way but not the efficient one */}
          {/* <button onClick={() => this.SwitchNameHandler('Android')}>Switch Name</button> */}
        <Person
          name={this.state.persons[0].name}
          age={this.state.persons[0].age}
        />
        <Person
          name={this.state.persons[1].name}
          click={this.SwitchNameHandler.bind(this, 'Flutter')}
        >
          My Hobbies: Coding
        </Person>
        <Person name={this.state.persons[2].name} />
      </div>
    );
  }
}

export default App;

```
In Person.js

```ruby
import React from 'react'

const person = (props) => {
    return (
        <div>
            <p onClick = {props.click}>I am a {props.name} and I am { Math.floor( Math.random()*20 ) } years 		Old</p>
            <p>{props.children}</p>
        </div>
    );
    
}

export default person;
```
# 3.16. Adding Two Way Binding

In App.js

```ruby
import React, { Component } from "react";
import "./App.css";
import Person from "./Person/Person.js";

class App extends Component {
  state = {
    persons: [
      { name: "Gauthy", age: 22 },
      { name: "Gowthy", age: 24 },
      { name: "Gowtham", age: 26 }
    ]
  };

  SwitchNameHandler = (newName) => {
    // Don't do like this -> this.state.persons[0].name = 'Ram';
    this.setState({
      persons: [
        { name:  newName, age: 22 },
        { name:  newName, age: 24 },
        { name: "Gowtham", age: 26 }
      ]
    });
  };

  nameChangedHandler = ( event ) => {
    this.setState({
      persons: [
        { name:  'Android', age: 22 },
        { name:  event.target.value, age: 24 },
        { name: "Gowtham", age: 26 }
      ]
    });
  }

  render() {
    return (
      <div className="App">
        <h1>Hello World</h1>
        <p>This is Working!!!</p>
        <button onClick={this.SwitchNameHandler.bind(this, 'Android')}>Switch Name</button>
          {/* Alternative way but not the efficient one */}
          {/* <button onClick={() => this.SwitchNameHandler('Android')}>Switch Name</button> */}
        <Person
          name={this.state.persons[0].name}
          age={this.state.persons[0].age}
        />
        <Person
          name={this.state.persons[1].name}
          click={this.SwitchNameHandler.bind(this, 'Flutter')}
          changed={this.nameChangedHandler}
        >
          My Hobbies: Coding
        </Person>
        <Person name={this.state.persons[2].name} />
      </div>
    );
  }
}

export default App;

```
In Person.js

```ruby
import React from 'react'

const person = (props) => {
    return (
        <div>
            <p onClick = {props.click}>I am a {props.name} and I am { Math.floor( Math.random()*20 ) } years Old</p>
            <p>{props.children}</p>
            <input type ='text' onChange={props.changed} value={props.name}/>
        </div>
    );
    
}

export default person;
```
# 3.17. Adding Styling with Stylesheets

- Create Person.css file

```ruby
.Person {
    width: 60%;
    margin: 16px auto;
    border: 1px solid #eee;
    box-shadow: 0 2px 3px #ccc;
    padding: 16px;
    text-align: center;
}
```
- Import that file in Person.js

```ruby
import React from 'react'
import './Person.css'

const person = (props) => {
    return (
        <div className = 'Person'>
            <p onClick = {props.click}>I am a {props.name} and I am { Math.floor( Math.random()*20 ) } years 		Old</p>
            <p>{props.children}</p>
            <input type ='text' onChange={props.changed} value={props.name}/>
        </div>
    );
    
}

export default person;
```
# 3.18. Working with Inline Styles

- In App.js

```ruby
import React, { Component } from "react";
import "./App.css";
import Person from "./Person/Person.js";

class App extends Component {
  state = {
    persons: [
      { name: "Gauthy", age: 22 },
      { name: "Gowthy", age: 24 },
      { name: "Gowtham", age: 26 }
    ]
  };

  SwitchNameHandler = (newName) => {
    // Don't do like this -> this.state.persons[0].name = 'Ram';
    this.setState({
      persons: [
        { name:  newName, age: 22 },
        { name:  newName, age: 24 },
        { name: "Gowtham", age: 26 }
      ]
    });
  };

  nameChangedHandler = ( event ) => {
    this.setState({
      persons: [
        { name:  'Android', age: 22 },
        { name:  event.target.value, age: 24 },
        { name: "Gowtham", age: 26 }
      ]
    });
  }

  render() {

    const style = {

      backgroundColor: 'white',
      font: 'inherit',
      border: '1x solid blue',
      padding: '8px',
      cursor: 'pointer'

    }

    return (
      <div className="App">
        <h1>Hello World</h1>
        <p>This is Working!!!</p>
        <button 
        style ={ style}
        onClick={this.SwitchNameHandler.bind(this, 'Android')}>Switch Name</button>
          {/* Alternative way but not the efficient one */}
          {/* <button onClick={() => this.SwitchNameHandler('Android')}>Switch Name</button> */}
        <Person
          name={this.state.persons[0].name}
          age={this.state.persons[0].age}
        />
        <Person
          name={this.state.persons[1].name}
          click={this.SwitchNameHandler.bind(this, 'Flutter')}
          changed={this.nameChangedHandler}
        >
          My Hobbies: Coding
        </Person>
        <Person name={this.state.persons[2].name} />
      </div>
    );
  }
}

export default App;
```

