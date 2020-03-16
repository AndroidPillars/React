
# 2.1. Next Generation JavaScript

# 2.1.1. let and const

- Before ES6 the only variable used in JavaScript is var.
```ruby
var myName = 'Android';
console.log(myName);

myName = 'iOS';
console.log(myName);
```
- In ES6 the introduced, let and const are different ways of creating variables.
- let -> variables values.
```ruby
let myName = 'Android';
console.log(myName);

myName = 'iOS';
console.log(myName);
```
- const -> constant values.
```ruby
const myName = 'Android';
console.log(myName);
```

# 2.1.2. Arrow Functions

```ruby
function myName(name){
  console.log(name);
}

myName('Android');
```
```ruby
const myName = (name) => {
  console.log(name);
}

myName('Android');
```

```ruby
const myName = name => {
  console.log(name);
}

myName('Android');
```
```ruby
const myName = () =>{
  console.log();
}

myName();
```
```ruby
const myName = (name, language) => {
  console.log(name, language);
}

myName('Android','Flutter');
```
```ruby
const multiply = (number) => {
 return  number*2;
}

console.log(multiply(2));
```
```ruby
const multiply = (number) => number*2;

console.log(multiply(10));
```

# 2.1.3. Exports and Imports(Modules)

- In JavaScript files we can import statement from another file so that the JavaScript files themselves know their dependencies.
- The default keyword uses when import some thing from that file it will always be our default export.
- In app.js

- default export
```ruby
import person from './person.js'
import prs from './person.js'
```

- Named Export
```ruby
import {smth} from './utility.js'
import {smth as Smth} from './utility.js'
import * as bundled from './utility.js'
```
__For Example,__

In person.js,
```ruby
const person= {
  name:'Android'
}

export default person
```
In utility.js,
```ruby
export const clean=()=>{...}
export const baseDate = 10;
```

In app.js,

```ruby
import person from './person.js'
import prs from './person.js'

import { baseData } from './utility.js'
import { clean } from './utility.js'
```

# 2.1.4. Classes

- Classes are essentially blueprints for Objects.
- A class is created using class keyword and class can have both properties and methods.
- Methods are simply function attached to the classes where properties are variables attached to the classes.
```ruby
class Person{
  myName = 'Android'
  call = () => {...}
}
```
- In some cases, we need a "blueprint" for creating many objects of the same "type".
- The way to create an "object type", is to use an object constructor function.
- Objects of the same type are created by calling the constructor function with the new keyword.
```ruby
const mPerson = new Person()
mPerson.call()
console.log(mPerson)
```
- Classes also supports inheritance, which means you have another class which you inherit from taking all its properties and methods and potentially adding new properties and menthods.
```ruby
class Person extends BaseClass
```
- In JavaScript, the thing called this is the object that "owns" the code.
- The value of this, when used in an object, is the object itself.
- In a constructor function this does not have a value. It is a substitute for the new object. 
- The value of this will become the new object when a new object is created.
- Note that this is not a variable. It is a keyword. You cannot change the value of this.
```ruby
class Human{
   constructor(){
    this.gender = 'Machine';
  }
  
  printGender(){
    console.log(this.gender);
  }
}

class Person extends Human{
  
  constructor(){
    super();
    this.name= 'Android';
    this.gender = 'Male';
  }
  
  myName(){
    console.log(this.name);
  }
}

const person = new Person();
person.myName();
person.printGender();
```
# 2.1.5. Classes, Properties and Methods

- Properties are like "variables attached to classes/ objects"

In ES6,
```ruby
constructor(){
    this.myProperty = 'value';
  }
```
In ES7,
```ruby
myProperty = 'value';
```
- You can assign a property directly inside your class with myProperty equals value.

- Methods are like 'functions attached to classes/objects

In ES6,
```ruby
myMethod(){...}
```
In ES7,
```ruby
myMethod = () => {...}
```
```ruby
class Human{
  
  gender = 'Machine';
  
  printGender = () => {
    console.log(this.gender);
  }
}

class Person extends Human{
  
    this.name= 'Android';
    this.gender = 'Male';
  
  myName = () => {
    console.log(this.name);
  }
}

const person = new Person();
person.myName();
person.printGender();
```

# 2.1.6. The Spread and Rest Operator

- ... only three dots
- Spread -> Used to split up array elements OR object properties.
```ruby
const newArray = [...oldArray, 1, 2]
const newObject = {...oldObject, newProp: 5}
```
- Rest -> Used to merge a list of functions arguements in to an array
```ruby
function sortArgs(...args){
  return args.sort()
}
```
```ruby
const numbers = [1,2,3];
const newNumbers = [...numbers, 4];

console.log(newNumbers);
```
```ruby
const person = {
  name: 'Android'
};

const newPerson = {
  ...person,
  age: 10
}

console.log(newPerson)
```
```ruby
const filter = (...args) => {
  return args.filter(el => el === 1);
}


console.log(filter(1,2,3))
```
# 2.1.7. Reference and Primitive Type Refresher

```ruby
const number = 1;
const number2 = number;

console.log(number)
```
- The number2 has been copied from number
- So numbers, Strings, booleans, these are called primitive types because whenever you reassign or you store a variable in other variable. It will copy the value, objects and arrays are reference types.
```ruby
const person = {
  name: 'Android'
}

const secondPerson = person;
console.log(secondPerson)
```
```ruby
const person = {
  name: 'Android'
};

const secondPerson = {
  ...person
};

person.name = 'Flutter'

console.log(secondPerson)
```

# 2.1.8. Refreshing Array Functions

```ruby
const numbers = [1, 2, 3];

const doubleNumArray = numbers.map((num) => {
  return num * 2;
});

console.log(numbers);
console.log(doubleNumArray);
```
# 2.1.9. Destructuring

- Destructuring allows you to easily extract array elements or object properties and store them in variables.
- In Spread -> It takes out all elements all properties and distribute them in a new array or object or wherever we are using it.
- Destructuring allows you to pull out single elements or properties and store them in variables for arrays and Objects.
- For Array Destructuring
```ruby
[a,b] = ['Hello','Android']
console.log(a)
console.log(b)
```
- For Object Destructuring
```ruby
{name}={name:'Android',age:20}
console.log(name)
console.log(age)
```
```ruby
const numbers = [1,2,3];
[num1,num2] = numbers;

console.log(num1,num2);
```

# 2.1.10. Reference and Primitive Type Refresher
```ruby
const number = 1;
const number2 = number;

console.log(number)
```
- The number2 has been copied from number
- So numbers, Strings, booleans, these are called primitive types because whenever you reassign or you store a variable in other variable. It will copy the value, objects and arrays are reference types.
```ruby
const person = {
  name: 'Android'
}

const secondPerson = person;
console.log(secondPerson)


const person = {
  name: 'Android'
};

const secondPerson = {
  ...person
};

person.name = 'Flutter'

console.log(secondPerson)
```

# 2.1.11. Refreshing Array Functions

```ruby
const numbers = [1, 2, 3];

const doubleNumArray = numbers.map((num) => {
  return num * 2;
});

console.log(numbers);
console.log(doubleNumArray);
```

# 2.1.12. Tools References

- https://jsbin.com/?html,output

