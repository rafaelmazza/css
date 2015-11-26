# CSS Styleguide

*it's all about the style*

## Table of Contents

  1. [Ecosystem](#ecosystem)
    - [Grid Framework](#grid-framework)
    - [UI Styleguide](#ui-styleguide)
  1. [CSS](#css)
    - [Formatting](#formatting)
    - [BEM](#bem)
    - [ID Selectors](#id-selectors)
  1. [Sass](#sass)
    - [Syntax](#syntax)
    - [Ordering](#ordering-of-property-declarations)
  1. [Predefined Settings](#predefined-settings)
    - [Colours](#colours)
    - [Fonts](#fonts)
    - [Sizes](#sizes)


## Ecosystem

### Grid Framework

Neat is a semantic grid framework built on top of Sass and Bourbon.

[Bourbon NEAT](http://neat.bourbon.io/)

### UI Styleguide

[UI Styleguide](#http://styleguide.carwow.co.uk)

## CSS

### Formatting

* Use soft tabs (2 spaces) for indentation
* Prefer dashes over camelCasing in class names. Underscores are OK if you're using BEM (see [BEM](#bem) below).
* Do not use ID selectors
* When using multiple selectors in a rule declaration, give each selector its own line.
* Put a space before the opening brace `{` in rule declarations
* In properties, put a space after, but not before, the `:` character.
* Put closing braces `}` of rule declarations on a new line
* Put blank lines between rule declarations

**Bad**

```css
.avatar{
    border-radius:50%;
    border:2px solid white; }
.no, .nope, .not_good {
    // ...
}
#lol-no {
  // ...
}
```

**Good**

```css
.avatar {
  border-radius: 50%;
  border: 2px solid white;
}

.one,
.selector,
.per-line {
  // ...
}
```

### BEM

We encourage BEM for these reasons:

  * It helps create clear, strict relationships between CSS and HTML
  * It helps us create reusable, composable components
  * It allows for less nesting and lower specificity
  * It helps in building scalable stylesheets

**BEM**, or “Block-Element-Modifier”, is a _naming convention_ for classes in HTML and CSS. It was originally developed by Yandex with large codebases and scalability in mind, and can serve as a solid set of guidelines for implementing OOCSS.

  * CSS Trick's [BEM 101](https://css-tricks.com/bem-101/)
  * Harry Roberts' [introduction to BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)

```css
.block {}
.block__element {}
.block--modifier {}
.block__element--modifier
```

  * `.block` represents the higher level of an abstraction or component.
  * `.block__element` represents a descendent of .block that helps form .block as a whole.
  * `.block--modifier` represents a different state or version of .block.
  * `.block__element--modifier` represents a different state or version of a .block element.

**Example**

```haml
%form.search-bar.search-bar--active
  %label.search-bar__label
  %input.search-bar__field.search-bar__field--required
```

```css
.search-bar {} /* Block */
.search-bar--active {} /* Modifier */
.search-bar__label {} /* Element */
.search-bar__field {} /* Element */
.search-bar__field--required {} /* Block element modifier */
```

### ID selectors

While it is possible to select elements by ID in CSS, it should generally be considered an anti-pattern. ID selectors introduce an unnecessarily high level of [specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) to your rule declarations, and they are not reusable.

For more on this subject, read [CSS Wizardry's article](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/) on dealing with specificity.

## Sass

### Syntax

* Use the `.scss` syntax, never the original `.sass` syntax
* Order your `@extend`, regular CSS and `@include` declarations logically (see below)

### Ordering of property declarations

1. `@extend` declarations

    Just as in other OOP languages, it's helpful to know right away that this “class” inherits from another.

    ```scss
    .btn--active {
      @extend %btn;
      // ...
    }
    ```

2. Property declarations

    Now list all standard property declarations, anything that isn't an `@extend`, `@include`, or a nested selector.

    ```scss
    .btn--active {
      @extend %btn;
      background: $green;
      // ...
    }
    ```

3. `@include` declarations

    Grouping `@include`s at the end makes it easier to read the entire selector, and it also visually separates them from `@extend`s.

    ```scss
    .btn-active {
      @extend %btn;
      background: $green;
      @include transition(background 0.5s ease);
      // ...
    }
    ```

## Predefined Settings

We have many predefined settings such as:

### Colours
### Fonts
### Sizes
