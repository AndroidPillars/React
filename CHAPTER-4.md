# 4.1. Working with Lists and Conditionals

# 4.1.1. Rendering Content Conditionally

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
In Person.css file

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
In Person.js

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

# 4.1.2 Handling Dynamic Content The JavaScript Way

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
# 4.1.3. Outputting Lists

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
# 4.1.4 List and State with Delete

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
    OtherState: "Some Other Value",
    showPersons: false
  };

  deletePersonHandler = (personIndex) => {
    const persons = this.state.persons;
    persons.splice(personIndex, 1);
    this.setState({persons: persons});
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
          {this.state.persons.map((person, index) => {
            return <Person 
            name = {person.name} 
            age = {person.age}
            click = {() => this.deletePersonHandler(index)} />;
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

# 4.1.5. Updating State Immutably

In App.js

```ruby
deletePersonHandler = (personIndex) => {
    // const persons = this.state.persons.slice;
    const persons = [...this.state.persons] // Spread Operator
    persons.splice(personIndex, 1);
    this.setState({persons: persons});
  };
```

# 4.1.6. Lists & Keys

In App.js

```ruby
import React, { Component } from "react";
import "./App.css";
import Person from "./Person/Person.js";
import person from "./Person/Person.js";

class App extends Component {
  state = {
    persons: [
      { id: '1wd', name: "Gauthy", age: 22 },
      { id: '2ds', name: "Gowthy", age: 24 },
      { id: '3dd', name: "Gowtham", age: 26 }
    ],
    OtherState: "Some Other Value",
    showPersons: false
  };

  deletePersonHandler = (personIndex) => {
    // const persons = this.state.persons.slice;
    const persons = [...this.state.persons] // Spread Operator
    persons.splice(personIndex, 1);
    this.setState({persons: persons});
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
          {this.state.persons.map((person, index) => {
            return <Person 
            click = {() => this.deletePersonHandler(index)}
            name = {person.name} 
            age = {person.age}
            key = {person.id}
            />;
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

# 4.1.7. Flexible Lists

In App.js

```ruby
import React, { Component } from "react";
import "./App.css";
import Person from "./Person/Person.js";
import person from "./Person/Person.js";

class App extends Component {
  state = {
    persons: [
      { id: '1wd', name: "Gauthy", age: 22 },
      { id: '2ds', name: "Gowthy", age: 24 },
      { id: '3dd', name: "Gowtham", age: 26 }
    ],
    OtherState: "Some Other Value",
    showPersons: false
  };

  deletePersonHandler = (personIndex) => {
    // const persons = this.state.persons.slice;
    const persons = [...this.state.persons] // Spread Operator
    persons.splice(personIndex, 1);
    this.setState({persons: persons});
  };

  nameChangedHandler = (event, id) => {

    const personIndex = this.state.persons.findIndex( p => {
      return p.id === id;
    })

    const person = { ...this.state.persons[personIndex] };

     // const person = Object.assign({}, this.state.persons[personIndex]); -- alternative way

     person.name = event.target.value;

     const persons = [...this.state.persons]
     persons[personIndex] = person;

    this.setState({persons: persons});
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
          {this.state.persons.map((person, index) => {
            return <Person 
            click = {() => this.deletePersonHandler(index)}event
            name = {person.name} 
            age = {person.age}
            key = {person.id}
            changed = { (event) => this.nameChangedHandler(event, person.id)}
            />;
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
