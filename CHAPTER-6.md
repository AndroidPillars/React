# 6.1. Debugging React Apps

- Debugging allows you to easily find sources of errors in your code, but also teaches you about the inner working of the language thus preventing you from making the same error in the future.
- By Using browser’s developer tools -> pressing F12 or right clicking and selecting “Inspect” -> See the errors in “Console”.
- By Using chrome developer tools -> By Clicking “>>” -> Sources -> Page -> top -> localhost:3000 -> static/js -> project path -> src ->
where you can find the source -> By placing the debug point we can find the error by checking the code line by line.
- Chrome -> Extension -> React Developer Tools -> https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi/related

# 6.2. Using Error Boundaries(React 16+)

- Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, and does something worth while with it like displaying a fallback interface instead of the component tree that crashed or logging the exact error. 
- Error boundaries catch errors during rendering, in lifecycle methods, and in constructors of the whole tree below them, unmount the component tree while maintaining the usual workings and renderings of the rest of the React application.

__In App.js__

```ruby
import React, { Component } from "react";

import classes from "./App.css";
import Person from "./Person/Person.js";
import ErrorBoundary from "./ErrorBoundary/ErrorBoundary";

class App extends Component {
  state = {
    persons: [
      { id: "1wd", name: "Android", age: 22 },
      { id: "2ds", name: "Flutter", age: 24 },
      { id: "3dd", name: "React", age: 26 }
    ],
    OtherState: "Some Other Value",
    showPersons: false
  };

  deletePersonHandler = personIndex => {
    // const persons = this.state.persons.slice;
    const persons = [...this.state.persons]; // Spread Operator
    persons.splice(personIndex, 1);
    this.setState({ persons: persons });
  };

  nameChangedHandler = (event, id) => {
    const personIndex = this.state.persons.findIndex(p => {
      return p.id === id;
    });

    const person = { ...this.state.persons[personIndex] };

    // const person = Object.assign({}, this.state.persons[personIndex]); -- alternative way

    person.name = event.target.value;

    const persons = [...this.state.persons];
    persons[personIndex] = person;

    this.setState({ persons: persons });
  };

  togglePersonalHandler = () => {
    const doesShow = this.state.showPersons;
    this.setState({
      showPersons: !doesShow
    });
  };

  render() {
    let persons = null;
    let btnClass = "";

    if (this.state.showPersons) {
      persons = (
        <div>
          {this.state.persons.map((person, index) => {
            return (
              <ErrorBoundary key={person.id}>
                <Person
                  click={() => this.deletePersonHandler(index)}
                  event
                  name={person.name}
                  age={person.age}
                  changed={event => this.nameChangedHandler(event, person.id)}
                />
              </ErrorBoundary>
            );
          })}
        </div>
      );

      btnClass = classes.Red;
    }

    const assignedClasses = [];
    if (this.state.persons.length <= 2) {
      assignedClasses.push(classes.red); // assignedClasses = ['red']
    }

    if (this.state.persons.length <= 1) {
      assignedClasses.push(classes.bold); // assignedClasses = ['red', 'bold']
    }

    return (
      <div className={classes.App}>
        <h1>Hello World</h1>
        <p className={assignedClasses.join(" ")}>This is Working!!!</p>
        <button className={btnClass} onClick={this.togglePersonalHandler}>
          Toggle Persons
        </button>
        {persons}
      </div>
    );
  }
}

export default App;
```

__In Person.js__

```ruby
import React from "react";
import classes from "./Person.css";

const person = props => {
  const rnd = Math.random();
  if (rnd > 0.7) {
    throw new Error("Some thing went wrong");
  }
  return (
    <div className={classes.Person}>
      <p onClick={props.click}>
        I am a {props.name} and I am {Math.floor(Math.random() * 20)} years Old
      </p>
      <p>{props.children}</p>
      <input type="text" onChange={props.changed} value={props.name} />
    </div>
  );
};

export default person;
```
__Create the folder ErrorBoundary -> with the file name ErrorBoundary.js__

```ruby
import React, { Component } from "react";

class ErrorBoundary extends Component {
  state = {
    hasError: false,
    errorMessage: ""
  };

  componentDidCatch = (error, info) => {
    this.setState({ hasError: true, errorMessage: error });
  };

  render() {
    if (this.state.hasError) {
      return <h1>{this.state.errorMessage}</h1>;
    } else {
      return this.props.children;
    }
  }
}

export default ErrorBoundary;
```
