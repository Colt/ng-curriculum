#Dependency Injection And Services

**Dependency injection** is core feature to angular that helps us make more modular code.

Dependency injection is a software pattern that angular uses to figure out what dependencies (e.g. $scope, $http service, etc) a software component (e.g. a controller, a module, etc) has.  For example, the following controller depends on $scope and $routeParams:

```
app.controller('MathController', function($scope, $routeParams){
  $scope.val1 = parseInt($routeParams.val1, 10);
  $scope.val2 = parseInt($routeParams.val2, 10);
  $scope.op = "";
  $scope.result = 0;
  if ($routeParams.op === "add") {
    $scope.op = "+";
    $scope.result = $scope.val1 + $scope.val2;
  } else if ($routeParams.op === "subtract") {
    $scope.op = "-";
    $scope.result = $scope.val1 - $scope.val2;
  }
});
```

**EXERCISE: Look at an angular app you have made previous (reddit clone or your portfolio site).  What dependencies are there?  Where do you see dependencies other than the contoller?**

**EXERCISE:  In the above example (MathController) does the order of the dependencies matter?  Does $scope have to come before $routeParams?  Do the names matter?  Could we name them something else?**

**EXERCISE: DO NOT SKIP THIS EXERCISE.  In production code, you typically want your javascript file to be as small as possible so that it can be downloaded faster.  To make the files smaller, developers minify their js files.  Find a minification tool and minify your js code.  Update your html file so that it now points to your newly minified js files.  Does your angular app still work?  If it stopped working, what is the problem?**

**EXERCISE: So far we have mainly seen one way to do dependency injection.  Research and figure out the other two ways.  Which one is the best practice?**

![](http://html5hub.com/wp-content/uploads/2013/11/superA.png)

Angular supports 3 ways to define dependencies for your code:

1.  Implicit annotation
2.  Inline array annotation
3.  $inject property annotation

We have been usiing __implicit annotation__ so far.  Implicit annotation is kind of a hack because angular actually has to parse your code and convert the parameters of your function to a string in order to figure out your dependencies.  __The implicit annotation dependency injection will break when you minify your code.__   This happens because minfication tools rename variables to a something smaller, but the minification tool doesn't know that the variable name in the function is meaningful to angular.

__BEST PRACTICE__: Always use inline array annotation.

**EXERCISE: Fix the app you minified earlier to use inline array annotation.  Minify the javascript files again.  Verify that the code still works when using the minified js.**

**EXERCISE: When using inline array annotation does the order of anything matter?  What order should match?**

**EXERCISE: Read over the [angular docs on dependency injection](https://docs.angularjs.org/guide/di).  Try to understand as much as you can.**