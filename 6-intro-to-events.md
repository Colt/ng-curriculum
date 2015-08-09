#Angular Events

###ng-click

`ng-click` is used to run a specific method on the current $scope when an element is clicked. Think of it as the Angular equivalent of the `on-click` property.  Let's use it to build a random number picker!

In a controller, let's add a property to the `$scope` called `number`:

```
$scope.number = 5;	
```

Let's display `number` in the template:

```
	<h3>The number is: {{number}}</h3>
	
```

Next, let's add a button which will call `pickRandomNumber()`(we haven't defined it yet) when clicked.

```
	<button ng-click="pickRandomNumber()">Pick Random Number</button>
	
```

Now let's implement `pickRandomNumber()`. Remember that `ng-click` calls a method on the current $scope, so we need to make sure `pickRandomNumber()` is defined on the $scope. Back in your controller, add:

```
	$scope.pickRandomNumber = function(){
		$scope.number = Math.floor(Math.random() * 10) + 1
	}
```

And that's it!  Try clicking your button and watch as the number changes atomically on the screen.

**EXERCISE:  Explain in as much detail as you can what happens when you click the button.  Why does `number` update in the template without us telling it to?**

**EXERCISE: Add a button that will reverse some text when clicked.  Take a look at the example gif below.**

![](http://zippy.gfycat.com/ClosedFreshGar.gif)

**EXERCISE: Create a simple Ping Pong Score Keeper.  It should display the 2 players' scores, have buttons to increment each player's scores, and highlight the winner(assume games only go to 11).  It should also display the current server(switch serves every 2 points).  Lastly, make sure to include a reset button.  BONUS: Keep track of how many games each player wins.**

![](https://i.gyazo.com/40d31881e3774f4f374503920e784931.gif)


**EXERCISE: Contact List.  Create a simple contacts app.  Each contact has a name, email, and phone number.  A user can create new contacts using a form.  A user can search contacts as well(you'll need to research this part). HINT: try binding name, email, and phone as properties on one `newContact` object rather than creating 3 different properties on the `$scope`**


![](https://i.gyazo.com/e1dba3d8e24812690d1af363630af5a6.gif)


###Other Events

There are a bunch of other built-in event directives like

* ng-submit
* ng-change
* ng-mousedown
* ng-mouseenter
* ng-mouseleave
* ng-mousemove
* ng-mouseover
* ng-mouseup

They all work just like `ng-click`.  When a specific event is triggered, they will run a given method on the current $scope.  

**EXERCISE: Add a feature to a previous exercise using one of the event directives listed above**