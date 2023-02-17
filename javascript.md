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

### Official doc
* https://nodejs.org/docs/latest-v16.x/api/os.html#ostotalmem

### basic tutorial

* https://jstutorial.medium.com/how-i-designed-an-animated-book-store-with-javascript-jquery-and-css-86251724ae91
* https://beforesemicolon.medium.com/50-javascript-best-practice-rules-to-write-better-code-86ce731311d7
* https://websitesetup.org/bootstrap-tutorial-for-beginners/
* https://www.w3schools.com/react/default.asp

### In depth tutorial
* https://github.com/javascript-society/javascript-path 

### interview questions 
* https://github.com/Sathish2905/javascript_interview_questions
* https://github.com/rohan-paul/Awesome-JavaScript-Interviews
* https://github.com/InterviewMap/CS-Interview-Knowledge-Map
* https://github.com/MaximAbramchuck/awesome-interview-questions
* https://github.com/ganqqwerty/123-Essential-JavaScript-Interview-Questions
* https://github.com/sudheerj/javascript-interview-questions
* https://github.com/kennymkchan/interview-questions-in-javascript

### sample code
* https://frontendmasters.com/blog/vanilla-javascript-todomvc/  Plain old todomvc. debates on not using js framework. pros and cons.
* https://developerhowto.com/2018/12/29/build-a-rest-api-with-node-js-and-express-js/
* https://github.com/React-Avancado/boilerplate
* https://github.com/ant-design/ant-design

### Virtual DOM.
* https://medium.com/devinder/react-virtual-dom-vs-real-dom-23749ff7adc9 Real vs Virtual DOM vs Shadow Dom
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
* [How to debug Node JS Errors](https://dev.to/jay818/how-to-debug-node-js-errors-3j9i)


## node token
```
 git+https://oauth2:yourtoken@gitlab.com:6443/somegit
 git+https://<token-from-github>:x-oauth-basic@github.com/<user>/<GitRepo>.git
```

## Node in general
* https://levelup.gitconnected.com/set-up-and-run-a-simple-node-server-project-38b403a3dc09 gentle intro to start a node project
* https://www.toptal.com/nodejs/top-10-common-nodejs-developer-mistakes
* https://www.guru99.com/node-js-tutorial.html
* https://stackoverflow.com/questions/14415398/best-approach-to-design-a-rest-web-service-with-binary-data-to-be-consumed-from
* https://stackoverflow.com/questions/23210437/npm-install-private-github-repositories-by-dependency-in-package-json
* https://stackoverflow.com/questions/28728665/how-to-use-private-github-repo-as-npm-dependency?noredirect=1&lq=1
* https://stackoverflow.com/questions/23210437/npm-install-private-github-repositories-by-dependency-in-package-json
* https://stackoverflow.com/questions/17509669/how-to-install-an-npm-package-from-github-directly?rq=1
* https://stackoverflow.com/questions/27087483/how-to-resolve-git-pull-fatal-unable-to-access-https-github-com-empty
* https://github.com/goldbergyoni/nodebestpractices
* [Express routing with Sqlite](https://geshan.com.np/blog/2021/10/nodejs-sqlite/)
* [Express web framework from MDN](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs)
* https://stackoverflow.com/questions/50605219/difference-between-npx-and-npm

## Node setup
* https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-windows
* https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-beginners-tutorial
* https://heynode.com/tutorial/what-packagejson/
* https://heynode.com/tutorial/how-use-semantic-versioning-npm/
* [Node Hero – Node.js Project Structure Tutorial](https://blog.risingstack.com/node-hero-node-js-project-structure-tutorial/)

## node alternative
* [deno](https://deno.land/api)  Deno
* [flyjs](https://github.com/superfly/flyjs) flyJs specific for Edge application. The Fly JavaScript runtime

### Scaffolding in general
There are many packages out there.  Webpack, Yeoman, Grunt, jsHint, Slush 
* https://www.reddit.com/r/javascript/comments/262qw5/yeoman_vs_slush/


### Bootstrap
* https://websitesetup.org/bootstrap-tutorial-for-beginners/

### Yarn 

#### Gulp
* http://www.codedigest.com/quick-start/13/what-is-gulp-how-to-use-gulp Gulp intro
* https://medium.com/@horte/how-to-create-a-slush-generator-part-1-eafece6c1ca8
* https://mariusschulz.com/blog/introducing-the-gulp-iife-plugin GULP iife plugins
* https://css-tricks.com/gulp-for-beginners/ beginners and useful plugins
* https://nystudio107.com/blog/a-gulp-workflow-for-frontend-development-automation walkthough annotated.

#### Parcel
* https://benfrain.com/moving-from-gulp-to-parcel/

#### WebPack
* https://www.smashingmagazine.com/2017/02/a-detailed-introduction-to-webpack/
* https://ui.dev/webpack
* https://survivejs.com/webpack/introduction/

#### Grunt
* https://semaphoreci.com/community/tutorials/getting-started-with-grunt-js
* https://gruntjs.com/getting-started
* https://www.geeksforgeeks.org/introduction-to-grunt/
* https://www.webfx.com/blog/web-design/grunt-tutorial-01/

#### Yeoman
* https://flaviocopes.com/introduction-to-yeoman/
* https://frontendmasters.com/courses/workflows-and-tooling/yeoman-introduction/
* https://blog.techtalentsouth.com/an-intro-to-yeoman

#### Slush
* https://stackoverflow.com/questions/26322592/how-to-make-a-slush-generator
* https://medium.com/@horte/how-to-create-a-slush-generator-part-1-eafece6c1ca8
### Lint checker
There are many.  JsHint, ESLint 
* https://medium.com/@sheldonled/from-jshint-to-eslint-8a0a135fa2bf

#### transpiling ES6
* https://css-tricks.com/transpiling-es6/ introduce Babel and Gulp
