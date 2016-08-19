#CSS Coding Guidelines

Best practices for writing CSS and Sass in ThoughtWorks.

Bits stolen from or inspired by better guides: [AirBnb](https://github.com/airbnb/css), [Github](http://primercss.io/guidelines/), [Google](https://google.github.io/styleguide/htmlcssguide.xml) and ThoughtWork's own [website styleguide](https://showcase.thoughtworks.com/style-guide).

# CSS Formatting

## Rule declaration
A "rule declaration" is a selector and its accompanying properties. 
* Indent using soft tabs (2 spaces)
  * Spaces are the only way to guarantee code renders the same in any environment
* One space before `{`
* One space after, but not before `:`
* Closing `}` on a new line
* Line breaks between rule declarations
* Be consistent with quotes, naming conventions, etc. 

### Example
```
.one {
  border: 1px solid #fff;
  width: 100px;
}

.two {
  border: 2px solid #fff;
  width: 200px;
}
```

## Selectors
Selectors indicate which elements in the DOM tree will be styled by the defined properties. Selectors can match HTML elements, or an element's class, ID or attributes. 
* Follow [BEM patterns](http://getbem.com/introduction/) for naming to keep your CSS modular and reusable
* If there are multiple selectors, each selector should be on its own line
* Avoid ID selectors, which have unnecessarily high specificity

### Example
```
.block__element--modifier,
.container__title--white {
  color: #fff;
}
```

## Properties
Properties are key-value pairs that give the selected elements of a rule declaration their style. Some recommendations:

Omit units after "0" values and omit leading "0"s in values
```
// Not recommended
margin: 0px;
font-size: 0.8em;

// Recommended
margin: 0;
font-size: .8em;
```

Use shorthand properties where possible
```
// Not recommended
padding-bottom: 2em;
padding-left: 1em;
padding-right: 1em;
padding-top: 0;

// Recommended
padding: 0 1em 2em;
```

Use `0` instead of `none` if a style has no border
```
// Not recommended
border: none;

// Recommended
border: 0;
```

For colors, use lowercase, 3-character hex codes where possible. Use `rgba()` only when transparency is required. 
```
// Not recommended
color: #FFFFFF;
color: rgb(255,255,255);

// Recommended
color: #fff;
```
Note: In SCSS, `rgba()` can accept hex colors like so `rgba(#000, .5)`

# Sass Formatting
* Use the newer `.scss` syntax and file extension, not the original `.sass`
* Use dash-cased variable names, e.g. `$my-variable-name`
* Avoid nesting where possible, and never nest more than 3 levels deep

When selectors are heavily nested, you're probably writing CSS that is: 
* Strongly coupled to HTML
* Too specific
* Not reusable

## Property declaration ordering
1. @extend first, or [avoid @extend](https://www.sitepoint.com/avoid-sass-extend/) altogether 
2. @include 
3. Normal properties
4. Nested selectors, if absolutely necessary, go last with line breaks in between

# Other tips
## Javascript hooks

Avoid binding to the same class in both your CSS and JavaScript to avoid breaking functionality when making changes.

Recommend creating JavaScript-specific classes to bind to, prefixed with .js-:

```
<button class="btn js-request-to-book">Request to Book</button>
```

## Comments
* Prefer line comments (// in Sass-land) to block comments
* Prefer comments on their own line
* Only write comments for code that isn't self-documenting, for example:
  * Uses of z-index
  * Compatibility or browser-specific hacks

## Methodologies

Besides BEM for naming, ThoughtWorks recommends following [OOCSS](https://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/), [SMACSS](https://smacss.com/) and [Atomic Design](http://bradfrost.com/blog/post/atomic-web-design/) patterns. It's a good idea to read up on these methodologies and strategies if you want to write maintainable, scalable code. 
