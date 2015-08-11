#Custom Filters

We've seen how to use Angular's built-in filters like `currency`, `number`, and `uppercase`.  These are definitely useful, but we often will need to create custom filters to format data to meet our specific needs.

**EXERCISE: Come up with a situation where you would want to create a custom filter.**

We're going to start by creating a "snake_case" to "kebab-case" filter.  We want to be able to write: `{{"hello_class" | kebab}}` and see "hello-class" in the view.

We need to start by defining a filter named "kebab".  In `filters.js`:

```
 app.filter('kebab', function () {
 
  });
```

Remember that filters are just functions to which we pass input and get some returned output to display.  Every filter needs to return a function that takes a single argument:

```
 app.filter('kebab', function () {
    return function (input) {
    };
  });
 
```

The last step is to write our logic inside of the returned function.
 
**STOP! Think about how you would write the code to convert to kebab-case. Try it on your own first before you move on**

Here's a possible solution that will replace all `_`'s with `-`'s:

```
 app.filter('kebab', function () {
    return function (input) {
        return input.replace(/_/g , "-");
    };
  });
```

**EXERCISE: Fix our `kebab` filter so that it doesn't break when you pass it a non-number input.  It should just return the unaltered input.**

**EXERCISE: Write a `camel` filter which will take EITHER a snake_cased or kebab-cased string and convert it to camelCase. So `{{"hello-world" | camel}}` should display "helloWorld", and `{{"hello_world" | camel}}` should also display "helloWorld"**

**EXERCISE: Write a `pigLatin` filter which converts a given string to Pig Latin.  Learn the basics of Pig Latin [here](http://www.wikihow.com/Speak-Pig-Latin).**

**EXERCISE: Create a filter called `redact` which will remove all instances of a provided word from a string and replace it with "REDACTED". `{{"My dog Rusty is adorable" | redact: "Rusty"}} should return "My dog REDACTED is adorable". You will need to research creating custom filters that take parameters.**
