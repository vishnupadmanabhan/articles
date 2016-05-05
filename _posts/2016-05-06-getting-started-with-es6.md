---
layout: post
title:  "Getting Started with ES6"
excerpt: "The new JavaScript - ES6. It's cool."
banner: http://res.cloudinary.com/neoelemento/image/upload/v1462390494/blog/es6-min.jpg
author: "Vishnu"
date:   2016-05-06 00:01:00
categories: ES6, javascript, programming
---
Being in tech is at times overwhelming. There is always scope to learn more and if you are not able to keep up with the industry, you are going to be left behind at some point. There are so many new languages, frameworks, workflows and techniques coming out every day that it is hard to keep up. But to stay relevant in your area it is important to see the trend and prepare yourself for the future. 

One particular area where I have seen this trend in the past few years is in the JavaScript world. This last decade has seen so mch change in the JavaScript world more than in any other platform. Right from the creation of jQuery to frameworks like Angular, React and Vue, JavaScript has been growing in leaps and bounds.

## JavaScript is cool
Let's admit it. The world seems to be swayed away by JavaScript in the past few years. Every other day there is a "cool" new framework coming out and there is a lot of movement happening in the JavaScript space. So if you are anything like me, following the tech community, you would've come across the term **ECMAScript**, particularly **ES6** or **ES2015**.

