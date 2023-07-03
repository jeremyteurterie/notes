---
id: b4mad08hpmecmeggoba5k8v
title: Intro
desc: ''
updated: 1686990558066
created: 1686990544108
---
# Intro To The DOM

Alright, so now we get to get to the fun stuff, working in the actual browser body and not just in the console. I think one of the big mistakes people make is they jump into the browser too quickly without understanding the stuff that we have talked about so far. Now that you understand control flow, functions, array methods, etc, you will be able to do more within the browser.

## The DOM

The DOM stands for **Document Object Model**, It is essentially a programming interface for web/HTML documents. We already know that we display the content on web pages using HTML tags with text and we style it using CSS. The DOM is the structure of the web page that we can interact with using JavaScript. It generally includes all of the HTML tags, attributes and the text between the tags called "text nodes". The DOM is usually represented as a tree structure.

Let's look at this very simple page structure:

<img width="600px" src="images/basic-html-structure.png">

The DOM representation of this would look something like this:

<img width="600px" src="images/basic-dom.png">

I'll talk about the `window` and `document` objects in a minute, but under that you'll see the structure of this document in a tree structure.

We have the `html` element, which holds the `head` and `body` elements. The `head` element holds the title element, which has a text node inside of it. In this case that would be the text, 'Website'. The `meta` element includes an attribute of `charset` which is set to `utf-8`. So any attributes are going to be accessible in the DOM as well. The `body` element holds the `h1` element, which has a text node inside of it with the text, 'Hello World'. It also has an `id` attribute. Then we have the `p` element with a text node inside of it.

So this is how your HTML document full of tags, attributes and text nodes looks in the DOM.

## The Window Object

A few sections back, we talked about the global `window` object. The `window` object is the top level object in the browser. It is the root of the browser's object hierarchy. It has properties and methods that are available to all of the JavaScript code in the browser. To see the window object's API (methods and properties), you can type `window` in the console or in your code

```JavaScript
console.log(window);
```

# The Document Object

On that `window` object, we have a property/object called `document`. This is an object that represents the HTML document that we are currently viewing. It has all types of properties and methods that we can use to interact with the HTML document.

```JavaScript
console.log(window.document);
```

Since `window` is the top-level object in the browser, we do not need to prefix it with **window**

```JavaScript
console.log(document);
```

Sometimes console.log() will show the properties and methods, but sometimes it will show the element/tag itself. To see all the methods and properties, you can use `console.dir`

```JavaScript
console.dir(document);
```

## Document Properties/Elements

We can access DOM elements directly, such as the `body`

```JavaScript
console.log(document.body);
```

We can also access elements such as links and images. Let's add a link to the HTML

```HTML
<a href="https://traversymedia.com">Traversy Media</a>
```

We can get all of the links with

```JavaScript
console.log(document.links);
```

This returns something called an `HTMLCollection`, which is similar to an array. We can access by index

```JavaScript
console.log(document.links[0]);
```

## Document methods

In addition to properties, the document object has a ton of methods. `document.write()` is a method that will write to the browser body. This is not used very much because you can't really target where you want to output, but it is available

```JavaScript
document.write('Hello From JS');
```

## Document Selection Methods

Getting elements using direct properties is not usually the way you want to do this. There are special methods available that allow us to directly select elements easily. I will be going over all of these in depth soon, but just to give you an example, let's look at `document.getElementById()`, which does exactly that. It allows us to basically grab an element from the HTML document by it's id. Then we could do whatever we want to that specific element including changing the style, removing it, adding an event listener to it and so on. The term `DOM manipulation` just refers to changing the DOM using JavaScript, which again can me adding, removing, changing elements, etc. A lot of the time we change the CSS through JavaScript to make something hide or show based on some user interaction.

Just to give you a very simple example of selecting something from the DOM, let's open an html page and create a new div element with the ID of `main` and just add some text to it.

```html
<div id="main">
  <h1>The DOM</h1>

  <a href="https://traversymedia.com">Traversy Media</a>
</div>
```

Now in our JavaScript file, we can use the `document.getElementById()` method to grab the element with the ID of `main`.

```js
console.log(document.getElementById('main'));
```

Now let's say we want to add some text into the div element. We can easily do that using the `innerHTML` property.

```js
document.getElementById('main').innerHTML = '<h1>Hello World</h1>';
```

This will replace everything in the main element. There are other methods we will get into soon that let us just append or add elements.

So you see, The DOM gives us a lot of power to interact with the HTML document. The code we just wrote is written in JavaScript, but uses the DOM and it's API to access the document and its elements. Even when you start using a front-end framework like React, this is the stuff that it is doing under the hood.

The DOM was created to be independent of any particular language. Yes, JavaScript is definitely the most common language to do this stuff with, but implementations of the DOM can be built for any language, as this Python example demonstrates:

```python
# Python DOM example
import xml.dom.minidom as m
doc = m.parse(r"C:\Projects\Py\chap1.xml")
doc.nodeName # DOM property of document object
p_list = doc.getElementsByTagName("para")
```

## DOM Libraries

I've been doing this for about 15 years now and I know people still complain about JavaScript, but I think very few of them, worked with JavaScript ten+ years ago. Before the big ES6 update, JavaScript was not easy to work with, including accessing and manipulating the DOM. So we had libraries like **jQuery** that were built to make it easier to work with the DOM.

A lot of people ask me if they should learn jQuery and my answer to that now is usually no. If you're genuinely interested in learning it, that's fine. Just make sure you learn the fundamentals of vanilla JavaScript first. You may want to learn jQuery to deal with legacy code. There is a chance you'll run into it in the wild. But do you need to learn it? In my opinion, no you don't.

