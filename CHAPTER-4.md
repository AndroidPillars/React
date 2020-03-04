# Working with Lists and Conditionals

# Rendering Content Conditionally

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
    ],
    OtherState: 'Some Other Value',
    showPersons: false
  };

  SwitchNameHandler = newName => {
    this.setState({
      persons: [
        { name: newName, age: 22 },
        { name: newName, age: 24 },
        { name: "Gowtham", age: 26 }
      ]
    });
  };

  nameChangedHandler = event => {
    this.setState({
      persons: [
        { name: "Android", age: 22 },
        { name: event.target.value, age: 24 },
        { name: "Gowtham", age: 26 }
      ]
    });
  };

  togglePersonalHandler = () => {

      const doesShow = this.state.showPersons;
      this.setState({
        showPersons: !doesShow
      })

  }

  render() {
    const style = {
      backgroundColor: "white",
      font: "inherit",
      border: "1x solid blue",
      padding: "8px",
      cursor: "pointer"
    };

    return (
      <div className="App">
        <h1>Hello World</h1>
        <p>This is Working!!!</p>
        <button
          style={style}
          onClick = {this.togglePersonalHandler}
        >
        Toggle Persons
        </button>
        { this.state.showPersons ? 
          <div>
          <Person
            name={this.state.persons[0].name}
            age={this.state.persons[0].age}
          />
          <Person
            name={this.state.persons[1].name}
            click={this.SwitchNameHandler.bind(this, "Flutter")}
            changed={this.nameChangedHandler}
          >
            My Hobbies: Coding
          </Person>
          <Person name={this.state.persons[2].name} />
        </div> : null
        }
      </div>
    );
  }
}

export default App;
```
- In Person.css file

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
- In Person.js

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

# Handling Dynamic Content The JavaScript Way

In App.js

```ruby
import React, { Component } from "react";
import "./App.css";
import Person from "./Person/Person.js";
import person from "./Person/Person.js";

class App extends Component {
  state = {
    persons: [
      { name: "Gauthy", age: 22 },
      { name: "Gowthy", age: 24 },
      { name: "Gowtham", age: 26 }
    ],
    OtherState: 'Some Other Value',
    showPersons: false
  };

  SwitchNameHandler = newName => {
    this.setState({
      persons: [
        { name: newName, age: 22 },
        { name: newName, age: 24 },
        { name: "Gowtham", age: 26 }
      ]
    });
  };

  nameChangedHandler = event => {
    this.setState({
      persons: [
        { name: "Android", age: 22 },
        { name: event.target.value, age: 24 },
        { name: "Gowtham", age: 26 }
      ]
    });
  };

  togglePersonalHandler = () => {

      const doesShow = this.state.showPersons;
      this.setState({
        showPersons: !doesShow
      })

  }

  render() {
    const style = {
      backgroundColor: "white",
      font: "inherit",
      border: "1x solid blue",
      padding: "8px",
      cursor: "pointer"
    };

    let persons = null;

    if(this.state.showPersons){
      persons = (
        <div>
        <Person
          name={this.state.persons[0].name}
          age={this.state.persons[0].age}
        />
        <Person
          name={this.state.persons[1].name}
          click={this.SwitchNameHandler.bind(this, "Flutter")}
          changed={this.nameChangedHandler}
        >
          My Hobbies: Coding
        </Person>
        <Person name={this.state.persons[2].name} />
      </div> 
      );
    }

    return (
      <div className="App">
        <h1>Hello World</h1>
        <p>This is Working!!!</p>
        <button
          style={style}
          onClick = {this.togglePersonalHandler}
        >
        Toggle Persons
        </button>
        {persons}
      </div>
    );
  }
}

export default App;
```
# Outputting Lists

```ruby
import React, { Component } from "react";
import "./App.css";
import Person from "./Person/Person.js";
import person from "./Person/Person.js";

class App extends Component {
  state = {
    persons: [
      { name: "Gauthy", age: 22 },
      { name: "Gowthy", age: 24 },
      { name: "Gowtham", age: 26 }
    ],
    OtherState: "Some Other Value",
    showPersons: false
  };

  SwitchNameHandler = newName => {
    this.setState({
      persons: [
        { name: newName, age: 22 },
        { name: newName, age: 24 },
        { name: "Gowtham", age: 26 }
      ]
    });
  };

  nameChangedHandler = event => {
    this.setState({
      persons: [
        { name: "Android", age: 22 },
        { name: event.target.value, age: 24 },
        { name: "Gowtham", age: 26 }
      ]
    });
  };

  togglePersonalHandler = () => {
    const doesShow = this.state.showPersons;
    this.setState({
      showPersons: !doesShow
    });
  };

  render() {
    const style = {
      backgroundColor: "white",
      font: "inherit",
      border: "1x solid blue",
      padding: "8px",
      cursor: "pointer"
    };

    let persons = null;

    if (this.state.showPersons) {
      persons = (
        <div>
          {this.state.persons.map(person => {
            return <Person name={person.name} age={person.age} />;
          })}
        </div>
      );
    }

    return (
      <div className="App">
        <h1>Hello World</h1>
        <p>This is Working!!!</p>
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
