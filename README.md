# React

- React is a JavaScript Library for building User Interfaces.
- It is about building JavaScript-driven apps.
- They don't run on the server.
- React apps run in the browser and this gives us a great advantage. 
- Things happen instantly since they happen in the user's browser.
- We don't have to wait for a server response to get a new page or to render something new.
- User Interfaces are bascially what the user sees and React is all about using components for building these.

# Why React

- React helps us with a problem we'll ecounter with normal in JavScript, the UI state becomes difficult to manage.
- In Bigger JavaScript applications, you have to manually target elememts in your DOM and if you then change the structure of your HTML code, changes are you will need to change the way you targetted your elements because you used query selector.
- Even if you use jQuery, traversing the DOM is easier, but it's still always something you have to keep in mind.
- IF you've get more complex web apps where you dynamically add and remove elements, this quickly can become cumbersome.
- But React help us by making the whole UI state management a non-issue.
- It allows us to focus on our business logic instead of keeping our application from exploding.
- It is highly-efficient and fast.
- React features a huge ecosystem and an extremely-active community which means that there is a great chance that for a given problem you face.

# React Alternatives

- Angular and Vue.

# Outline

- Getting Started 
- The Basics
- Debugging
- Styling Components
- Routing
- Http Requests
- Components Deep Dive
- Forms and Validation
- Redux
- Authentication
- Testing Introduction
- Deployment
- Animation, Next Steps and webpack

# Sample Application

- Visit, https://codepen.io/
- Settings -> Search react, react-dom and JavaScript Preprocessor -> Babel

HTML

```ruby
<div id='p1'></div>
<div class='technology'>
  <h1>Web Development</h1>
  <p>React</p>
</div>
```

CSS

```ruby
.technology{
  display: inline-block;
  margin: 10px;
  border: 1px solid #ccc;
  box-shadow: 0 2px 2px #ccc;
  width: 200px;
  padding:20px
}
```

JS

```ruby
function Technology(props){
  return(
    <div className='technology'>
      <h1>{props.development}</h1>
      <p>{props.language}</p>
    </div>
  );
}

ReactDOM.render(
<Technology 
  development='Andorid' 
  language = 'Flutter'/>,
document.querySelector('#p1'));
```

- where, ReactDOM.render(); -> This method allows us to render a JavaScript function as a component to the real DOM and that treat it as a component part is exactly what React cares about.

