# Coder's Log
----------------------------------------------------------

# Format

## LOG:

## DATE, 2021 

# Today's Progress:

# Thoughts: 

# Link to work: <br>

# Resources: <br>

----------------------------------------------------------

## LOG: #017

## Feb 6th, 2021 

# Today's Progress:

#### **Es9 Object Spread Operator**

Spread syntax (...) allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected.

**Description**
Spread syntax can be used when all elements from an object or array need to be included in a list of some kind. 

In the above example, the defined function takes x, y, and z as arguments and returns the sum of these values. An array value is also defined.

When we invoke the function, we pass it all the values in the array using the spread syntax and the array name — ...numbers.

If the array contained more than three numbers, e.g. [1, 2, 3, 4], then it would still work fine, except that all four would be passed, but only the first three would be used unless you added more arguments to the function, e.g.:

    function sum(x, y, z, n) {
    return x + y + z + n;
    }

**OR**

    const animals = {
        tiger: 23,
        lion: 5,
        monkey: 2    
    }

    const { tiger, ...rest } = animals;

**OR**

    const array = [1,2,3,4,5];
    function sum (a,b,c,d,e) {
        return a + b + c + d + e;
    }

    sum(...array);

    <- 15

**spread operators can be used for arrays or objects**

**cloning to prevent mutation.**
    let numList = [1,2,3];
    let numListClone = [...numList]; **[1, 2, 3]**

