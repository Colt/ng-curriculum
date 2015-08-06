##Expressions and Built-In Filters

Angular expressions are "Javascript-like snippets that are usually placed in bindings like "{{ expression }}".  We've already used expressions to render a property that we set using `ng-model`.  However, expressions are not just limited to displaying single properties.

Try writing some simple expressions like:

* `1 + 2 = {{1 + 2}}`
* `My name is {{"BoJack" +  " Horseman"}}`
* `The array [99,43,22] is {{ [99,43,22].length }} items long.`

You might think that Angular expressions are similar to the `<%= %>` tags in EJS or ERB.  While they are definitely similar, there are a few key differences.  The most important difference is that **you cannot write conditionals or loops inside an expression**.  We'll see soon that Angular provides its own ways of achieving the same functionality.

Just like with EJS or ERB templates, you do not want to have complex logic in your views.  If you want to run more complex code, we'll see how to move logic to a controller shortly.

Another key difference is that we can use Angular filters inside of expressions.  Filters are simply bits of code that format data before displaying it.  Angular comes with a few built-in filters, and we'll also see how to define custom filters later on.  Let's try using one:

Add the following expression to your markup:

```
{{3.14159265359}}
```

We can use built-in filters to format our long number. The syntax to use a filter is `{{ expression | filter }}`.

Let's try using the built-in `currency` filter to display the above numbers as a price:

```
{{3.14159265359 | currency}}
```

Notice that this filter does 2 things for us: it rounds the data to 2 decimal places and prepends a dollar sign.


**QUICK EXERCISE: Change the above code so that our currency filter uses a Euro symbol instead of a Dollar sign.  It should display "€ 3.14".  You'll need to do some research of your own.**

**EXERCISE: Add a text input to a page that displays user input in all caps and all lowercase. You will need to use 2 built-in filters that we haven't covered. Use the following gif as a reference**

![](http://zippy.gfycat.com/CookedWelcomeDesertpupfish.gif)

Let's try using another built-in filter to format our data.  Angular has a `number` filter that allows us to round numbers to specific decimal places.  Try the following:

```
{{3.14159265359 | number:3}}
{{3.14159265359 | number:6}}
{{3.14159265359 | number:1}}
```

**EXERICSE: Create a drop down menu where the user can select how many digits to round pi to.  It should work like the following gif. BONUS: Find out how to pluralize "digit" correctly. Angular comes with a built-in way of pluralizing things!**

![](http://zippy.gfycat.com/LegalThickIndochinesetiger.gif)


**EXERCISE: Create a simple tip calculator using the basic Angular concepts that we've covered so far(and nothing more advanced).  A user can enter a meal price into an input, then select a percentage to tip from a dropdown menu.  Display the resulting tip at the bottom of the page. Check out the following gif to see how it should work.**

![](http://zippy.gfycat.com/FlamboyantQuickGordonsetter.gif)

**EXERCISE: With one single expression, prove that the context angular expressions run is not the window object.  What is it instead?**
