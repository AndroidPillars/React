# 1.1. React

- React is a open-source frontend JavaScript library front-end JavaScript library developed by Facebook in 2011.
- It follows the component based approach which helps in building reusable UI components.
- It is used for developing complex and interactive web and mobile UI.

# 1.2. Why React

- React helps us with a problem we'll ecounter with normal in JavScript, the UI state becomes difficult to manage.
- In Bigger JavaScript applications, you have to manually target elememts in your DOM and if you then change the structure of your HTML code, changes are you will need to change the way you targetted your elements because you used query selector.
- Even if you use jQuery, traversing the DOM is easier, but it's still always something you have to keep in mind.
- IF you've get more complex web apps where you dynamically add and remove elements, this quickly can become cumbersome.
- But React help us by making the whole UI state management a non-issue.
- It allows us to focus on our business logic instead of keeping our application from exploding.
- It is highly-efficient and fast.
- React features a huge ecosystem and an extremely-active community which means that there is a great chance that for a given problem you face.

# 1.3. React Alternatives

- Angular and Vue.

# 1.4. Two Kinds of Applications

- Single Page Applications

- A single-page application is an application that works inside a browser and does not require page reloading during use.
- In single-page applications, our page is built up with components and every components is a React Component. 
- The entire page is also managed by a root react component which is execlusively under React's control.
- Example: Gmail, Google Maps, Trello, Facebook or GitHub.

# 1.4.1. Pros of the Single-Page Application

- Fast and responsive

Since single-page applications don’t update the entire page but only required content, they significantly improve a website’s speed. Most resources (HTML/CSS/Scripts) are only loaded once throughout the lifespan of an application. Only data is transmitted back and forth. This is a great advantage, and according to Google research, if a page takes more than 200 milliseconds to load it can have a potentially high impact on business and sales.

- Caching capabilities

A single-page app can cache any local data effectively. An SPA sends only one request to a server and then stores all the data it receives. Then it can use this data and work even offline. If a user has poor connectivity, local data can be synchronized with the server when the connection allows.

- Linear user experience

SPAs provide users with a simple linear experience. These web apps – like Saucony, for example – contain a clear beginning, middle, and end. The Saucony web app provides an excellent interactive experience using parallax scrolling and amazing transitions and effects to present the complete customer journey.

- Debugging with Chrome

It’s easy to debug an SPA with Chrome since such apps are developed on frameworks like AngularJS Batarang and React developer tools. These frameworks have their own Chrome developer tools that make debugging much easier than with MPAs. In addition, SPAs allow you to monitor network operations and investigate page elements and data associated with them.

# 1.4.2. Cons of the Single-Page Application

- SEO optimization

Some people are of the opinion that SPAs provide poor SEO optimization. This is because single-page apps operate on JavaScript and download data on request from the client side. The URL doesn’t really change and different pages don’t have their unique URL addresses. It’s hard to optimize these websites for search engines since most pages can’t be scanned by search bots.

Recently, Google launched a new scheme to increase single-page app SEO optimization. Google now indexes dynamic pages. But for this, developers need to make sure that their JavaScript files can be indexed by Google (because Google runs them in their crawler). They also need to verify that a website uses HTML5 mode in the URL scheme.

- Browser history

An SPA doesn’t save visitors’ jumps between states. This means that when users click the back button, they won’t go back. A browser only takes users to the previous page, not to the previous state in an app.

To solve this problem, there’s an HTML5 History API with which developers can equip their SPA frameworks. The History API offers developers access to browser navigation history via JavaScript.

- Security issues

Single-page apps are less immune to cross-site scripting (XSS) attacks than are multi-page apps. Using XSS, hackers can inject client-side scripts into web applications.

One security issue is the exposure of sensitive data. If developers aren’t careful about what data is contained in the initial page load, they can easily send data that shouldn’t be exposed to all users. The whole of an SPA isn’t generally visible in the browser, which can provide a false sense of security.

One more reason that SPAs can be insecure is missing access control at the functional level. Since developers move features and logic off the server and out to the client, it’s really easy to provide a client with access to functions that they shouldn’t be permitted to use.

# 1.4.3. When to use an SPA

- Single-page web applications fit perfectly for building dynamic platforms with small data volumes. 
- Furthermore, a single-page app is ideal as a base for future mobile app development. 
- The main drawback of this development approach is poor SEO optimization. 
- But this architecture is excellent for SaaS platforms, social networks, and closed communities where search engine optimization doesn’t matter. 
- If a project requires effective SEO, on the other hand, then you should use a multi-page application.


- Multi Page Applications

- Multiple-page applications work in a “traditional” way. 
- Every change eg. display the data or submit data back to server requests rendering a new page from the server in the browser. 
- In Multiple-page application, we also split our app in to theoretical components, but actually a lot of page is just going to be normal HTML and CSS code and some widgets we dump in, like an image gallery or something like that is managed by React.
- So, the entire page is not under React's control.
- Example: ebay and Amazon

# 1.4.4. Pros of the Multiple-Page Application

- SEO

SEO is better on MPAs since the architecture is native to search engine crawlers. Such apps provide better control over SEO thanks to multiple pages and changing content. Moreover, developers can add meta tags to every page. An MPA gives a better chance of ranking for different keywords since an app can be optimized for one keyword per page.

- Unlimited scalability

MPAs allow you to create new content and place it on new pages. Multi-page apps can include as much information about products or services as required, with no page limitations. Single-page applications don’t allow a lot of features on one page, which can lead to longer loading times. Therefore, when company needs more features, they decide to use multi-page applications.

-Insights from Google Analytics

MPAs can provide lots of analytics with valuable information on how a website is performing: which features are working and which aren’t. With a single-page app, the only useful information you can collect is who visitors are and for how long they stay on the site.

# 1.4.5. Cons of the Multiple-Page application

- Slow speed and performance

With multi-page apps, a server needs to reload most resources such as HTML, CSS, and scripts with every interaction. When loading another page, the browser completely reloads page data and downloads all resources again, even components that are repeated throughout all pages (e.g. the header and footer). This affects speed and performance.

- More time for development

Compared to SPAs, MPAs take longer to develop. In most cases, developers have to code the backend from scratch. There are also difficulties in frontend and backend separation since they interact very closely with each other. Developers need to use frameworks for both the frontend or backend. This results in longer app development.

- Maintenance and updates

Maintaining and updating multiple pages can be a chore, and things only get worse the larger a website becomes. In addition, maintaining security may be problematic because developers need to secure each separate page. Single-page apps allow developers to just secure data endpoints.

# 1.4.6. When to use an MPA
- A multi-page application is appropriate for large companies with a broad range of products or services that require lots of features and multiple menus. 
- An MPA is more suitable for online stores, business sites, catalogs, and marketplaces. 
- Companies running these sites probably also have diverse user bases. 
- To put it simply, if you have a lot of content and features to include on your website or if you are reselling multiple products and services, then an MPA would be a good choice.

# 1.5. Outline

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

# 1.6. Sample Application

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

- where, ReactDOM.render() -> This method allows us to render a JavaScript function as a component to the real DOM and that treat it as a component part is exactly what React cares about
