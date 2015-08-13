#Built-In Directives

Directives are Angular's way of extending HTML.  Angular uses directives to add functionality to HTML elements and attributes. According to the docs:

> At a high level, directives are markers on a DOM element (such as an attribute, element name, comment or CSS class) that tell AngularJS's HTML compiler to attach a specified behavior to that DOM element or even transform the DOM element and its children.

There are 4 ways of writing directives, but it's best practice to only write them using **tag names** like `<pop-up-dialog></pop-up-dialog>` or `<side-bar>`, and **attributes** like `<span fav-spell="expecto patronum"></span>` or `<div weather-widget="94114"></div>`.

Angular comes with a bunch of built-in directives, some of which we've already used.  We will focus on built-in directives for now, but soon we will write our own custom directives.

**EXERCISE: Name at least 3 built-in directives that we have used so far.**

Here's a complete-ish list of Angular's built-in directives in no particular order:

* ng-repeat
* ng-hide
* ng-href
* ng-class
* ng-src
* ng-app
* ng-show
* ng-click
* ng-disabled
* ng-checked
* ng-selected
* ng-model
* ng-style
* ng-disabled
* ng-readonly
* ng-include 
* ng-switch
* ng-controller
* ng-view
* ng-if
* ng-init
* ng-bind
* ng-cloak
* ng-bind-template
* ng-model-options
* ng-change
* ng-form
* ng-submit

We're going to start by talking about a few of the most common built-in directives

###ng-repeat

`ng-repeat` will iterate over a collection and create a template for every item in the collection.  Think of it as the Angular equivalent of a `forEach`.  It's extremely useful. Let's try an example:

Let's start by defining a collection. In a controller, add the following:

```
	$scope.names = ["Harry", "Ron", "Hermione", "Sirius", "Hedwig", "Tonks"];
```

Now let's iterate through the `names` array in the template.  In `index.html`(make sure you have declared `ng-controller` correctly) add the following:

```
	<ul>
		<li ng-repeat="name in names">
			{{name}}
		 </li>
	</ul>
```
**EXERCISE: Add a property called `symbols` with the value `["&spades;", "&clubs;", "&hearts;", "&diams;"]`.  Use an `ng-repeat` to display each one in the template.  
BONUS: Figure out how to make these entity codes actually display as symbols,like the following image**

![](http://content.screencast.com/users/ColtSteele1/folders/Jing/media/d75c95af-4729-4b8f-bf84-3b98a87f3213/00000003.png)

**EXERICSE: Try using `ng-repeat` to iterate through an array with some duplicates, like `[1,1,2,5,6,9,9,9]`.  What happens?  Research how `ng-repeat` handles duplicate data and how to "fix" this issue.**

**EXERCISE: Use `ng-repeat` to iterate through the attributes(keys) of an object and list them on in the template**

###ng-show/hide

`ng-show` and `ng-hide` will show or hide a specific HTML element based off of a provided expression.  Let's take a look at some examples.

```
	<div ng-show="3 + 4 == 5"> 
		3 + 4 isn't 5, don't show
	</div>
	
	<div ng-show="3 + 4 == 7">
		3 + 4 is 7, do show
	</div>

	<div ng-hide="3 + 4 == 5">
 		3 + 4 isn't 5, don't hide
	</div>

	<div ng-hide="3 + 4 == 7">
		3 + 4 is 7, do hide
	</div>

```

The element is hidden when the expression provided to `ng-show` attribute is false. `ng-hide` will hide an element when the expression given to ng-hide is true.

**EXERCISE: Inspect an element that is hidden by ng-show/hide in the browser.  What does Angular do to hide an element?**

**EXERCISE: Create a simple password validator like the one shown below.  If the password is less than 6 characters, hide the submit button and show the error message.  Otherwise, show the button and hide the error**

![](http://zippy.gfycat.com/FelineEqualElectriceel.gif)

###ng-class

`ng-class` will dynamically set an element's class depending on a provided expression.

Define the following CSS class:

```
	.highlight {
		background-color: yellow;
	}
```

We can use `ng-class` to selectively apply our "highlight" class to elements.

```
	<div ng-class="{highlight: 4 + 4 == 8}"> 4 + 4 = 8</div>
	<div ng-class="{highlight: 4 + 4 == 10}">4 + 4 = 10</div>
```


**EXERCISE: Build on top of the previous password validator exercise.  Use `ng-class` to make the form and character count green when valid and red when invalid.  Take a look at the following gif:**

![](http://zippy.gfycat.com/ActualBeautifulIzuthrush.gif)


**FINAL EXERCISE: Build a simple camera shop interface using the data provided below.  Display each camera's title, image(look into `ng-src`), price, and rating.  If an item's "onSale" property is true, display the words "ON SALE!!" and give the price a yellow color.  A user should be able to sort by price or rating.  You'll need to research how to accomplish this."**

![](http://zippy.gfycat.com/UnsteadyDampCanine.gif)

Use the following data:

```
	[
		{
			title: "Nikon D3100 DSLR",
			image: "http://ecx.images-amazon.com/images/I/713u2gDQqML._SX522_.jpg",
			rating: 3.4,
			price: 369.99,
			onSale: true
		},
		{
			title: "Canon EOS 70D",
			image: "http://ecx.images-amazon.com/images/I/81U00AkAUWL._SX522_.jpg",
			rating: 2.0,
			price: 1099.0,
			onSale: false
		},
		{
			title: "Nikon D810A",
			image:"http://ecx.images-amazon.com/images/I/91wtXIfLl2L._SX522_.jpg",
			rating: 4.2,
			price: 3796.95,
			onSale: true
		}
	]
```


Questions

* Why use `ng-src` and `ng-href`?
* What are directives?
* Does ng-class require an object to be passed in?
* What order does an ng-repeat display items in?
* How does ng-repeat handle duplicate data?
