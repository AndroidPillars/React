# 5.1. Styling React Components & Elements

# 5.1.1. Setting Styles Dynamically

__In App.js__

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
__In App.css__

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

# 5.1.2. Setting Class Names Dynamically

__In App.js__

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

# 5.1.3. Adding and Using Radium

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

# 5.1.4. Using Radium for Media Queries

In App.js

```ruby
import React, { Component } from "react";
import "./App.css";
import Radium, { StyleRoot } from "radium";
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
      ":hover": {
        backgroundColor: "green",
        color: "black"
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
      style[":hover"] = {
        backgroundColor: "green",
        color: "black"
      };
    }

    const classes = [];
    if (this.state.persons.length <= 2) {
      classes.push("red"); // classes = ['red']
    }

    if (this.state.persons.length <= 1) {
      classes.push("bold"); // classes = ['red', 'bold']
    }

    return (
      <StyleRoot>
        <div className="App">
          <h1>Hello World</h1>
          <p className={classes.join(" ")}>This is Working!!!</p>
          <button style={style} onClick={this.togglePersonalHandler}>
            Toggle Persons
          </button>
          {persons}
        </div>
      </StyleRoot>
    );
  }
}

export default Radium(App);
```
In Person.css

```ruby
.Person {
    width: 60%;
    margin: 16px auto;
    border: 1px solid #eee;
    box-shadow: 0 2px 3px #ccc;
    padding: 16px;
    text-align: center;
}

/* @media(min-width: 500px){
    .Person{
        width: 450px;
    }
} */
```

In Person.js

```ruby
import React from "react";
import Radium from "radium";
import "./Person.css";

const person = (props) => {
  const style = {
    "@media(min-width: 500px)": {
      width: "450 px"
    }
  };

  return (
      <div className="Person" style={style}>
        <p onClick={props.click}>
          I am a {props.name} and I am {Math.floor(Math.random() * 20)} years
          Old
        </p>
        <p>{props.children}</p>
        <input type="text" onChange={props.changed} value={props.name} />
      </div>
  );
};

export default Radium(person);
```

# Introducing Styled Components

- Visit https://styled-components.com/
- Open CmdPrompt -> For installing the plugin
```ruby
npm install --save styled-components
```

In App.js

```ruby
import React, { Component } from "react";
import styled from "styled-components";
import "./App.css";
import Person from "./Person/Person.js";

const StyledButton = styled.button`
      
      background-color: green;
      color: white;
      font: inherit;
      border: 1x solid blue;
      padding: "8px";
      cursor: pointer;

      &:hover {
        background-color: green;
        color: black;
      }
`;

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
    }

    const classes = [];
    if (this.state.persons.length <= 2) {
      classes.push("red"); // classes = ['red']
    }

    if (this.state.persons.length <= 1) {
      classes.push("bold"); // classes = ['red', 'bold']
    }

    return (
        <div className="App">
          <h1>Hello World</h1>
          <p className={classes.join(" ")}>This is Working!!!</p>
          <StyledButton onClick={this.togglePersonalHandler}>
            Toggle Persons
          </StyledButton>
          {persons}
        </div>
    );
  }
}

export default App;

```

In Person.js

