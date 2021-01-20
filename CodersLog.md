# Coder's Log
----------------------------------------------------------

# Format

## LOG:

## DATE, 2021 

**Today's Progress**:

**Thoughts**: 

**Link to work**:

**Resources**:

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

## LOG: 002

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

**Link to work**:

[Shopping List Maker](https://jameslusk.github.io/shopping-list.v1/)

**Resources**:
[checkbox solution #1](https://stackoverflow.com/questions/56837740/how-to-add-remove-class-from-a-parent-list-itemli-when-their-child-checkbox-is)<br>
[checkbox solution #2](https://stackoverflow.com/questions/40245046/js-how-to-select-and-line-through-the-items-in-html-list-by-pressing-on-a-butt)<br>
[checkbox solution #3](https://github.com/drood87/shoppingList/blob/master/script.js)<br>
[checkbox solution #4](https://github.com/NickPax/shopping-list/blob/master/script.js)

----------------------------------------------------------