Alright, so in the next video, I want to examine some of the properties on the browser's `document` object itself.

# Examining the Document Object

Alright, so we know that the DOM is a tree of objects of elements, nodes and attributes. We also know that the `document` object is the root of the DOM tree. It offers extremely helpful methods for us to use to manipulate the DOM including methods to select elements, create elements, and so on. There's also a ton of properties that we can use to get information about the document and that's what I want to look at in this video.

### Shopping List UI

<img src="images/shopping-list.png">

So what you're looking at right now is the UI or user interface for a simple shopping list application. We will be building this project out, but right now, it's only the HTML and CSS, so it's not actually working because there's no JavaScript. There is a JavaScript file linked, but it's empty. That's what we'll be working in to explore the DOM.

You can download the code resources directly from this section, or from the main sandbox GitHub repository.

Let's quickly just look at the structure of this HTML page, so we know what we're working with.

So we have a container that wraps around everything, a heading, then we have a form that has one single text input and a submit button. Under that, we have a filter input to filter the items. Then we have a list of items with an x icon to remove those items. As I mentioned, the functionality of this will not work because we have no JavaScript. Finally, we have a clear all button that will do just that.

So, it's a pretty simple UI, but it's a good starting point for us to explore the DOM.

### Browser Dev Tools

The browser dev tools will be used extensively throughout this course. We've been using the console quite a bit, but I want to check out the `Elements` tab real quick. This is where you can see all of your elements/tags, attributes, text, etc. In reality, you should know some HTML and CSS and you should have at least a little experience with this tab.

We can see the CSS styling here as well. In many cases, we'll be changing styles and adding and removing classes through JavaScript and we'll be using the dev tools to see what's happening.

### The Document Object

So if we type into the console `window`, we see everything that is available to use in the global object and `document` is one of them. You can see that there's a ton of properties and methods available to us. Anything you see here can be used in your JavaScript code.

Let's start off by just logging the document.

```js
console.log(document);
```

<img src="images/dom1.png">

It gives us just that, the entire document including the doctype, html tag and head and body tags with everything in between them.

### `document.all`

```js
console.log(document.all);
```

<img src="images/dom2.png">

`document.all` gives us everything in the DOM in an array-like object called a `HTMLCollection`. It's not an array, but it is structured like one. We can't use methods like `forEach()` and `map()` on it, but we can use bracket notation to access the items. We can also use the `length` property to get the number of items in the collection. There's also a method called `item()` that we can use to get a specific item in the collection.

```js
console.log(document.all.length);
console.log(document.all[2];
console.log(document.item(2));
```

`document.all()` is not a very useful method and it's actually deprecated, so we shouldn't use it. It's better to use methods like `document.getElementById()`. I did want to show you that it exists and give you an example of an HTMLCollection.

### `document.documentElement`

```js
console.log(document.documentElement);
```

This will get you the HTML element and everything in it including both the head and body tags.

### `document.head` & `document.body`

```js
console.log(document.head);
console.log(document.body);
```

These two properties give us the head and body elements. We can get the children of those elements using the `children` property.

```js
console.log(document.head.children);
console.log(document.body.children);
```

These will give us an HTMLCollection of the direct children of the head and body elements. So in the case of the body, we only get the container div and the script tag because those are the only direct children of the body element.

<img src="images/dom3.png">

If I wanted to get the children of the container div, I would have to do something like this.

```js
console.log(document.body.children[0].children);
```

<img src="images/dom4.png">

So now I have a collection of all of the children of the container div. This is a little bit cumbersome and there are better ways to select elements, but let's say I wanted to change the text of the heading. I could do something like this.

```js
document.body.children[0].children[0].textContent = 'Hello World';
```

<img src="images/dom5.png">

### Other Page Properties

Here are some other properties on the `document` object that we can access and manipulate.

```js
document.doctype;
document.domain;
document.URL;
document.characterSet;
document.contentType;
```

### `document.forms`

`document.forms`. This will give us an HTMLCollection of all of the forms on the page.

```js
console.log(document.forms);
```

We can get specific forms in the collection by index or by name.

```js
console.log(document.forms[0]);
console.log(document.forms['item-form']);
```

We can get specific attributes as well

```js
console.log(document.forms[0].id);
console.log(document.forms[0].method);
console.log(document.forms[0].action);
```

We aren't only limited to reading the attributes. We can also change them.

```js
document.forms[0].id = 'new-id';
```

I could add a value to the input like this:

```js
document.forms[0].item.value = 'Hello World';
```

`item` being the `name` attribute of the input.

### `document.links`

To get an HTMLCollection of links, we can use `document.links`.

```js
console.log(document.links);
```

We don't have any links in this specific project, so let's add one just to test it out.

```html
<a href="#" class="my-link" id="link">My Link</a>
```

Now we can see that we have a link in the collection.

We can get specific attributes as well.

```js
console.log(document.links[0].id);
console.log(document.links[0].className);
console.log(document.links[0].classList);
console.log(document.links[0].href);
```

### `document.images`

We can also get an HTMLCollection of images with `document.images`.

```js
output = document.images;
output = document.images[0];
output = document.images[0].src;
```

In the code above, we accessed the attributes directly, but we can also use the `getAttribute()` method.

```js
output = document.images[0].getAttribute('src');
```

This will do the same thing as accessing the `src` attribute directly.

### `document.scripts`

If you want to get an HTMLCollection of scripts, you can use `document.scripts`.

```js
console.log(document.scripts);
```

So as you can see, everything in our HTML document is available to us in the DOM using the document object that the browser creates for us.

This is just the tip of the iceberg. There are so many more properties and methods available. We'll be using them throughout the course.

