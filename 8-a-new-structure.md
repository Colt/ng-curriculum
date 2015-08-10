#A New Structure

As our Angular apps grow we'll need a new file structure.  It won't work to put everything in an `app.js` file when we have multiple controllers, modules, directives, filters, services, and more.  

We're going to start by using the following structure:

```
app
	css
	js
		app.js
		controllers.js
		directives.js
		filters.js
		services.js
	index.html
```

This structure is pretty simple.  We have an app.js file where we will declare our app and all dependencies.  For now it will just look like:

```
var app = angular.module("whateverYourModuleNameIs")
```

We also have files like `controllers.js` and `directives.js` which contain all of our controllers or custom directives(we'll get there soon).  Basically, instead of writing everything inside of `app.js`, we've broken it out into separate files grouped by functionality.

In order for this structure to work, make sure you correctly include all the scripts in your `index.html` file.

**EXERICSE: Convert the reddit clone app to this new file structure**

The next thing we'll want to do is serve up our application using some sort of server.  For now we can just run `python -m SimpleHTTPServer` inside of the app directory.  Visit `localhost:8000` to see the application.

**EXERCISE:Serve your reddit clone app using SimpleHTTPServer.  Make sure everything works correctly.**


Questions:

* What are possible issues with this new file structure?
* Why do we want to serve our application in the first place?  It seems to work fine when we just open `index.html` in the browser...
