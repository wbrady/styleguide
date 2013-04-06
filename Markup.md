## Influences
* [Github's Markup Styleguide](https://github.com/styleguide/templates)

## Doctype
A proper Doctype which triggers standards mode in your browser should always be used. Quirks mode should always be avoided. Use the `html5` doctype.

```html
<!DOCTYPE html>
```

## Coding Style
* Always put quotes around attributes.
* Use double quotes `""`.
* Use soft-tabs with a two space indent.
* Indent every nested element or logical statement. For example:
```html
<ul id="users">
  <% users.each do |user| %>
    <li><%= user.name %></li>
  <% end %>
</ul>
```
* Add a new line between attributes when an element has long class or id names and align them by the attribute name:
```html
<p id="incredibly-long-id-name"
   class="very-long-class-name-1 very-long-class-name-2">
  Text
</p>
```

## HTML Guidelines
* Paragraphs of text should always be placed in a `<p>` tag. Never use multiple `<br/>` tags.
* Items in list form should always be in `<ul>`, `<ol>`, or `<dl>` rather than a set of `<div>` or `<p>`.
* Every form input that has text attached should utilize a `<label>` tag.

## Templating
* Write code comments in the templating language rather than HTML: `<%# TODO - fix this %>`
