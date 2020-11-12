# Week-7 -- Day-3

## JSON

**JSON** --> **J**ava**S**cript **O**bject **N**otation.

The internet is an incredibly  large amount of interactions. Requests  are made  and then delivered.

This goes back and forth. With that said in one of those types of interactions, we  request  and respond with JSON objects.

What is JSON object? Well, it's an object. It represents a thing. It can an  almost infinite  amount of data  regarding  this thing. So let's say this thing is a new USER. The new USER process usually starts with a signup  form. User fills out a signup  form  on the web and then submits it. Well, guess what that form data  can be  wrapped up in JSON object and then submitted. So take a look at a simple new USER JSON object:

{name: "Daniel  Ricciardo", country: "Australia", profession: "Professional Driver"}

The defining characteristic of a JSON object are the **{ } (curly braces)**! Whenever you see **{ }** and it's not the body of  a function of  conditional statements it  must be  a JSON object. Let's break down the syntax for a JSON object.

{ key: value, key: value, key:value...}

The three dots are not part of the syntax. The  important  parts are the **curly braces**, a **key then a colon then the value.** You can have multiple key values pairs as long as they are  separated  by a **comma**.

All JSON **values**  must be  one of the following **types**: **string, number, object, array, boolean or null**.

JSON are incredibly important in web-development so I recommend checking out  additional  resources before proceeding. Visit  W3Schools  to learn more about JSON:

https://www.w3schools.com/js/js_json_intro.asp

## package.json

Here is what node.js has to say about package.json:

> All  npm  packages contain a file, usually in the project root, called
> `package.json` - this file holds various metadata relevant to the
> project. This file  is used  to give information to `npm` that allows it
> to  identify  the project as well as handle the project's dependencies.
> It can also contain other metadata such as a project description, the
> version of the project in a particular distribution, license
> information, even configuration data - all of which  can be  vital to
> both `npm` and to the end users of the package. The `package.json`
> file is normally  located at  the root directory of a Node.js project.

The most important is that package.json is JSON type that holds information  regarding  a node project. This information can include what the name of the project is and what packages this project depends on (dependencies). Nerdy fact: when you do  an npm  install in the root directory  npm  installs all the packages listed in the dependencies section of the package.json file.

package.json also  contains  scripts that can do various things like starting up the project or testing this project.

## Express with  ejs  View Engine

What the hell is **ejs** or a **View Engine**?

Well, let's start with view engine or  templating  engine. Here is how express explains it:

> A _template engine_ enables you to use static template files in your
> application. At runtime, the template engine replaces variables in a
> template file with  actual  values, and transforms the template into an
> HTML file sent to the client. This approach makes it easier to design
> an HTML page.

Hmm. you might still be a little confused about template engines based on the definition above.

let me see if I can clarify it a little. A view engine allows you to pass  JavaScript  variables/values to an HTML (view) page. So  for example  you can have a  hard coded  h1  element but the inner text comes from JavaScript.

    <h1><%= header %></h1>

***<%= header %>*** is the  ejs  part. So where ever we load this HTML file we need to  provide  the value for header.

That is as simple as I can put it. I hope that helps.

## Getting started with Express and  ejs  View Engine

Run:

```bash

express name-of-folder --ejs

```

That is it. You just have to make sure you have express installed beforehand.

Check out the following page for more information:

https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/skeleton_website
