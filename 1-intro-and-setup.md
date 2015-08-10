#Introduction and Setup

###How This Curriculum Works

This Angular curriculum is largely self-driven.  I'm giving you all the lessons for Unit 1 up front.  They are part tutorial, part homework assignment.  Be prepared to do some research of your own to complete these lessons.

Here's an overview of the Angular content:

Unit 1:

 * Intro and Setup
 * 2 Way Data Binding
 * Expressions and Filters
 * Intro to Controllers
 * Built-In Directives
 * Angular Events
 * Unit 1 Assessment Reddit Clone

Unit 2:

 * Routing
 * Custom Filters
 * Controller Revisited
 * Debugging Angular Apps
 * Form validations
 * Dependency Injection
 * HTTP Service
 * Custom Services/Factories
 * Structuring Angular Apps for 2.0
 * Custom Directives
 
Unit 3:

 * Angular + Firebase Intro
 * Firebase Auth
 * Angular + Express
 * Angular + Rails

Before you move on to the next lesson, you should:

* Complete all exercises and SAVE EVERY EXERCISE FOR FUTURE USE
* Answer all questions in ONE MARKDOWN FILE

This is completely self-paced, but we will be tracking your individual progress.  In order to to do that, we will need to assess your knowledge as we go. **Be prepared to show your exercises to instructors and engage in discussions about the questions. We will record your performance** 

Let's get started!

###What is Angular?

According to the official Angular introduction, Angular is a:

> client-side technology, written entirely in JavaScript. It works with the long-established technologies of the web (HTML, CSS, and JavaScript) to make the development of web apps easier and faster than ever before.

It boils down to this: **Angular helps us build complex, single-page applications very quickly.**

###Setup

We're going to start by setting up a very simple Angular app. Soon we'll learn about patterns for structuring complicated Angular apps, but for now we're just going to use a single `index.html` file with a few scripts.

* Create an `index.html` file.
* Add Angular.  For now were going to use this CDN: `https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.4.3/angular.js`.
* Add jQuery.  jQuery is (sort of) a dependency of Angular. 
* Add `ng-app` to the `<html>` element in your document.  This declares everything inside of the `<html>` element part of an Angular app. We will see this 'ng' prefix a lot in Angular.
* Test it out!  Add the following line anywhere inside of the `<body>` tag: `{{1 + 6}}`.  Open the page in your browser.  If Angular is setup correctly, you should see `7` displayed.

Questions:

* Why learn Angular JS over other frameworks like Angular, Backbone, Knockout,etc?
* People have some very strong opinions about Angular.  What are 3 common complaints people have about Angular?
* Is Angular an MVC framework?
* Why did I say jQuery is "sort of" a dependency of Angular? Does it depend on it or not?!
* Read the docs for `ng-app`. What is it and what does it do?

Resources:

* [Angular Docs](https://docs.angularjs.org/api)

