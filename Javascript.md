## Influences
* [Github's Javascript Styleguide](https://github.com/styleguide/javascript)

## Coding Style
* Use soft-tabs with a two space indent.
* Use camelCase for variable names.
* Keep lines 80 characters or shorter.
* Include all modules at the top of the file.
* Put a `;` at the end of a statement that defines a variable or calls a function. For example:
```javascript
// here
var foo = "bar";

// here
console.log("bar");

// here
var foo = function() {
  console.log("bar");
};

// but not here
function foo() {
  console.log("bar");
}
```

* Put a space before and after an operation: `foo = "bar"` and `2 + 3 * 4`.
* Put the `{` on the same line as the `function` keyword.
* Put the `}` on its own line.
* Write long arrays like this:
```javascript
var arr = [
  "Lorem ipsum dolor sit amet, consectetur adipisicing elit"
, "Lorem ipsum dolor sit amet, consectetur adipisicing elit"
, "Lorem ipsum dolor sit amet, consectetur adipisicing elit"
, "Lorem ipsum dolor sit amet, consectetur adipisicing elit"
];
```
* Write objects like this:
```javascript
var obj = {
  foo: "bar",
  x: y,
  a: b,
};
```

## Coffeescript
I don't currently use Javascript but haven't decided whether it is best or not.
