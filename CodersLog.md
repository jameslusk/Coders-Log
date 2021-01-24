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
