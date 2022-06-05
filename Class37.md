# **Readings: React 1**

# **ES6 Syntax**

## **Difference between var, let and const**

The differences between the three are based on scope, hoisting, and reassignment.


| Keyword  | Scope | Hoisting | Can Be Reassigned | Can Be Re-declared |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| var  | Function scope  | Yes  | Yes  | Yes |
| let  | Block scope  | No | Yes  | No |
| const  | Block scope  | No  | No  | No |


A commonly accepted practice is to use ***const*** as much as possible, and ***let*** in the case of loops and reassignment. Generally, ***var*** can be avoided outside of working on legacy code.

<br>

## **Variable Scope**

cope in JavaScript refers to the current context of code, which determines the accessibility of variables to JavaScript. The two types of scope are:

- **Global variables:** are those declared outside of a block.
- **Local variables:** are those declared inside of a block.

<br>

## **Hoisting**

If we attempt to use a variable before it has been declared and initialized, it will return *undefined*

```
// Attempt to use a variable before declaring it
console.log(x);

// Variable assignment
var x = 100;
```

However, if we omit the var keyword, we are no longer declaring the variable, only initializing it. It will return a *ReferenceError* and halt the execution of the script.

```
// Attempt to use a variable before declaring it
console.log(x);

// Variable assignment without var
x = 100;
```

The reason for this is due to **hoisting**, a behavior of JavaScript in which variable and function declarations are moved to the top of their scope. Since only the actual declaration is hoisted, not the initialization, the value in the first example returns undefined.


<br>


## **Variable Declaration**

**let** keyword, allows for block-scoped variables which cannot be hoisted or re-declared.

<br>


## **Constants Declaration**

**const** keyword, cannot be re-declared or reassigned, but is not immutable.


<br>

## **Arrow functions**

The arrow function expression syntax is a shorter way of creating a function expression. Arrow functions do not have their own *this*, do not have prototypes, cannot be used for constructors, and should not be used as object methods.


### **ES5**

```
function func(a, b, c) {} // function declaration
var func = function (a, b, c) {} // function expression
```


### **ES6**

```
let func = (a) => {} // parentheses optional with one parameter
let func = (a, b, c) => {} // parentheses required with multiple parameters
```

<br>

## **Classes/constructor functions**


ES6 introducess the class syntax on top of the prototype-based constructor function.

### **ES5**
```
function Func(a, b) {
  this.a = a
  this.b = b
}

Func.prototype.getSum = function () {
  return this.a + this.b
}

var x = new Func(3, 4)
```

### **ES6**

```
class Func {
  constructor(a, b) {
    this.a = a
    this.b = b
  }

  getSum() {
    return this.a + this.b
  }
}

let x = new Func(3, 4)
```


<br>


## **Inheritance**
The extends keyword creates a subclass.

### **ES5**

```
function Inheritance(a, b, c) {
  Func.call(this, a, b)

  this.c = c
}

Inheritance.prototype = Object.create(Func.prototype)
Inheritance.prototype.getProduct = function () {
  return this.a * this.b * this.c
}

var y = new Inheritance(3, 4, 5)
```

### **ES6**

```
class Inheritance extends Func {
  constructor(a, b, c) {
    super(a, b)

    this.c = c
  }

  getProduct() {
    return this.a * this.b * this.c
  }
}

let y = new Inheritance(3, 4, 5)
```

<br>

<br>


## **React: Part 1**

React is a JavaScript library, and so we’ll assume you have a basic understanding of the JavaScript language.

## **JXS**


This funny tag syntax is neither a string nor HTML.

```
const element = <h1>Hello, world!</h1>;
```

It is called **JSX**, and it is a syntax extension to JavaScript. We recommend using it with React to describe what the UI should look like. JSX may remind you of a template language, but it comes with the full power of JavaScript.


Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called “components” that contain both. We will come back to components in a further section, but if you’re not yet comfortable putting markup in JS, this talk might convince you otherwise.

React doesn’t require using JSX, but most people find it helpful as a visual aid when working with UI inside the JavaScript code. It also allows React to show more useful error and warning messages.

<br>

### **Embedding Expressions in JSX**

In the example below, we declare a variable called *name* and then use it inside JSX by wrapping it in curly braces:

```
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;
``` 


You can put any valid JavaScript expression inside the curly braces in JSX. For example, ```2 + 2, user.firstName, or formatName(user)``` are all valid JavaScript expressions.

In the example below, we embed the result of calling a JavaScript function, formatName(user), into an ```<h1>``` element.


<br>

## **Rendering Elements**


Let’s say there is a ```<div>``` somewhere in your HTML file:

```
<div id="root"></div>
```
We call this a *“root”* DOM node because everything inside it will be managed by React DOM.


Applications built with just React usually have a single root DOM node. If you are integrating React into an existing app, you may have as many isolated root DOM nodes as you like.

To render a React element, first pass the DOM element to ```ReactDOM.createRoot()```, then pass the React element to root.```render()```:

```
const root = ReactDOM.createRoot(
  document.getElementById('root')
);
const element = <h1>Hello, world</h1>;
root.render(element);
```

<br>

## **Handling Events**

The difference bewteen handling React events and handling DOM events are:

    - React events are named using camelCase, rather than lowercase.
    - With JSX you pass a function as the event handler, rather than a string.


1. For example, the HTML:
```
<button onclick="activateLasers()">
  Activate Lasers
</button>
```


is slightly different in React:

```
<button onClick={activateLasers}>
  Activate Lasers
</button>
```

2. Another difference is that you cannot return *false* to prevent default behavior in React. You must call``` preventDefault``` explicitly. For example, with plain HTML, to prevent the default form behavior of submitting, you can write:
```
<form onsubmit="console.log('You clicked submit.'); return false">
  <button type="submit">Submit</button>
</form>
```


In React, this could instead be:

```
function Form() {
  function handleSubmit(e) {
    e.preventDefault();
    console.log('You clicked submit.');
  }

  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}
```