```ruby
import React from "react";
import "./Person.css";
import styled from "styled-components";

const StyledDiv = styled.div`
    width: 60%;
    margin: 16px auto;
    border: 1px solid #eee;
    box-shadow: 0 2px 3px #ccc;
    padding: 16px;
    text-align: center;

    @media(min-width: 500px){
    .Person{
    width: 450px;
    }
`;

const person = props => {
  const style = {
    "@media(min-width: 500px)": {
      width: "450 px"
    }
  };

  return (
    <StyledDiv>
      <p onClick={props.click}>
        I am a {props.name} and I am {Math.floor(Math.random() * 20)} years Old
      </p>
      <p>{props.children}</p>
      <input type="text" onChange={props.changed} value={props.name} />
    </StyledDiv>
  );
};

export default person;
```
In Person.css

```ruby
/* .Person {
    width: 60%;
    margin: 16px auto;
    border: 1px solid #eee;
    box-shadow: 0 2px 3px #ccc;
    padding: 16px;
    text-align: center;
} */

@media(min-width: 500px){
    .Person{
        width: 450px;
    }
}
```

# Styled Components and Dynamic Styles

In App.js

```ruby
import React, { Component } from "react";
import styled from "styled-components";
import "./App.css";
import Person from "./Person/Person.js";

const StyledButton = styled.button`
      
      background-color: ${props => props.alt ? 'red' : 'green'};
      color: white;
      font: inherit;
      border: 1x solid blue;
      padding: "8px";
      cursor: pointer;

      &:hover {
        background-color: ${props => props.alt ? 'red' : 'green'};
        color: black;
      }
`;

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
    }

    const classes = [];
    if (this.state.persons.length <= 2) {
      classes.push("red"); // classes = ['red']
    }

    if (this.state.persons.length <= 1) {
      classes.push("bold"); // classes = ['red', 'bold']
    }

    return (
        <div className="App">
          <h1>Hello World</h1>
          <p className={classes.join(" ")}>This is Working!!!</p>
          <StyledButton alt={this.state.showPersons} onClick={this.togglePersonalHandler}>
            Toggle Persons
          </StyledButton>
          {persons}
        </div>
    );
  }
}

export default App;
```
# Working with CSS Modules

-  Open CmdPrompt
```ruby
npm run eject
```
- Open cofig folder in project module -> webpack.config.dev.js -> Find test: /\.css$/ -> Options -> Add the below lines

```ruby
options: {
     importLoaders: 1,
     modules: true,
     localIdentName: '[name]__[local]__[hash:base64:5]'
    },
```
where, 
modules: true -> This enables the CSS module Features and localIdentName -> This will used by this features to dynamically generate unique CSS class names at the end.

- Similary -> webpack.config.prod.js also

If you get Error,

npm ERR! errno 1
npm ERR! protest-app@0.1.0 start: `react-scripts start`
npm ERR! Exit status 1

```ruby
npm install -g react-scripts after that run npm run eject, or you can use npx instead of npm
```

- Then restart the Visual Studio Code.

In App.js

```ruby
import React, { Component } from "react";

import classes from './App.css';
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
    let persons = null;
    let btnClass = [classes.Button];

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

      btnClass.push(classes.Red);
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
          <button className = {btnClass.join(' ')} onClick={this.togglePersonalHandler}>
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

.Button{
  background-color: green ;
  color: white;
  font: inherit;
  border: 1x solid blue;
  padding: "8px";
  cursor: pointer; 
}

.Button:hover{
  background-color: lightseagreen;
  color: black;
}

.Button.Red{
  background-color: red;
}

.Button.Red:hover{
  background-color: salmon;
}

```

__Alternative Way on the Above Code,__

In App.js

```ruby
import React, { Component } from "react";

import classes from './App.css';
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
    let persons = null;
    let btnClass = '';

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
          <button className = {btnClass} onClick={this.togglePersonalHandler}>
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

.App button{
  background-color: green ;
  color: white;
  font: inherit;
  border: 1x solid blue;
  padding: "8px";
  cursor: pointer; 
}

.App button:hover{
  background-color: lightseagreen;
  color: black;
}

.App button.Red{
  background-color: red;
}

.App button.Red:hover{
  background-color: salmon;
}
```

# CSS Modules and Media Queries

In Person.js

```ruby
import React from "react";
import classes from"./Person.css"; // If we are using ReactScripts 2.X or higher we need to use ./Person.module.css and rename file name also


const person = props => {
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
In Person.css

```ruby
 .Person {
    width: 60%;
    margin: 16px auto;
    border: 1px solid #eee;
    box-shadow: 0 2px 3px #ccc;
    padding: 16px;
    text-align: center;
} 

@media(min-width: 500px){
    .Person{
        width: 450px;
    }
}
```
