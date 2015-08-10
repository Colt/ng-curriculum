#Intro to Controllers

In MVC, controllers provide properties and functionality for use in the view.  Angular controllers are no different.  They are just functions that provide data for use in the views.

Angular takes care of the hard part: connecting our controllers and views together.  All we have to do is add various properties to the `$scope` and use them inside of our views.

When a new controller is created, Angular automatically gives it a brand new `$scope`. The `$scope` object is a JS object that glues together controllers and views.  Properties that are on the `$scope` object are available to the view and the controller. This will make more sense after a few examples!

**All properties added to the `$scope` are automatically available in our view.**

Let's write our first controller! Inside a new JS file `app.js` add

```
var app = angular.module("firstApp", []);
app.controller("MyFirstController", function($scope){
	$scope.name = "Severus Snape";
})
```

The first line tells Angular to create a **module** named `firstApp`.  `angular.module('firstApp', [])` returns a new module which we use on the next line when we call `.controller()` on `app	`.

Back in our view, we need specify which module our `ng-app` should use.  Update our `<html>` element to `<html ng-app="firstApp">`.

**Question: What are Angular modules?  Why use them?**

We're declaring a new controller named "MyFirstController".  The first argument to `.controller()` is just the name of the new controller, and the second argument is a function that defines the functionality of the controller.  Inside of "MyFirstController", we're adding a `name` property to the `$scope` with the value "Severus Snape". 

Note: This is just one way of writing a controller and adding properties to the `$scope`. We will discuss some others in the "Controllers Revisited" lesson.

Now let's use the `name` property inside of our view.

Before we can access the `name` property, we need to specify which part of our template is "inside" of of our controller.  To do that, we use the directive `ng-controller`.

In `index.html`, add the following code:

```
	<div ng-controller="MyFirstController">
	</div>
```

Just like `ng-app` declares that the elements inside of a particular element are part of an Angular app, `ng-controller` declares that the elements in side of a particular element belong to a controller.

Now we have access to any properties that we set inside of MyFirstController, as long as we access them within the `<div>`.

Let's reuse our code from the very first example.  Try this

```
	<div ng-controller="MyFirstController">
		<h1>My name is: {{name}}</h1>
		<input type="text" placeholder="What is your name">
	</div>
	
```	

When you run this in your browser, you'll see that the initial value that we set for `name` in our controller is displayed both inside of the text `input` and in the `h1`.  When we refer to `name`, angular automatically looks for a property called `name` on the `$scope`.

Try moving the `h1` and `input` somewhere outside of the `div`.  Notice that we no longer have access to the initial value of "Severus Snape".  

**Why doesn't this cause an error message?**

To wrap up, according to the Angular Docs you should use controllers to: 

* Set up the initial state of the $scope object.
* Add behavior to the $scope object.

**EXERCISE: Write another controller called "ExercisesController" which you will use for the next 3 exercises.**

**EXERCISE: Add a property called `FavColor` and give it an initial value of your favorite color.  Display it in the view**

**EXERCISE: Add another property called `secondsInACentury`.  It should be equal to the number of seconds in a century(don't worry about leap years and leap seconds).  Make sure you actually calculate the answer with code, instead of just looking it up.  Finally, display the answer in your template inside of an `h3` tag.  Use a built-in filter to format the huge number with commas in the right place.**
  
**EXERCISE: Create a property called "rightNow" in the controller that is equal to the current time(use a built-in JS function to find the time)  Display it in the view and format it nicely(using a built-in filter) so that it looks something like this: Sunday, October 20, 2015**

Questions: 

* What the hell is `$scope`?
* What are Angular modules?
* Why do we pass in `$scope` as an argument to controller functions?

Resources:

* [Controllers Docs](https://docs.angularjs.org/guide/controller)