**spread operator for destructuring.**
    let animal = {
    name: 'dog',
    color: 'brown',
    age: 7

#### **Finally**

Finally is used to place important code, it will be executed
whether an exception is handled or not. Finally is a block

A finally block contains all the crucial statements that must be executed whether exception occurs or not. The statements present in this block will always execute regardless of whether exception occurs in try block or not such as closing a connection, stream etc.

Syntax of Finally block
    try {
        **Statements that may cause an exception**
    }
    catch {
        **Handling exception**
    }
    finally {
        **Statements to be executed**
    }



    const urls = [
        'https://jsonplaceholder.typicode.com/users',
        'https://jsonplaceholder.typicode.com/posts',
        'https://jsonplaceholder.typicode.com/albums'    
    ]

    Promise.all(urls.map(url =>
        fetch(url).then(people => people.json())
    ))
        .then(array => {
        console.log('users', array[0])
        console.log('posts', array[1])
        console.log('albums', array[2])
        })
        .catch(err => console.log('ughhhh fix it!', err))
        .finally(() => console.log('extra'));

#### **for await of**

    const urls = [
        'https://jsonplaceholder.typicode.com/users',
        'https://jsonplaceholder.typicode.com/posts',
        'https://jsonplaceholder.typicode.com/albums'    
    ]

    const getData = async function() {
        try {
            const [ users, posts, albums ] = await Promise.all(urls.map(url =>
                fetch(url).then(people => people.json())
            ));
            console.log('users', users);
            console.log('posts', posts);
            console.log('albums', albums);
        } catch (err) {
            console.log('oops', err);
        }
    }

    const getData2 = async function() {
        const arrayOfPromises = urls.map(url => fetch(url));
        for await (let request of arrayOfPromises) {
            const data = await request.json();
            console.log(data);
        }
    }

#### **Promise.allSettled()**

The Promise.allSettled() method returns a promise that resolves after all of the given promises have either fulfilled or rejected, with an array of objects that each describes the outcome of each promise.

It is typically used when you have multiple asynchronous tasks that are not dependent on one another to complete successfully, or you'd always like to know the result of each promise.

In comparison, the Promise returned by Promise.all() may be more appropriate if the tasks are dependent on each other / if you'd like to immediately reject upon any of them rejecting.

    const promise1 = Promise.resolve(3);
    const promise2 = new Promise((resolve, reject) => setTimeout(reject, 100, 'foo'));
    const promises = [promise1, promise2];

    Promise.allSettled(promises).
    then((results) => results.forEach((result) => console.log(result.status)));

    // expected output:
    // "fulfilled"
    // "rejected"

Syntax
    Promise.allSettled(iterable);

Parameters

iterable:
An iterable object, such as an Array, in which each member is a Promise.

Return value

A pending Promise that will be asynchronously fulfilled once every promise in the specified collection of promises has completed, either by successfully being fulfilled or by being rejected. At that time, the returned promise's handler is passed as input an array containing the outcome of each promise in the original set of promises.

However, if and only if an empty iterable is passed as an argument, Promise.allSettled() returns a Promise object that has already been resolved as an empty array.

For each outcome object, a status string is present. If the status is fulfilled, then a value is present. If the status is rejected, then a reason is present. The value (or reason) reflects what value each promise was fulfilled (or rejected) with.

Examples

Using Promise.allSettled

    Promise.allSettled([
    Promise.resolve(33),
    new Promise(resolve => setTimeout(() => resolve(66), 0)),
    99,
    Promise.reject(new Error('an error'))
    ])
    .then(values => console.log(values));

    // [
    //   {status: "fulfilled", value: 33},
    //   {status: "fulfilled", value: 66},
    //   {status: "fulfilled", value: 99},
    //   {status: "rejected",  reason: Error: an error}
    // ]

#### `Todays Project`

I worked with a free Starwars API to create a random character profile generator.

# Thoughts: 

Information Overload

# Link to work: <br>
[Star Wars API](https://jameslusk.github.io/starwars-api/)

# Resources: <br>
[Spread syntax (...)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)<br>
[Finally](https://beginnersbook.com/2013/04/java-finally-block/#:~:text=A%20finally%20block%20contains%20all,closing%20a%20connection%2C%20stream%20etc.)<br>
[Promise.allSettled()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/allSettled)<br>
[Lists and examples for new Javascript features](https://github.com/daumann/ECMAScript-new-features-list)<br>


----------------------------------------------------------

## LOG: #016

## Feb 5th, 2021 

# Today's Progress:

Started the day sovling my RoboFriends app issue. For some reason my API with JSON/users was being deployed as HTTP as opposed to HTTPS, therefore it was pushing users to the LOADING (implemented in code if API is down) screen. I'm not exactly sure what caused this issue. To solve I simply re ran the process of NPM build and repackaged the code for deployment. Wonderously, it worked. 

### `Todays Notes`

**AJAX**

Ajax is a set of web development techniques using many web technologies on the
client side to create asynchronous web applications.

With Ajax, web applications can send and retrieve data from a server
asynchronously without interfering with the display and behaviour of the 
existing page. 

**Promises**

The Promise object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.

Description
A Promise is a proxy for a value not necessarily known when the promise is created. It allows you to associate handlers with an asynchronous action's eventual success value or failure reason. This lets asynchronous methods return values like synchronous methods: instead of immediately returning the final value, the asynchronous method returns a promise to supply the value at some point in the future.

A Promise is in one of these states:

- pending: initial state, neither fulfilled nor rejected.
- fulfilled: meaning that the operation was completed successfully.
- rejected: meaning that the operation failed.

A pending promise can either be fulfilled with a value or rejected with a reason (error). When either of these options happens, the associated handlers queued up by a promise's then method are called. If the promise has already been fulfilled or rejected when a corresponding handler is attached, the handler will be called, so there is no race condition between an asynchronous operation completing and its handlers being attached.

As the Promise.prototype.then() and Promise.prototype.catch() methods return promises, they can be chained.

**Chained Promises**

The methods promise.then(), promise.catch(), and promise.finally() are used to associate further action with a promise that becomes settled. These methods also return a newly generated promise object, which can optionally be used for chaining; for example, like this:

    const myPromise =
    (new Promise(myExecutorFunc))
    .then(handleFulfilledA,handleRejectedA)
    .then(handleFulfilledB,handleRejectedB)
    .then(handleFulfilledC,handleRejectedC);

    // or, perhaps better ...

    const myPromise =
    (new Promise(myExecutorFunc))
    .then(handleFulfilledA)
    .then(handleFulfilledB)
    .then(handleFulfilledC)
    .catch(handleRejectedAny);

Handling a rejected promise too early has consequences further down the promise chain. Sometimes there is no choice because an error must be handled immediately; in such cases we must throw something, even if it is a dummy error message like throw -999, to maintain error state down the chain. On the other hand, in the absence of an immediate need it is simpler to leave out error handling until a final .catch() statement.

The termination condition of a promise determines the "settled" state of the next promise in the chain. Any termination other than a throw creates a "resolved" state while terminating with a throw creates a "rejected" state.

    handleFulfilled(value)       { /*...*/; return nextValue;  }
    handleRejection(reason)  { /*...*/; throw  nextReason; }
    handleRejection(reason)  { /*...*/; return nextValue;  }

**Es8 ASYNC AWAIT**

#### e.g. #1

    movePlayer(100, 'Left')
        .then(() => movePlayer(400, 'Left'))
        .then(() => movePlayer(10, 'Right'))
        .then(() => movePlayer(330, 'Left')

**VS**
    
    async function playerStart() {
        const first = await movePlayer(100, 'Left')// Pause
        const second = await movePlayer(400, 'Left')// Pause
        const third = await movePlayer(10, 'Right')// Pause
        const fourth = await movePlayer(330, 'Left')// Pause
    }

#### e.g. #2

    fetch('https://jsonplaceholder.typicode.com/users')
        .then(resp => resp.json())
        .then(console.log

**VS**

    async function fetchUsers() {
        const resp = await fetch('https://jsonplaceholder.typicode.com/users')
        const data = await resp.json()
        console.log(data)
    }

#### e.g. #3

    const urls = [
        'https://jsonplaceholder.typicode.com/users',
        'https://jsonplaceholder.typicode.com/posts',
        'https://jsonplaceholder.typicode.com/albums'    
    ]
    
      Promise.all(urls.map(url =>
          fetch(url).then(people => people.json())
      ))
        .then(array => {
          console.log('users', array[0])
          console.log('posts', array[1])
          console.log('albums', array[2])
        })
        .catch(err => console.log('ughhhh fix it!', err));

**VS**

    const urls = [
        'https://jsonplaceholder.typicode.com/users',
        'https://jsonplaceholder.typicode.com/posts',
        'https://jsonplaceholder.typicode.com/albums'    
    ]

    const getData = async function() {
        try {
            const [ users, posts, albums ] = await Promise.all(urls.map(url =>
                fetch(url).then(people => people.json())
            ))
            console.log('users', users)
            console.log('posts', posts)
            console.log('albums', albums)
        } catch (err) {
            console.log('oops', err)
        }
    }

# Thoughts: 

# Link to work: <br>

# Resources: <br>
[Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)<br>

----------------------------------------------------------

## LOG: #015

## Feb 4th, 2021 

# Today's Progress:

**React.Component**
(Life Cycle Hooks)

Overview
React lets you define components as classes or functions. Components defined as classes currently provide more features which are described in detail on this page. To define a React component class, you need to extend React.Component:

    class Welcome extends React.Component {
    render() {
        return <h1>Hello, {this.props.name}</h1>;
    }
    }
The only method you must define in a React.Component subclass is called render(). All the other methods described on this page are optional.

We strongly recommend against creating your own base component classes. In React components, code reuse is primarily achieved through composition rather than inheritance.

Note:

React doesn’t force you to use the ES6 class syntax. If you prefer to avoid it, you may use the create-react-class module or a similar custom abstraction instead. Take a look at Using React without ES6 to learn more.

The Component Lifecycle
Each component has several “lifecycle methods” that you can override to run code at particular times in the process. You can use this lifecycle diagram as a cheat sheet. In the list below, commonly used lifecycle methods are marked as bold. The rest of them exist for relatively rare use cases.

Mounting
These methods are called in the following order when an instance of a component is being created and inserted into the DOM:

    constructor()
    static getDerivedStateFromProps()
    render()
    componentDidMount()

Note:

These methods are considered legacy and you should avoid them in new code:

UNSAFE_componentWillMount()


# Thoughts: 

# Link to work: <br>

# Resources: <br>
[Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)<br>


----------------------------------------------------------

## LOG: #014

## Feb 2nd, 2021 

# Today's Progress:

Read an article about JSX in React.

**What is JSX?**
JSX is a JavaScript Extension Syntax used in React to easily write HTML and JavaScript together.

Take a look at the below code:

    const jsx = <h1>This is JSX</h1>

This is simple JSX code in React. But the browser does not understand this JSX because it's not valid JavaScript code. This is because we're assigning an HTML tag to a variable that is not a string but just HTML code.

**We can use the above JSX in our React code like this:**

    class JSXDemo extends React.Component {
        render() {
            return <h1>This is JSX</h1>;
        }
    }

    ReactDOM.render(<JSXDemo />, document.getElementById('root'));

I also did a little bit of hand coding wiht the Mimo app on my iphone, as well as read up on JavaScript with CodePlayGround app on my iphone.

# Thoughts: 

Hard to get some good coding hours in on travel days

# Link to work: <br>
- Null

# Resources: <br>
[JSX in React](https://www.freecodecamp.org/news/jsx-in-react-introduction/)

----------------------------------------------------------

## LOG: #013

## Jan 31st, 2021 

# Today's Progress:

**What is NPM**
npm is a package manager for the JavaScript programming language.

It is the default package manager for the JavaScript runtime environment Node.js

It consists of a command line client, also called npm, and an online database of public and paid-for private packages, called the npm registry.

npm is the world's largest Software Registry. The registry contains over 800,000 code packages. Open-source developers use npm to share software. Many organizations also use npm to manage private development.

Create a new React-based project using create-react-app:

$ npm init react-app ./my-react-app

**What is JSON**
JSON (JavaScript Object Notation) is a common data storage format,
typically used for its simplicity when your code needs to read from it.

- JSON stands for JavaScript Object Notation

- JSON is a lightweight format for storing and transporting data

- JSON is often used when data is sent from a server to a web page

- JSON is "self-describing" and easy to understand

JavaScript Object Notation 
	Its a key value pair 
	its popular light-weight way of transfering data 

	for example : 
	Lets try to create a json for Person Object 
			with name , age , isMarried , gender 

		Its ket value pair 
		the key is always String and need to be in quotation
		value can be :
			String 
			Number 
			Boolean 
			null 
			array 
			another json object


		This is one json with 5 fields 
		each key value pair should be separated by comma 
		{
			"name" 		: "Anna", 
			"age" 		: 18  , 
			"isMarried" : false , 
			"gender"	: "female", 
			"company"	: null 
		}

**To Start a NEW JSON & Live-Server**
    $ npm init

    $ sudo npm install -g live-server

Typing '$ live-server' in the terminal will open a locally hosted browser window.

**LoDash**
    $ npm install lodash

Why Lodash?
Lodash makes JavaScript easier by taking the hassle out of working with arrays, numbers, objects, strings, etc.
Lodash’s modular methods are great for:

Iterating arrays, objects, & strings
Manipulating & testing values
Creating composite functions

[Lodash](https://lodash.com/)


**browserify**
    $ sudo npm install -g browserify

require('modules') in the browser

Browserify lets you require('modules') in the browser by bundling up all of your dependencies.

Use a node-style require() to organize your browser code and load modules installed by npm.

browserify will recursively analyze all the require() calls in your app in order to build a bundle you can serve up to the browser in a single <script> tag.

[Browserify](http://browserify.org/)

### React

**Create New React App**
    $ npx create-react-app my-app
    $ cd my-app
    $ npm start

**Tachyons**
    $ npm install tachyons

# Thoughts: 

# Link to work: <br>

# Resources: <br>
[Lodash](https://lodash.com/)<br>
[Browserify](http://browserify.org/)<br>
[Free Logo Maker](https://hatchful.shopify.com/)<br>
[React Get Started](https://create-react-app.dev/docs/getting-started/)<br>


----------------------------------------------------------

## LOG: #012

## Jan 30th, 2021 

# Today's Progress:

Finished Easy Bank web challange. Updated my Portfolio webpage with this newly finished project

I returned to the ZTM course today and started learning more about Github. The following is a list of git commands used to create and implement branches;

[GitHub Tutorial](https://www.atlassian.com/git/tutorials/using-branches#:~:text=Git%20branches%20are%20effectively%20a%20pointer%20to%20a%20snapshot%20of%20your%20changes.&text=Instead%20of%20copying%20files%20from,not%20a%20container%20for%20commits.)

**Common Options**
git branch
-List all of the branches in your repository. This is synonymous with git branch --list.

git branch 
-Create a new branch called . This does not check out the new branch.

git branch -d 
-Delete the specified branch. This is a “safe” operation in that Git prevents you from deleting the branch if it has unmerged changes.

git branch -D 
-Force delete the specified branch, even if it has unmerged changes. This is the command to use if you want to permanently throw away all of the commits associated with a particular line of development.

git branch -m 
-Rename the current branch to .

 
git branch -a
-List all remote branches. 

**Creating Branches**
It's important to understand that branches are just pointers to commits. When you create a branch, all Git needs to do is create a new pointer, it doesn’t change the repository in any other way. If you start with a repository that looks like this:

Git Tutorial: repository without any branches
Then, you create a branch using the following command:

git branch crazy-experiment
-The repository history remains unchanged. All you get is a new pointer to the current commit:

Git Tutorial: Create new branch
Note that this only creates the new branch. To start adding commits to it, you need to select it with git checkout, and then use the standard git add and git commit commands. 

**Creating remote branches**
So far these examples have all demonstrated local branch operations. The git branch command also works on remote branches. In order to operate on remote branches, a remote repo must first be configured and added to the local repo config.

 
$ git remote add new-remote-repo https://bitbucket.com/user/repo.git # Add remote repo to local repo config $ git push  crazy-experiment~ # pushes the crazy-experiment branch to new-remote-repo
-This command will push a copy of the local branch crazy-experiment to the remote repo .

**Deleting Branches**
Once you’ve finished working on a branch and have merged it into the main code base, you’re free to delete the branch without losing any history:

git branch -d crazy-experiment
-However, if the branch hasn’t been merged, the above command will output an error message:

error: The branch 'crazy-experiment' is not fully merged. If you are sure you want to delete it, run 'git branch -D crazy-experiment'.
-This protects you from losing access to that entire line of development. If you really want to delete the branch (e.g., it’s a failed experiment), you can use the capital -D flag:

git branch -D crazy-experiment
-This deletes the branch regardless of its status and without warnings, so use it judiciously.

The previous commands will delete a local copy of a branch. The branch may still exist in remote repos. To delete a remote branch execute the following.

 
git push origin --delete crazy-experiment

Or

git push origin :crazy-experiment
-This will push a delete signal to the remote origin repository that triggers a delete of the remote crazy-experiment branch.


# Thoughts: 

Long day

# Link to work: <br>
[Easy Bank](https://trusting-ardinghelli-5ba15f.netlify.app/)

# Resources: <br>
[GitHub Tutorial](https://www.atlassian.com/git/tutorials/using-branches#:~:text=Git%20branches%20are%20effectively%20a%20pointer%20to%20a%20snapshot%20of%20your%20changes.&text=Instead%20of%20copying%20files%20from,not%20a%20container%20for%20commits.)<br>
[ZTM Start Here Guidelines](https://github.com/zero-to-mastery/start-here-guidelines)<br>
[ZTM Git Repo](https://github.com/zero-to-mastery)

----------------------------------------------------------

## LOG: #011

## Jan 29th, 2021 

# Today's Progress:

Worked on Easy Bank website project for roughly 2hrs. Finished section/feature and section/articles.

# Thoughts: 

Got some good practice in with flexbox, grid, and media queries. Felt good to get some solid reps in.

# Link to work: <br>
https://trusting-ardinghelli-5ba15f.netlify.app/

# Resources: <br>
[Responsive 4-column layout with CSS Grid | Build a responsive website from scratch (Part 6)](https://www.youtube.com/watch?v=FTEkwBDEjDg&list=PLUWqFDiirlsuYscECzks6zIZWr_Cfcx9k&index=6)

----------------------------------------------------------

## LOG: #010

## Jan 28th, 2021 

# Today's Progress:

Worked a little bit more on the Easy Bank Project. Fixed hero image/text div.

# Thoughts: 

I wish I had had more time to work on projects. Only go in 1.5hr.

# Link to work: <br>
https://trusting-ardinghelli-5ba15f.netlify.app/

# Resources: <br>
[Responsive 4-column layout with CSS Grid | Build a responsive website from scratch (Part 6)](https://www.youtube.com/watch?v=FTEkwBDEjDg&list=PLUWqFDiirlsuYscECzks6zIZWr_Cfcx9k&index=6)

----------------------------------------------------------

## LOG: #009

## Jan 27th, 2021 

# Today's Progress:

Worked for about two hours on the Easy Bank website challenge from FrontEndMentor.io/. Finished up Menu popup and added Hero section images.

# Thoughts: 

Slowly plugging a long. Advanced CSS can be a bit overwhelming. There are a lot of syntax variables to learn to manipulate the visual appearance.

# Link to work: <br>
https://jameslusk.github.io/easyBank/

# Resources: <br>
[Responsive 4-column layout with flexbox | Build a responsive website from scratch (Part 5)](https://www.youtube.com/watch?v=8_AWtI_SOU8&list=PLUWqFDiirlsuYscECzks6zIZWr_Cfcx9k&index=5)

----------------------------------------------------------

## LOG: #008

## Jan 26th, 2021 

# Today's Progress:

Whew! Long day of traveling for BNSF. Researched how to push your source code to a live server and domain. Used Netlify and linked to my GitHub. Not to difficult. Designed my Portfolio Page v1.

# Thoughts: 

I'm Tired

# Link to work: <br>
jameslusk.io

# Resources: <br>
[Netlify](netlify.com)

----------------------------------------------------------

## LOG: #007

## Jan 25th, 2021 

# Today's Progress:

Read through JavaScript documentation regarding Browserify, ECMA, and Modules. Trying to understand.

Worked in ZTM course with terminal window, and VS code options.

ZTM - Started Git & GitHub section.

**Easy Bank Website Project**
Added responsive hamburger menu and mobile menu overlay with JavaScript functions 

# Thoughts: 

Glad to be getting into some GitHub functionality in my ZTM course and please with progress on website project. Let's go!

# Link to work: <br>
https://jameslusk.github.io/easyBank/

# Resources: <br>
[Brief history of JavaScript Modules](https://medium.com/sungthecoder/javascript-module-module-loader-module-bundler-es6-module-confused-yet-6343510e7bde)<br>
[ES modules: A cartoon deep-dive](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/)<br>
[JavaScript. The Core: 2nd Edition](http://dmitrysoshnikov.com/ecmascript/javascript-the-core-2nd-edition/)<br>
[The Modern JavaScript Tutorial](https://javascript.info/)<br>

----------------------------------------------------------

## LOG: #006

## Jan 24th, 2021 

# Today's Progress:

### Notes 

#### Es10

**flat()**
// flat() to remove Nested Arrays

    const array = [1,[2,3],[4,5]];

    array.flat();

    <- (5) [1, 2, 3, 4, 5]

    const array = [1,2,[3,4,[5]]];

    array.flat();

    <- (5) [1, 2, 3, 4, Array(1)]

// flay(2) flattens deeper in the array

**flatMap()**

    const array = [1,2,[3,4,[5]]];

    const thisArray = array.flatMap(number => number + 2);
    
    <- (3) [3, 4, "3,4,52"]


**Trimming**

    userEmail = '              eddytheeagly@gmail.com'
    userEmail2 = 'eddytheeagly@gmail.com              '

    userEmail.trimStart()
    userEmail2.trimEnd()


**fromEntries**

    userProfiles = [['commanderTom', 23], ['derekZlander', 40], ['hansel', 18]];

    Object.fromEntries(userProfiles);

    <- {commanderTom: 23, derekZlander: 40, hansel: 18}

**try {} catch {}**

    try {
        4 + 5;
    } catch {

    }
    <- 9

    try {
        bob + 'hi';
    } catch {
        console.log(`you messed up`);
    }
    <- you messed up

    try {
        bob + 'hi';
    } catch (error) {
        console.log(`you messed up` + error);
    }
    <- you messed up ReferenceError: bob is not defined

#### Advanced loops in JavaScript

// Method #1
    const basket = ['apples', 'oranges', 'grapes'];

    for (let i = 0; i < basket.length; i++) {
        console.log(basket[i]);
    }

    <- apples
       oranges
       grapes 

// Method #2

    basket.forEach(item => {
        console.log(item);
    })

    <- apples
       oranges
       grapes 

// for of loop (iterating over array - going 1 by 1 and look at array/strings items)
// for of loops only work on iterable elements (arrays, strings)

    for (item of basket) {
        console.log(item)
    }

    <- apples
    oranges
    grapes 

// for in loop (loop over and see object properties)
// for in loop only works for observing objects

    const detailedBasket = {
        apples : 5,
        oranges: 10,
        grapes: 1000,
    }

// 'apple' is property, where '5' is value (enumirating - for objects)

    for (item in detailedBasket) {
        console.log(item);
    }

    <- apples
       oranges
       grapes

#### MAX_SAFE_INTEGER

The MAX_SAFE_INTEGER constant has a value of 9007199254740991 (9,007,199,254,740,991 or ~9 quadrillion). The reasoning behind that number is that JavaScript uses double-precision floating-point format numbers as specified in IEEE 754 and can only safely represent integers between -(253 - 1) and 253 - 1.

Safe in this context refers to the ability to represent integers exactly and to correctly compare them. For example, Number.MAX_SAFE_INTEGER + 1 === Number.MAX_SAFE_INTEGER + 2 will evaluate to true, which is mathematically incorrect. See Number.isSafeInteger() for more information.

This field does not exist in old browsers. Using it without checking its existence, such as Math.max(Number.MAX_SAFE_INTEGER, 2), will yield undesired results such as NaN.

Because MAX_SAFE_INTEGER is a static property of Number, you always use it as Number.MAX_SAFE_INTEGER, rather than as a property of a Number object you created.

### Es2020

#### BigInt
// used when wanting to calculate above MAX SAFE INTEGER

    typeof 1n;

    <- "bigint"


#### Optional Chaining '?.'

    let willPokemon = {
        pikachu: {
            species: 'mouse',
            height: 0.4,
            weight: 6,
        }
    }

    let weight = willPokemon.pikachu.weight;
    console.log(`weight: `, weight)

    <- weight: 6

// Part 2

    let willPokemon = {
        pikachu: {
            species: 'mouse',
            height: 0.4,
            weight: 6,
        }
    }

    let jamesPokemon = {
        raichu: {
            species: 'mouse',
            height: 0.8,
            weight: 16,
        }
    }

    let weight3 = jamesPokemon?.pikachu?.weight; // Replaces if statements

    console.log(weight3);

    <- undefined


#### Nullish Coalescing Operator ?? (instead of || 'or' operator)

    let willPokemon = {
        pikachu: {
            species: 'mouse',
            height: 0.4,
            weight: 6,
        }
    }

    let jamesPokemon = {
        pikachu: {
            species: 'mouse',
            height: 0.8,
            weight: 16,
            power: '',
        }
    }

    let power = jamesPokemon?.pikachu?.power ?? 'no power';

    console.log(power);

    <- undefined

### Debugging

// This line of code...
    const flattened = [[0, 1], [2, 3], [4, 5]].reduce((a, b) => a.concat(b), []);

// Becomes this...
    const flattened = [[0, 1], [2, 3], [4, 5]].reduce((accumulator, array) => {
        console.log('array ', array);
        console.log('accumulator ', accumulator);
        [].concat(array);
        return accumulator.concat(array);
    }, []);

// Replace console.log as a manual debugger with the following...
    const flattened = [[0, 1], [2, 3], [4, 5]].reduce((accumulator, array) => {
        debugger;
        return accumulator.concat(array);
    }, []);

// Sets off debugger in Console

### What is JavaScript

**JavaScript Definition:**
an object-oriented computer programming language commonly used to create interactive effects within web browsers.

**JavaScript** is single-threaded that can be non-blocking: meaning only one line of syntax is executed at a time and is also asynchronous. 
 
// Call Stack

// Web API

// Call Back Queue

// Event Loop

## Website Project:

Started a project from [FrontEnd Mentor](frontendmentor.io). 

# Thoughts: 

I was feeling a bit overwhelmed with thinking about how far I need to go just to get to a baseline level within web development. I am feeling a bit impatient. I have to remind myself that it all just takes time.

# Link to work: <br>
https://jameslusk.github.io/easyBank/

# Resources: <br>
[MAX_SAFE_INTEGER](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/MAX_SAFE_INTEGER)<br>
[Brief history of JavaScript Modules](https://medium.com/sungthecoder/javascript-module-module-loader-module-bundler-es6-module-confused-yet-6343510e7bde)<br>
[ES modules: A cartoon deep-dive](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/)<br>
[JavaScript. The Core: 2nd Edition](http://dmitrysoshnikov.com/ecmascript/javascript-the-core-2nd-edition/)<br>
[The Modern JavaScript Tutorial](https://javascript.info/)<br>
[You dont know javascript](https://github.com/getify/You-Dont-Know-JS)<br>
[How to think like a programmer](https://www.freecodecamp.org/news/how-to-think-like-a-programmer-lessons-in-problem-solving-d1d8bf1de7d2/)

----------------------------------------------------------

## LOG: #005

## Jan 23rd, 2021 

# Today's Progress:

**Notes:**

#### Advanced Objects:
**Scope**
In the most simplified of terms, scope has two levels: global scope and local scope. Global scope refers to variables that are accessible anywhere because they are declared outside of any individual functions or methods — usually at the top of the file. They exist in the global space, ready to be called upon at any time. The first example below concerns global scope.
![Picture(https://miro.medium.com/max/700/1*7mxyY1uQDid48yH1yJ0QtA.png)]

**Context**
Context in JavaScript is another subject of confusion. It refers primarily to the use of the keyword this. The value of this depends on where it is being invoked.
Invoking this in the global space will return the entire window object. This is because the window object is the starting point of all the code we write.

// Referecene type

    var obj1 = { value: 10 };
    var obj2 = obj1;
    var obj3 = { value: 10 };

    > obj1 === obj2;
    <- true

    > obj2 === obj3;
    <- false

// Context vs Scope
// Scope

    function b() {
        let a = 4;
    }

// Context 

    const obj4 = {
        a: function() {
            console.log(this); 
        }
    }

// Instantiation 

    class Player {
        consturctor(name, type) {
            console.log(this);
            this.name = name;
            this.type = type;
        }
        introduce() {
            console.log(`Hi, I am ${this.name}, I am a ${this.type}`);
        }
    }

    class Wizard extends Player {
        constructor(name, type) {
          super(name, type);
        }
        play() {
          console.log(`Kazaam! I am a ${this.type}!!`);
        }
      }
    const wizard1 = new Wizard('Shelly', 'Healer');
    const wizard2 = new Wizard('Shawn', 'Dark Magic');

#### Objects vs Arrays

// This is an OBJECT
    let obj = {a: 'a', b: 'b', c: 'c'};

// This is an ARRAY
    let array = [1, 2, 3, 5, 5];

// Cloning an Object
    let obj = {a: 'a', b: 'b', c: 'c'};

    let clone = Object.assign({}, obj);
    let clone2 = {...obj};

    obj.c = 5;
    console.log(obj);
    console.log(clone);
    console.log(clone2);

    <- {a: "a", b: "b", c: 5}
    <- {a: "a", b: "b", c: "c"}
    <- {a: "a", b: "b", c: "c"}

// Deep Cloning with JSON

    let obj = {a: 'a', b: 'b', c: {deep: 'copy me'}};

    let clone = Object.assign({}, obj);
    let clone2 = {...obj};
    let superClone = JSON.parse(JSON.stringify(obj));


    obj.c.deep = 'haha';
    console.log(obj);
    console.log(clone);
    console.log(clone2);
    console.log(superClone);

    <- {a: "a", b: "b", c: "haha"}
    <- {a: "a", b: "b", c: "haha"}
    <- {a: "a", b: "b", c: "haha"}
    <- {a: "a", b: "b", c: "copy me"} 

#### Es7 

// .includes()

    const pets = ['cat', 'dog', 'bat'];
    pets.includes('dog');

    <- true

// Exponential operator

    const square = (x) => x**2;

    square(2);

    <- 4

#### Es8 

// String padding

    Turtle.padStart(10);

    <- "          Turtle"

    Turtle.padEnd(10);

    <- "Turrle          "

// Trailing comma ',' -> Makes syntacially cleaner

    const fun = (a,b,c,d,) => {
        console.log(a);
    }

    fun(1,2,3,4,);

    <- 1

// Objects

    let obj = {
        username0: 'Santa',
        username1: 'Rudolph',
        username2: 'Grinch',
    }

    Object.values(obj).forEach(value => {
        console.log(value);
    })

    Object.entries(obj).forEach(value => {
        console.log(value);
    })

    Object.entries(obj).map(value => {
        return value[1] + value[0].replace('username', '');
    })

    <- (3) ["Santa0", "Rudolph1", "Grinch2"]

#### VS Code Setup

I watched a video from freeCodeCamp about VS Code setup and settings. Learned about emmet setup and found a cheat sheet for it.

# Thoughts: 

More advanced data structures in JavaScript. It makes me want to go back to my cs50 course and rewrite those PSETs in JavaScript for practice. So much to take in, to be honest. I can tell I am just getting small tastes of things I will have to eventually take big bites out of.

# Link to work: <br>
No links today.

# Resources: <br>
[JS Comparison Table](https://dorey.github.io/JavaScript-Equality-Table/)<br>
[Equality comparisons and sameness](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness)<br>
[The Abstract Equality Comparison Algorithm](https://262.ecma-international.org/5.1/#sec-11.9.3)<br>
**Useful Tool** [JavaScript Object Explorer](https://sdras.github.io/object-explorer/)<br>
[Emmet Cheet Sheet](https://docs.emmet.io/cheat-sheet/)


----------------------------------------------------------

## LOG: #004

## Jan 22nd, 2021 

**Today's Progress**:

## Notes:

# JavaScript ES5 & ES6: let and const

## let

### i.e. Redeclaring Variables
#1;

    var x = 10;
    // Here x is 10
    {
    var x = 2;
    // Here x is 2
    }
    // Here x is 2

#2;

    var x = 10;
    // Here x is 10
    {
    let x = 2;
    // Here x is 2
    }
    // Here x is 10

### i.e. Loop Scope
#1;

    var i = 5;
    for (var i = 0; i < 10; i++) {
    // some statements
    }
    // Here i is 10

#2;

    let i = 5;
    for (let i = 0; i < 10; i++) {
    // some statements
    }
    // Here i is 5

## const

Variables defined with const behave like let variables, except they cannot be reassigned:

    const PI = 3.141592653589793;
    PI = 3.14;      // This will give an error
    PI = PI + 10;   // This will also give an error

### i.e. Declaring

Redeclaring or reassigning an existing const variable, in the same scope, or in the same block, is not allowed:

    const x = 2;       // Allowed
    const x = 3;       // Not allowed
    x = 3;             // Not allowed
    var x = 3;         // Not allowed
    let x = 3;         // Not allowed

    {
    const x = 2;   // Allowed
    const x = 3;   // Not allowed
    x = 3;         // Not allowed
    var x = 3;     // Not allowed

    ### Destructuring

// if we had an object below and wanted to access each item...
    const obj = {
        player: 'bobby',
        exp: 100,
        wizardLevel = false
    }

// we would have to do the following...
    const player = obj.player;
    const exp = obj.exp;
    let wizardLevel = obj.wizardLevel;

// with destructuring you can do this...

    const { player, exp } = obj;

    let { wizardLevel } = obj;

// this makes the above const and let available to use elsewhere in your code.

### Object Properties

    const name = 'john snow';

    const obj = {
        [name]: 'hello',
        ['ray' + 'smith']: 'sup'
    }

// Appears in console like the following...
    >obj
    {john snow: "hello", raysmith: "sup"}

    // Another i.e.
    const a = "Simon";
    const b = true;
    const c = {};

    const obj = { a, b, c }

// Appears in console like the following...

    >obj
    {a: "Simon", b: true, c: {…}}

### New String Syntax

    const name = "Sally";
    const age = 34;
    const pet = "horse";

    const greeting = `Hello ${name} you seem to be ${age-10}, what a majestic ${pet} you have!`;

// Console.log

    > greeting
    <- "Hello Sally you seem to be 24, what a majestic horse you have!"

### Default Arguments

// i.e.
    function greet(name='', age=30, pet='cat') {
        return `Hello ${name} you seem to be ${age-10}, what a majestic ${pet} you have!`;
    }

// Console.log

    > greet()
    <- "Hello  you seem to be 20, what a majestic cat you have!"

// i.e. #2 Console.log

    > greet("john", 50, "monkey");
    <- "Hello john you seem to be 40, what a majestic monkey you have!"

### Symbol

    let sym1 = Symbol();
    let sym2 = Symbol('foo');
    let sym3 = Symbol('foo');

// Console.log

    > sym1
    <- Symbol()
    > sym2
    <- Symbol(foo)
    > sym3
    <- Symbol(foo)
    > sym2 === sym3
    <- false

### Arrow Functions

// old way...

    function add(a, b) {
        return a + b;
    }

// arrow function way...

    const add = (a, b) => a + b;

// OR...

    const add = (a, b) => {
        return a + b;
    }

// Console.log

    > add(27, 34);
    <- 61
    
### Closures

// Function Alerts Hi in broswer

    const first = () => {
        const greet = 'HI';
        const second = () => {
            const name = "bobby";
            alert(greet);
        }
        return second;
    }

    const newFunc = first();
    newFunc();

### Currying

    > const multiply = (a, b) => a * b;
    > const curriedMultiply = (a) => (b) => a * b;
    > curriedMultiply(3)(4);
    <- 12

### Compose 

    > const compose = (f, g) => (a) => f(g(a));

    > const sum = (num) => num + 1;

    > compose(sum, sum)(5);

    <- 7

### Arrays

// Advanced arrays
    var thisArray = [1, 2, 10, 16];

    const double = []
    const newArray = thisArray.forEach((num) => {
        double.push(num * 2);
    })

    console.log(double);

    <- (4) [2, 4, 20, 32]
    

### Map, Filter, Reduce 

// map

    const mapArray = thisArray.map(num => num * 2);

    console.log(mapArray);

    <- (4) [2, 4, 20, 32]

// filter

    const filterArray = thisArray.filter(num => num > 5);

    console.log(filterArray);

    <- (2) [10, 16]

// reduce

    const reduceArray = thisArray.reduce((accumulator, num) => {
        return accumulator + num;
    }, 0);

    console.log('reduce', reduceArray);

    <- reduce 29

    const reduceArray = thisArray.reduce((accumulator, num) => {
        return accumulator + num;
    }, 5);

    console.log('reduce', reduceArray);

    <- reduce 34

**Thoughts**: 

Another day of deep learning in Advanced JavaScript. A bit overwhelming, a lot to take in. Need to get practicing with these principles and syntax to really hammer them in.

**Link to work**: <br>
No linked work today

**Resources**: <br>
[JavaScript Let](https://www.w3schools.com/js/js_let.asp)<br>
[JavaScript Const](https://www.w3schools.com/js/js_const.asp)<br>


----------------------------------------------------------

## LOG: #003

## Jan 21, 2021 

**Today's Progress**:

Solved the damned checkbox/line-through issue with my shopping list maker. Sort of; with the following code;

function strikeThrough(event) {
    var parent = document.getElementById("c1").parentElement;
    parent.classList.toggle("done");
}

It performs the strike-through of list item, but only first item on the list. Good enough for now. Moving on in lesson. Notes from fellow ZTM student below helped me out.

## Notes From Joao (ZTM Disscord)

Ok well there are a couple of ways. Based on  what you are doing right now, I would modify the li element's CSS style. To do that you can create addEventListener that will trigger when clicked on a checkbox, target it's parent element (given that your input is inside the li) and update the classList. You should of course create that class in your CSS which would simply apply the text-decoration property.
To target the element of a parent you can use parentElement (is not a function)
I think with this is enough to get started, I think you already are familiar with all of these?
A final hint: do not add the event listener for each individual checkbox. Create one for the entire list and check inside the function which element was clicked on.

## Today's lesson

Made a gradient background generator and learned syntax in both css and javascript to do so.

### CSS Linear Gradients
To create a linear gradient you must define at least two color stops. Color stops are the colors you want to render smooth transitions among. You can also set a starting point and a direction (or an angle) along with the gradient effect.

Styntax:

background-image: linear-gradient(direction, color-stop1, color-stop2, ...);

### <input type="color">

<input> elements of type color provide a user interface element that lets a user specify a color, either by using a visual color picker interface or by entering the color into a text field in #rrggbb hexadecimal format. Only simple colors (without alpha channel) are allowed though CSS colors has more formats, e.g. color names, functional notations and a hexadecimal format with an alpha channel.

The element's presentation may vary substantially from one browser and/or platform to another—it might be a simple textual input that automatically validates to ensure that the color information is entered in the proper format, or a platform-standard color picker, or some kind of custom color picker window.

### HTML

<p>Choose your monster's colors:</p>

<div>
    <input type="color" id="head" name="head"
           value="#e66465">
    <label for="head">Head</label>
</div>

<div>
    <input type="color" id="body" name="body"
            value="#f6b73c">
    <label for="body">Body</label>
</div>

### CSS 

p,
label {
    font: 1rem 'Fira Sans', sans-serif;
}

input {
    margin: .4rem;
}

### HTML DOM textContent Property

Definition and Usage
The textContent property sets or returns the text content of the specified node, and all its descendants.

If you set the textContent property, any child nodes are removed and replaced by a single Text node containing the specified string.

Note: This property is similar to the innerText property, however there are some differences:

textContent returns the text content of all elements, while innerText returns the content of all elements, except for <script> and <style> elements.
innerText will not return the text of elements that are hidden with CSS (textContent will). 
Tip: Sometimes this property can be used instead of the nodeValue property, but remember that this property returns the text of all child nodes as well.

Tip: To set or return the HTML content of an element, use the innerHTML property.

### ZTM Lesson #141. Scope:

// Scope

// Root Scope (window)
var fun = 5;

function funFUnction() {
    // Child Scope
    var fun = "hellooo";
    console.log(fun);
}

### JavaScript Function Scope
In JavaScript there are two types of scope:

Local scope
Global scope
JavaScript has function scope: Each function creates a new scope.

Scope determines the accessibility (visibility) of these variables.

Variables defined inside a function are not accessible (visible) from outside the function.

#### Local JavaScript Variables
Variables declared within a JavaScript function, become LOCAL to the function.

Local variables have Function scope: They can only be accessed from within the function.

// code here can NOT use carName

function myFunction() {
  var carName = "Volvo";

  // code here CAN use carName

}

#### Global JavaScript Variables
A variable declared outside a function, becomes GLOBAL.

A global variable has global scope: All scripts and functions on a web page can access it. 

var carName = "Volvo";

// code here can use carName

function myFunction() {

  // code here can also use carName

}

#### Conditional (Ternary) Operator
JavaScript also contains a conditional operator that assigns a value to a variable based on some condition.

Syntax:
variablename = (condition) ? value1:value2 

Example:
var voteable = (age < 18) ? "Too young":"Old enough";

#### The JavaScript Switch Statement
Use the switch statement to select one of many code blocks to be executed.

Syntax:
switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
}

This is how it works:

The switch expression is evaluated once.
The value of the expression is compared with the values of each case.
If there is a match, the associated block of code is executed.
If there is no match, the default code block is executed.

Example #2:

//Using this function, answer the questions below:
function moveCommand(direction) {
    var whatHappens;
    switch (direction) {
        case "forward":
            break;
            whatHappens = "you encounter a monster";
        case "back":
            whatHappens = "you arrived home";
            break;
            break;
        case "right":
            return whatHappens = "you found a river";
            break;
        case "left":
            break;
            whatHappens = "you run into a troll";
            break;
        default:
            whatHappens = "please enter a valid direction";
    }
    return whatHappens;
}

**Thoughts**: 

Wow, today was alot. Felt great to take a big step forward with my Shopping List checkbox issue. Started to dive into Advanced JavaScript. The rabbit hole is deep.

**Link to work**:<br>
https://jameslusk.github.io/background-generator/

**Resources**: <br>
[CSS Linear Gradients](https://www.w3schools.com/css/css3_gradients.asp)<br>
[<input type="color">](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/color)<br>
[HTML DOM textContent Property](https://www.w3schools.com/jsref/prop_node_textcontent.asp)<br>
[JavaScript Scope](https://www.w3schools.com/js/js_scope.asp)<br>
[Conditional (Ternary) Operator](https://www.w3schools.com/js/js_comparisons.asp)<br>
[The JavaScript Switch Statement](https://www.w3schools.com/js/js_switch.asp)<br>

----------------------------------------------------------
## LOG: #002

## Jan 20th, 2021 

**Today's Progress**: 5.2hrs

Made some progress with a Shopping List maker that I'm working on. It could really double as a To Do list. I have to where user can enter a item in the form field, press enter, and then the item gets added to the list with a checkbox and a delete button. I worked on coding the program to line-through the text when the checkbox is clicked. I spent most of my time today searching and trying different methods to no avail.

I was able to add the checkbox element with the following code;

<!-- // Add checkbox element to list -->
    checkBox = cb = document.createElement( "input" );
    cb.type = "checkbox";
    cb.id = "c1";
    cb.value = name;
    cb.checked = false;
<!-- //Append the checkbox to the li -->
    li.appendChild(cb);

As information, I am writing this program with logic in JavaScript.

**Thoughts**: 

Today was a mental struggle for sure. I searched and attempted different combonations of syntax to make the damn thing line-through list text when the checkbox is clicked. It's crazy that when you get so involved with a problem time seems to fly by. It didn't feel like I had been working on this issue for roughly 5 hours. Nonetheless, I do enjoy it. I enjoy the obsticles and the extraordinary feeling you get once you solve a problem.

I ened up reaching out to some people in the Zero to Mastery Discord as a desparate plea for help. Someone answered, looked at my code, and gave some pointers. I now need to get back on tomorrow and (try to )apply what they said.

**Link to work**:<br>

[Shopping List Maker](https://jameslusk.github.io/shopping-list.v1/)

**Resources**:<br>
[checkbox solution #1](https://stackoverflow.com/questions/56837740/how-to-add-remove-class-from-a-parent-list-itemli-when-their-child-checkbox-is)<br>
[checkbox solution #2](https://stackoverflow.com/questions/40245046/js-how-to-select-and-line-through-the-items-in-html-list-by-pressing-on-a-butt)<br>
[checkbox solution #3](https://github.com/drood87/shoppingList/blob/master/script.js)<br>
[checkbox solution #4](https://github.com/NickPax/shopping-list/blob/master/script.js)

----------------------------------------------------------

## LOG: #001

## Jan 19th, 2021

**Today's Progress**:
4.4hrs

I started my moring off by uploading a JavaScript Tester program I wrote yesterday and then created a README bio in GitHub for my profile. I then created and formatted this log as a way to journal and track my progress. I wish I had started it sooner.

Zero to Mastery (ZTM) Course: Learning about Document Object Model (DOM): When a web page is loaded, the browser creates a Document Object Model of the page.

The DOM is a W3C (World Wide Web Consortium) standard. The DOM defines a standard for accessing documents:
"The W3C Document Object Model (DOM) is a platform and language-neutral interface that allows programs and scripts to dynamically access and update the content, structure, and style of a document."

<h2>Learned about</h2> 

DOM Selectors
--------------
getElementsByTagName
getElementsByClassName
getElementById

querySelector
querySelectorAll

getAttribute
setAttribute

##Changing Styles
style.{property} //ok

className //best
classList //best

classList.add
classList.remove
classList.toggle

##Bonus
innerHTML //DANGEROUS

parentElement
children

##It is important to CACHE selectors in variables

##CODE: How to make parent elements contorl ( > * )
#parent > * {
    display: block;
    margin: 30px 0;
}

##CODE: how to force first letter to uppercase
textBox.value = textBox.value.charAt(0).toUpperCase() + textBox.value.slice(1).toLowerCase();

Made a simple shopping list maker with DOM and JavaSript.
**Thoughts**: 
Using DOM and JavaScript is exacltly what I was looking for in learning how to mimic making a To-Do list program with Flask. There are a lot of possibilites with JavaScript and DOM manipulation. I'm eager to get more involved. I have some ideas for projects using this system.

**Link to work**:

[Shopping List Maker](https://jameslusk.github.io/shopping-list.v1/)

**Resources**:<br>
[w3schoools - JavaScript HTML DOM](https://www.w3schools.com/js/js_htmldom.asp)<br>
[JavaScript Char/key codes](https://www.cambiaresearch.com/articles/15/javascript-char-codes-key-codes)<br>
[Event reference](https://developer.mozilla.org/en-US/docs/Web/Events)

----------------------------------------------------------
