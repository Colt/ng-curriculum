#Routing

One of Angular's most important features is its handling of routing and browser history navigation. 

Most single page apps actually consist of multiple "pages" or "screens". For example, we might have views for a landing page, login page, and signup page. Let's take our reddit clone example.  What if we wanted to add a "show page" for an individual post?  When a user clicks on a particular post, they see a view with details about the post.

A good example of this is gmail. gmail has different views for your inbox, viewing a specific email, composing a message, viewing starred emails, viewing spam etc.  The app is still a single page app, you just don't see everything at once.

**EXERCISE: Open up your gmail(or similar email provider) account. Try clicking around and accessing the different features.  Pay special attention to the url bar.  What do you notice?**

Typical issues with complex single page apps are:

* SPA's don't support browser history navigation.  The back and forwards buttons don't work.
* You can't bookmark parts of a SPA
* If all of our code is in a single template, things can get incredibly messy

Angular provides solutions for all of the above issues through it's router.  We can break out a view into multiple smaller views that are rendered inside of a layout depending on the URL the user is currently accessing.

We'll see how to use the `$routeProvider`, to make use of the browser’s history navigation and allow users to bookmark and share specific pages based off of the current URL.  Let's get started.

First we need to include the `ngRoute` module. It's a separate module that we need to include on our own. You can download the module or link to this CDN: "http://ajax.googleapis.com/ajax/libs/angularjs/1.4.3/angular-route.js"

Next, we need to load the `ngRoute` module by adding it as a dependent module.

```
var app = angular.module("yourAppName", ['ngRoute']);
```

Our `index.html` will act as our layout file.  Just like in Rails, we'll add all the common markup(navbar, footer, etc.) to our layout file, and then we'll render specific views in a particular place in our layout.  Instead of the `yield` ERB tag in Rails, we'll use the `ng-view` directive.  Add the following to `index.html`:


 ```
 
  <h1>NAVBAR</h1>

  <div ng-view></div>

  <h1>FOOTER</h1>
  
 ```
 
 According to the docs: 
 
 > The ng-view directive is a special directive that’s included with the ngRoute module. Its specific responsibility is to stand as a placeholder for $route view content. It creates its own scope and nests the template inside of it.
 
Next, let's declare some routes. To add a route to a module, we use the `config` function.  In our `app.js` file, add:

```
app.config(function($routeProvider) {
    $routeProvider
      .when('/', {
        templateUrl: 'partials/home.html',
        controller: 'HomeController'
      })
      .when('/dogs', {
      	templateUrl: 'partials/dogs.html',
      	controller: 'DogsController'
      })
});

```

**EXERCISE: Before reading on, take time to understand the above code on your own, and make it work. The end goal is to have 2 routes that display 2 different templates.  It's up to you to decide what to put in the templates. The above route declarations tell you exactly what files you need to create. Go write them!**

**EXERCISE: Seriously, do the above exercise.  Don't just move on to see the answer!**

The above route declarations define two routes: '/' and '/dogs'.  When a user visits '/', Angular will render the `partials/home.html` file inside of our layout file and set the `HomeController` as the controller on the `ng-view`. When a user visits '/dogs', Angular will render the `partials/dogs.html` file inside of our layout file and set the `DogsController` as the controller on the `ng-view`.

To make this work, we need to create 2 templates and 2 controllers.  Let's start with the `/` route.  Create a controller in `controllers.js` named `HomeController`:

```
app.controller('HomeController', function($scope){
});
```

Let's add a property to the scope called `message`.  Set it to whatever you want:

```
$scope.message = "Welcome!"
```

Now let's create the template.  Inside of `app/partials` create a `home.html` file.

```
	<p>This is the home template</p>

	<p>Message: {{message}}</p>
```

Make sure when you visit `localhost:8000`, you see the above template rendered between the header and footer we created earlier.  Let's repeat the same process for the '/dogs' route.  

Controller:

```
app.controller('DogsController', function($scope){
	$scope.message = "Woof Woof!"
});
```

Template:

```
	<p>This is the dogs template</p>

	<p>Message: {{message}}</p>

```

Make sure the second route works correctly by visiting `http://localhost:8000/#/dogs`. Play around with the browser navigation buttons.  Try bookmarking a page.  It should all work!

**QUESTION: Why does Angular put a `#` in the route path?** 

**EXERCISE: Figure out how to set a "catchall" route that will render the `home.html` template if the user visits any other route**

**EXERCISE: Make a simple portfolio site using Angular.  It should have 3 routes: "projects", "bio", and "resume".  Add a Bootstrap navbar to the layout file with links to all 3 routes. Figure out how to have the navbar reflect the current route that a user is on.**

**EXERCISE: Make a simple route-based calculator.  When a user visits "/add/4/10", display "14".  Do the same thing for division.  To accomplish this, your routes will need to have path variables.  Research how to define variable segments in your route.  Next, you'll need to research how you access the value of path variables inside of a controller.  You'll need to find the angular equivalent of the `params` hash in rails**

**EXERCISE: Refactor the above exercise so that your calculator works using the query string.  When a user visits "/add/?x=4&y=10", display "14".  You will need to research how to access query string data inside of a controller.**

**EXERCISE: Configure Angular so that routes do not contain `#`'s. Research!**

Questions:

* Why isn't `ngRoute` part of Angular core?  Name at least 2 other Angular modules we could use
* Compare and contrast client-side routing with server-side routing
* Aside from route definitions, what else can go in a `.config()`?
* What is `$rootScope`?
* What is the `$routeChangeSuccess` event?