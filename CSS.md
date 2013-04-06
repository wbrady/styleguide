## Influences
* [Github's CSS Styleguide](https://github.com/styleguide/css) - I flat out copy a lot of it.
* [Scalable and Modular Architecture for CSS](http://smacss.com/) by Jonathan Snook.
* [The Rails View](http://pragprog.com/book/warv/the-rails-view) by John Athayde and Bruce Williams.

## Coding Style
* Use soft-tabs with a two space indent.
* Keep lines under 80 characters long (if you're using a preprocessor the preprocessed lines only need to be under 80 characters long not the CSS lines that are generated)
* Put spaces after `:` in property declarations.
* Put one space before `{` in rule declarations on the same line as the rule.
* Put the `}` on its own line.
* Put a newline between rule declarations.
* Use 3-digit hex color codes `#000` unless using rgba.
* Use `//` for comments blocks (instead of `/* */`) and use one whitespace between `//` and the comment text.
* Document styles with [KSS](https://github.com/kneath/kss) - ideally
* Properties with multiple values should have each value on a new line aligned (see box-shadow in the following example)
* Organize states in the following order:
  * Box - any property that affects the display and position of the box (i.e. `display`, `float`, `position`, `left`, `top`, `height`, `width`, etc.)
  * Border - `border`, `border-radius` and `border-image`
  * Background - `background`, `background-color`, background-image`, `background-size`, etc.
  * Text - `font-family`, `font-size`, `text-transform`, `letter-spacing`, `word-wrap`, etc.
  * Other
* Use doble quotes `""` for strings

Here is a good example

```css
// This is a good example!
.styleguide-format {
  display: inline-block;
  border: 1px solid #0f0;
  background: rgba(0,0,0,0.5);
  font-size: 12px;
  color: #000;
  box-shadow: 10px 12px 11px #f00,
              20px 21px 21px #000,
              30px 0px  0px  #f00,
}

.other-format {
  background: blue;
}
```

## SCSS, LESS, Stylus
* Any `$variable` or `@mixin` that is used in more than one file should be put in `globals/`. Others should be put at the top of the file where they're used in.
* As a rule of thumb, don't nest futher than 3 levels deep. If you find yourself going further, think about reorganizing your rules (either the specificity needed, or the layout of the nesting).

## Stylus
When using Stylus, do not write the `{`, `:`, or `;` because you don't have to.
So this example in CSS:
```css
.example {
  background: black;
  color: white;
}
```
should be written like this in Stylus
```css
.example
  background black
  color white
```

## File Organization
* Place all base rules (rules that define base styles for elements) into their own file.
* Put each module into its own file.
* Place global states into their own file.
* State rules made for a specific module should reside with the module rules and not with the global state rules.

## Pixels vs. Ems
* Use `px` for `font-size`.
* Use unit-less `line-height` because it does not inherit a percentage value of its parent element, but instead is based on a multiplier of the `font-size`. TODO add a link to an article explaining this

## Class naming conventions
* Never reference `js-` prefixed class names from CSS files. `js-` are used exclusively from JS files.
* Use the `is-` prefix for state rules that are shared between CSS and JS.
* In a case where a state rule is made for a specific module, the state class name should include the module name in it.

## Specificity (classes vs. ids)
Elements that occur **exactly once** inside a page should use IDS, otherwise, use classes. When in doubt, use a class name.

* **Good** candidates for ids: header, footer, modal popups.
* ** Bad** candidates for ids: navigation, item listings.

When styling a component, start with an element + class namespace (prefer class names over ids), prefer direct descendant selectors by default, and use as little specificity as possible. Here is a good example:

```html
<ul class="category-list">
  <li class="item">Category 1</li>
  <li class="item">Category 2</li>
  <li class="item">Category 3</li>
</ul>
```

```css
ul.category-list { // element + class namespace

  &>li { // direct descendant selector > for list items
    list-style-type: disc;
  }

  a { // minimal specificity for all links
    color: #ff0000;
  }
}
```

#### CSS Specificity guidelines
* If you must use an id selector (`#selector`) make sure that you have no more than one in your rule declaration. A rule like `#header .search #quicksearch { ... }` is considered harmful.
* When modifying an existing element for a specific use, try to use specific class names. Instead of `.listings-layout.bigger` use rules like `.listings-layout.listings-bigger`. Think about `ack/greping` your code in the future.
* The class names `disabled`, `mousedown`, `danger`, `hover`, `selected`, and `active` should always be namespaced by a class (`button.selected` is a good example).

## Best practices
* Only include a selector that includes semantics (no `span` or `div`)
* Try to avoid conditional styling based on location. If you are changing the look of a module for usage elsewhere on the page or site, sub-class the module instead. For example rather than write something like this:

```html
<div id="special">
  <div class="button"></div>
</div>

.button {
  // default button styles
}

#special .button {
  // special button styles
}
```

write it like this
```html
<div id="special">
  <div class="button button-special"></div>
</div>

.button {
  // default button styles
}

.button-special {
  // special button styles
}
```

* Only modify state styles with Javascript. Sub-module styles should be applied to an element at render time and should never be changed again.
* Never use !important
* The most important thing is to **be consistent**.
