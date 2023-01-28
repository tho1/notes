There are so many javascript libraries.  Doesn't mean to be a know it all.  Here are the ones I come across.


* PollyJS  - retry policy
* InversifyJS - dependency injection
* router
* Axios or Fetch
* Async - Redux, Trunk, Saga :  validation, API calls, error handling, trigger redux mutations, or trigger a notification 
* Class components vs Functional components: [Understanding Functional Components vs. Class Components in React](https://www.twilio.com/blog/react-choose-functional-components)
* React hooks connect()
* Redux async - for validation, checking and other
* 

### links

* https://jstutorial.medium.com/how-i-designed-an-animated-book-store-with-javascript-jquery-and-css-86251724ae91
* https://beforesemicolon.medium.com/50-javascript-best-practice-rules-to-write-better-code-86ce731311d7


### 
* https://github.com/Sathish2905/javascript_interview_questions
* https://github.com/rohan-paul/Awesome-JavaScript-Interviews
* https://github.com/InterviewMap/CS-Interview-Knowledge-Map
* https://github.com/MaximAbramchuck/awesome-interview-questions
* https://github.com/ganqqwerty/123-Essential-JavaScript-Interview-Questions
* https://github.com/sudheerj/javascript-interview-questions
* https://github.com/kennymkchan/interview-questions-in-javascript

### 
* https://frontendmasters.com/blog/vanilla-javascript-todomvc/  Plain old todomvc. debates on not using js framework. pros and cons.
* https://medium.com/devinder/react-virtual-dom-vs-real-dom-23749ff7adc9 Real vs Virtual DOM vs Shadow Dom

### Virtual DOM.
dirty checking - traverse the entire tree at regular interval. Expensive and slow
observable - components listen on events when there is update.  Fast.  
Virtual DOM is an abstraction of the real DOM.  light weight. recreated after every render.  Reconciliation does compare and sync the virtual dom to the read DOM. It uses diffing algorithm.  Updated real DOM is rendered again.


### event loop
* https://medium.com/front-end-weekly/javascript-event-loop-explained-4cd26af121d4

### design patterns
* https://www.patterns.dev/
* https://www.patterns.dev/resources/ Also contain patterns for TS, vue, angular.  Super useful.

### testing
* https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing

### debugging
```
console.log({name,age,gender});
console.log( "plain text, %ccolored text", "color:green; font size:15px" );
console.warn("watch out");
console.error("you got an error");
console.table(["apples", "oranges", "bananas"]);
```



## Node in general
* https://levelup.gitconnected.com/set-up-and-run-a-simple-node-server-project-38b403a3dc09 gentle intro to start a node project
* https://www.toptal.com/nodejs/top-10-common-nodejs-developer-mistakes

## node alternative
* deno next version of Node.js by Node founder
* https://github.com/superfly/flyjs flyJs specific for Edge application. The Fly JavaScript runtime

### Scaffolding 
There are many packages out there.  Webpack, Yeoman, Grunt, jsHint, Slush 
* http://www.codedigest.com/quick-start/13/what-is-gulp-how-to-use-gulp Gulp intro

### Lint checker
There are many.  JsHint, ESLint 
* https://medium.com/@sheldonled/from-jshint-to-eslint-8a0a135fa2bf
