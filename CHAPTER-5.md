# Styling React Components & Elements

# Setting Styles Dynamically

In App.js

```ruby
import React, { Component } from "react";
import "./App.css";
import Person from "./Person/Person.js";
import person from "./Person/Person.js";

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
    const style = {
      backgroundColor: "green",
      color: "white",
      font: "inherit",
      border: "1x solid blue",
      padding: "8px",
      cursor: "pointer"
    };

    let persons = null;

    if (this.state.showPersons) {
      persons = (
        <div>
          {this.state.persons.map((person, index) => {
            return (
              <Person
                click={() => this.deletePersonHandler(index)}
                event
                name={person.name}
                age={person.age}
                key={person.id}
                changed={event => this.nameChangedHandler(event, person.id)}
              />
            );
          })}
        </div>
      );
      style.backgroundColor = "blue";
    }

    let classes = ['red', 'bold'].join(' ');

    return (
      <div className="App">
        <h1>Hello World</h1>
        <p className={classes}>This is Working!!!</p>
        <button style={style} onClick={this.togglePersonalHandler}>
          Toggle Persons
        </button>
        {persons}
      </div>
    );
  }
}

export default App;
```
In App.css

```ruby
.App {
  text-align: center;
}

.red{
  color: red;
}

.bold{
  font-weight: bold;
}
```

# Setting Class Names Dynamically

In App.js

```ruby
import React, { Component } from "react";
import "./App.css";
import Person from "./Person/Person.js";
import person from "./Person/Person.js";

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
    const style = {
      backgroundColor: "green",
      color: "white",
      font: "inherit",
      border: "1x solid blue",
      padding: "8px",
      cursor: "pointer"
    };

    let persons = null;

    if (this.state.showPersons) {
      persons = (
        <div>
          {this.state.persons.map((person, index) => {
            return (
              <Person
                click={() => this.deletePersonHandler(index)}
                event
                name={person.name}
                age={person.age}
                key={person.id}
                changed={event => this.nameChangedHandler(event, person.id)}
              />
            );
          })}
        </div>
      );
      style.backgroundColor = "blue";
    }

    const classes = [];
    if (this.state.persons.length <= 2) {
      classes.push("red"); // classes = ['red']
    }

    if(this.state.persons.length <= 1){
      classes.push("bold"); // classes = ['red', 'bold']
    }

    return (
      <div className="App">
        <h1>Hello World</h1>
        <p className={classes.join(' ')}>This is Working!!!</p>
        <button style={style} onClick={this.togglePersonalHandler}>
          Toggle Persons
        </button>
        {persons}
      </div>
    );
  }
}

export default App;
```

# Adding and Using Radium

- Open Terminal

```ruby
npm install --save radium
```
- Radium is a popular package for React which allows us to use inline styles with pseudo selectors and media queries.
- You can't style a pseudo-class on a particular element alone, in the same way that you can't have a pseudo-class in an inline style.

In App.js

```ruby
import React, { Component } from "react";
import "./App.css";
import Radium from 'radium';
import Person from "./Person/Person.js";


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
    const style = {
      backgroundColor: "green",
      color: "white",
      font: "inherit",
      border: "1x solid blue",
      padding: "8px",
      cursor: "pointer",
      ':hover': {
        backgroundColor: 'green',
        color: 'black'
      }
    };

    let persons = null;

    if (this.state.showPersons) {
      persons = (
        <div>
          {this.state.persons.map((person, index) => {
            return (
              <Person
                click={() => this.deletePersonHandler(index)}
                event
                name={person.name}
                age={person.age}
                key={person.id}
                changed={event => this.nameChangedHandler(event, person.id)}
              />
            );
          })}
        </div>
      );
      style.backgroundColor = "blue";
      style[':hover'] = {
        backgroundColor: 'green',
        color: 'black'
      }
    }

    const classes = [];
    if (this.state.persons.length <= 2) {
      classes.push("red"); // classes = ['red']
    }

    if(this.state.persons.length <= 1){
      classes.push("bold"); // classes = ['red', 'bold']
    }

    return (
      <div className="App">
        <h1>Hello World</h1>
        <p className={classes.join(' ')}>This is Working!!!</p>
        <button style={style} onClick={this.togglePersonalHandler}>
          Toggle Persons
        </button>
        {persons}
      </div>
    );
  }
}

export default Radium(App);

```

In Person.js

```ruby
import React from 'react'
import Radium from 'radium';
import './Person.css'

const person = (props) => {
    return (
        <div className = 'Person'>
            <p onClick = {props.click}>I am a {props.name} and I am { Math.floor( Math.random()*20 ) } years Old</p>
            <p>{props.children}</p>
            <input type ='text' onChange={props.changed} value={props.name}/>
        </div>
    );
    
}

export default Radium(person);
```

# Using Radium for Media Queries