JavaScript is a language that has really progressed in the [last few years](http://neoelemento.com/blog/2015/10/24/javascript-everywhere/). So what is all this hype around ES6? What is it got to do with JavaScript? Should you learn JavaScript or ECMAScript?

I am writing this post to give a brief intro to ES6 and some of its features and by no means is this a complete guide. There are excellent resources on the internet to learn ES6. My intention is to get the reader excited to at least go and explore ES6 for a bit.

## EcmaScript?
JavaScript core features are defined using ECMA standard. The language defined in the standard is called ECMAScript. JavaScript and Node.js are basically implementation or supersets of ECMAScript. ECMAScript 6 reached it feature complete status in the year 2015. Hence the name ES2015. But they are both the same. Feel free to refer them anyway you need.

### Using it today
As of today, the browsers and Nodejs community are actvely moving towards providing ES6 support. The latest edition of Chrome supports almost 95% of all ES6 features. Due to this inconsistancy amongst browsers, often ES6 code needs to be compiled into vanilla (ES5) JavaScript to be able to run across all browsers. Strictly speaking, the term **transpiling** seems to be more appropriate as the process is transformation of a version of JS to it's lower version to ensure support and there is no actual compilation going on.

There are various transpilers in the market today like traceur.js, babel.js. Babel is a popular transpiler. Using Babel, you can use all of ES6 features without worrying about browser support. You just link to the transpiled version of your JavaScript to your app and you are good to go. Let's take a look into setting up Babel. Feel free to look into Babel documentation as they have support for almost all of the build processes like Gulp, Grunt etc.

Now if you are not a fan of these build processes and command line stuff, there are GUI alternatives like [Prepros](https://prepros.io) which works well and compiling/transpiling is much simpler. We will briefly touch upon both using babel and Prepros.

#### Using Babel

To start using Babel for your projects, within your project folder create a `package.json` file. This file contains the details of all the dependencies that need to be the part of the project and pull them through Node Package Manager (npm). Using the command line way of installing Babel, type the following into your terminal window:

{% highlight bash %}
~ $ mkdir myProj
~ $ cd myproj
~ $ touch package.json > {}
~ $ npm install --save-dev babel-cli
{% endhighlight %}

Once the installation is done, the `package.json` will look something like this, depending on the version of Babel you are installing:

{% highlight json %}
{
  "name": "my-project",
  "version": "1.0.0",
  "devDependencies": {
    "babel-cli": "^6.0.0"
  }
}
{% endhighlight %}

Now that we have Babel installed, lets add a build script to our `package.json` so that we can add it to our npm build process.

{% highlight json %}
{
   "name": "my-project",
   "version": "1.0.0",
   "scripts": {
     "build": "babel src -d build" // specifies the source and destination folders
   },
   "devDependencies": {
     "babel-cli": "^6.0.0"
   }
}
{% endhighlight %}

Now, instead of running Babel from comman line we can simply run the following command from the terminal and get the transpiling done. Note that the source and destiantion directories, in this case `src` and `build` respectively are specified as the parameters:

{% highlight bash %}
~ $ npm run build
{% endhighlight %}

One thing to note here is that Babel comes with a number of transformations and not just ES6 transformations. Before Babel 6 was released, the transformation to ES6 (ES2015) was included by default. But from Babel 6, you need to be explicit about the transformations that need to be included. This si done by including **presets**. ES6 transformation can be included by adding the `es2015` preset like follows:

{% highlight bash %}
~ $ npm install babel-preset-es2015 --save-dev
{% endhighlight %}

Alternatively you can add a `babelrc` file to your project root and include the plugins there as follows:

{% highlight bash %}
echo '{ "presets": ["es2015"] }' > .babelrc
{% endhighlight %}

#### Using Prepros

Prepos is a wonderful GUI application that eases the build process by doing various compilation and preprocessing tasks. As per their [website](https://prepros.io), it is a tool to compile LESS, Sass, Compass, Stylus, Jade and much more with automatic CSS prefixing, It comes with built in server for cross browser testing. Built using Github's Electron framework, the same thing that powers VSCode and Atom editor, Prepros provides a sleek UI. It runs on Windows, Mac OS X and Linux. So it is a cross platform tool and I have tried it and it is wonderful.

Prepros is **free for evaluation without time limits** but continued use should be by purchasing a licence. Using it is pretty straight forward. You open the project in Prepros by dragging your project folder into it or by opening through the menu. Once your project is added, you'll be able to see the files as follows:

<a data-flickr-embed="true"  href="https://www.flickr.com/photos/neoelemento/26224672463/in/dateposted/" title="Prepros_001"><img src="https://farm8.staticflickr.com/7463/26224672463_94e087e520_b.jpg" width="100%"  alt="Prepros_001"></a><script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>

Once you select your source JavaScript file, you'll have an options pane towards the right where you can set the `destination folder`, `auto compile` (compile on file content change), `uglify` (minifying the js), `convert ES6 to ES5` (which is what we need) etc. This is all taken care through the user interface. This is why this is a handy tool to have in your arsenal.

Once you have set this up, you are ready to write some ES6! Let's move.

### Syntax
Once you have the transpiler setup, you can write code like this:

{% highlight javascript %}
class Car {
    constructor(name) {
        this.name = name;
    }    
    start() {
        return this.name + ' started';
    }
}
console.log(new Car('Aston Martin').greet());
{% endhighlight %}

The above code transpiles into something like this in ES5:

{% highlight javascript %}
'use strict';

var _createClass = function () { function defineProperties(target, props) { for (var i = 0; i < props.length; i++) { var descriptor = props[i]; descriptor.enumerable = descriptor.enumerable || false; descriptor.configurable = true; if ("value" in descriptor) descriptor.writable = true; Object.defineProperty(target, descriptor.key, descriptor); } } return function (Constructor, protoProps, staticProps) { if (protoProps) defineProperties(Constructor.prototype, protoProps); if (staticProps) defineProperties(Constructor, staticProps); return Constructor; }; }();

function _classCallCheck(instance, Constructor) { if (!(instance instanceof Constructor)) { throw new TypeError("Cannot call a class as a function"); } }
var Car = function () {
    function Car(name) {
        _classCallCheck(this, Car);
        this.name = name;
    }
    _createClass(Car, [{
        key: 'start',
        value: function start() {
            return this.name + ' started';
        }
    }]);
    return Car;
}();
console.log(new Car('Aston Martin').greet());
{% endhighlight %}

Looks scary? Don't worry about it, that is for your browser to read and understand, for you it is a very familiar `class` syntax which is similar to languages like c++, php etc.

## Bit about the language
Now that we have a little insight into what ES6 has to offer, let's look a little bit more into the what is new in ES6.

### Variable declaration (let and const)
If you come from JavaScript world the variable declaration using `var` keyword would be pretty familiar. In ES6, there are two additional keywords for variable declaration:

- let
- const

To understand why we have these additional keywords, let's take a little detour and look into a something special that JavaScript does.

### Variable hoisting 

Let's look at the following sample code:

{% highlight javascript %}
function onKey(start) {
    if (start) {
        var state = "Vehicle started";
        return state;    
    } else {
        // console.log(state); undefined
        return null;        
    }    
}
{% endhighlight %}

Nothing new there, a straight forward bit og code. when the function executes, if `start` is true, then the variable `state` is assigned a value of `"Vehicle started"`. Else the function returns `null`. Now let's assume, we uncomment the line below `return null` which will log the variable `state` to the console. In this case what would be the output?

{% highlight bash %}
undefined
{% endhighlight %}

You would expect the console to throw up a reference error since the else block should not have access to the `state` variable. The declaration happens within the `if` condition, but the variable is accessible within `else` condition, but just that the value is `undefined`. How can this happen?

This is a little confusing until you understand the concept of **hoisting**. Hoisting in JavaScript means that the declaration of the variable, in our case `state` is hoisted to the top, while the initialization remains within `if` clause. To make this more clear, here is what happens behind the scenes:

{% highlight javascript %}
function onKey(start) {
    var state; // JavaScript hoists the variable declaration
    if (start) {
        state = "Vehicle started"; // initialisation remains here
        return state;    
    } else {
        // console.log(state); undefined
        return null;
    }    
}
{% endhighlight %}

As you can see, JavaScript pulls up the variable and declares it on the top. This is called hoisting. Actually this is the reason why it is considered a best practice to declare your variables at the top.

To avoid this confusion around hoisting, block level declarations were created in ES6. Block level declarations are those where variables that are inaccessible outside of a given block scope. Block scopes, also called lexical scopes, are created within a function or inside of a block like an `if else` statement.

Let's take the same example as above and use `let` instead of `var`.

{% highlight javascript %}
function onKey(start) {
    if (start) {
        let state = "Vehicle started"; // scope is within if block
        return state;    
    } else {
        console.log(state); // throws ReferenceError
        return null;        
    }    
}
{% endhighlight %}

Using `let` keyword, keeps the scope of the variable `state` restricted within the `if` block and does not hoist it to the top. Also using `let` keyword prevents re-declaration. Within the same scope, if a variable is re-decalred, `let` throws an error.

{% highlight javascript %}
var step = 4; // initial declaration of step
let step = 5; // this will throw an error as step is being re-declared
if (something) {
    let step = 5; // this won't cause error as it is within scope of `if`    
}
{% endhighlight %}

So at this point in time, if you are already into ES6, there is no need to have `var` in your code. You can use either `let` or `const` for all your variable declarations.

The `const` keyword is different from the `let` keyword in a way that it is used to declare constants and need to be initialized. A constant value cannot be changed anywhere within the same scope. Similar to `let` declarations a `const` value is not hoisted. 

This might sound like `const` is immutable. In a sense yes, but that being said, a const declaration only prevents modification of the binding and not of the value itself. What this means is that const declarations for objects do not prevent modification of the objects.

{% highlight javascript %}
const step = 4; // step is assigned a value 4
step = 5; // error as const cannot be changed
const age; // error, as const needs to be initialised

// when applied to objects
const car = {
    make: "Aston Martin"
};
car = {
    make: "Jaguar" // error
};
car.make = "Mesarati"; // works fine
{% endhighlight %}

The binding `car` is created with an initial value of an object with a property, but `car.name` can be changed without causing an error because this changes what `car` contains and doesn’t change bound value of `car`. Any attempts to assign a value to `car` which in turn changes the binding, will result in an error. This a bit confusing but the fact is that `const` only prevents modification of the binding, not modification of the bound value. **It just means that the variable cannot be reassigned to something else**.

All this being said, **immutability can be forced as follows**:

{% highlight javascript %}
 const car = Object.freeze([...]);
 {% endhighlight %}

A variable declared using `var` or `const` cannot be accessed until after the declaration. If not, they result in reference errors. Remember, hoisting doesn't happen here.

### Some cool stuff
ES6 should have some tricks up it's sleeve shouldn't it? Being new and all? Oh yeah it does. I am not gonna be able to go into all of those, but will pick up few cool ones. You are going to love these if you are serious about JavaScript :wink:

#### 1. Arrow Operator
Seen this guy? `=>` Yeah the arrow operator. Nothing new eh? You might think, but this guy is really cool in ES6. How? Let's see. Take the following code snippet for example:

{% highlight javascript %}
let getter = function(value) {
    return value;
};
{% endhighlight %}

The same expression can be ES6 using arrow operator. Arrow operator helps in reducing an expression to a much simpler form. Using arrow syntax, the above code can be reproduced as:

{% highlight javascript %}
let getter = value => value;
{% endhighlight %}

Brain damaged eh? :laughing: How cool is that? All your `function` keyword, parenthesis `()` and braces `{}` are out of the window. Let's look at a slightly more complex example.

{% highlight javascript %}
// normal ES5
let fullName = function(firstName, lastName) {
    return firstName + " " + lastName;
};
// Using arrow syntax
let fullName = (firstName, lastName) => firstName + " " + lastName;
{% endhighlight %}

#### 2. Destructuring
One of the coolest things that ES6 offers is something called destructuring. I you are someone who works a lot in objects and arrays, you are going to love this. Since JSON has become a big thing, object and array literals have become most important in the language. Pulling data from these structures is very common practice in any JavaScript app. Let's look at the following example:

{% highlight javascript %}
let car = {
    make:     'Jaguar',
    power:    '300hp',
    topSpeed: 320    
}
let {make, topSpeed} = car; // assigning the variables to object
console.log("The " + make + " goes at " + topSpeed);
{% endhighlight %}

See the magic? :sunglasses: The variable was automatically assigned the value from the object. Same code in ES5 will be like so:

{% highlight javascript %}
var car = {
    make: 'Jaguar',
    power: '300hp',
    topSpeed: 320
};
var make = car.make;
var topSpeed = car.topSpeed;
console.log("The " + make + " goes at " + topSpeed);
{% endhighlight %}

See the ease? Number of lines of code that you save. If nothing, see how clean the syntax is? Go back and read what's written in the banner image again!

#### 3. Template literals
Template strings or template literals are cool like everything else with ES6. This is really helpful in scenarios where you want to insert an HTML snippet withing JavaScript and render it out dynamically. Traditionally, to do this, you would've done something like this:

{% highlight javascript %}
// as strings
var snippet = '<div class="fun">' +
                '<p>Inside of Div</p>' +
              '</div>';  
              
// with a dynamic value
var value = "Inside of div";
var snippet = '<div class="fun">' +
                '<p>' + value + '</p>' +
              '</div>';
              
// as array
var snippet = [
    '<div class="fun">',
    '<p>Inside of Div</p>',
    '</div>'
].join(''); 
{% endhighlight %}

Not to exaggerate, but this a was a big pain! And your code looked like somekind of soup. But with template literals, this can be way simpler and cleaner. Even inserting dynamic values are painless as shown below:

{% highlight javascript %}
// template literal
let snippet = `
    <div class="fun">
      <p>Inside of Div</p>
    </div>
`;
    
// with dynamic variable
let value = "Inside of div";
let snippet = `
    <div class="fun">
      <p>${value}</p>
    </div>
`;
{% endhighlight %}

Few of the JavaScript frameworks like [React](https://facebook.github.io/react/) and [Vue](http://vuejs.org/) use templating for rendering components. This feature is further supplimented by haveing template literals as a feature in ES6.

#### 4. Rest and spread
There are instances where you do not know exactly how many arguments you need to accept. You might want a function where you can accept any number of arguments. This is where the concept of **Rest** comes and helps you out. note that rest here does not mean the traditional restful services type thing. This is what it means:

**Rest Example**
{% highlight javascript %}
// function to add numbers
function sum(x, y, z) {
    return x + y + z;
}
sum(1, 2, 3) // result = 6
{% endhighlight %}

In the above example, the function `sum()` accepts three arguments and when you supply three numbers, it returns the sum. Now imaging you need sum of four numbers. You cannot use the same function as it takes in only three arguments. Now look at the following:

{% highlight javascript %}
// function to add numbers
function sum(...numbers) {
    return numbers.reduce(function(previous, current) {
        return previous + current;
    });
}
sum(1, 2, 3, 4) // result = 10
{% endhighlight %}

In the above example we make use of reduce, which is a higher order function in JavaScript. You can read more about higher order functions [here](http://eloquentjavascript.net/05_higher_order.html). Leaving that aside, see how we used the rest operator with the numbers variable `...numbers`.

**Spread Example**
 
## Conclusion
So, these are the few wonderful things that ES6 gives you. If you are not impressed, then I don't know what will impress you. With all this awesome changes to JavaScript, now is the right time to go and learn ES6 and start building things with it. What I have given here is just a scratch on the surface of the vast world of ES6.

There are numerous resources [like these](https://medium.com/javascript-scene/how-to-learn-es6-47d9a1ac2620#.6oi7c7rnq) on the internet which will give you a headstart to begin with ES6. Go and give it a try, you'll love it. I did.