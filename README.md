#mishmash

A battle-hardened style guide for modular CSS.

* [HTML](#html)
* [CSS](#css)
    * [Signifying state](#signifying-state)
        * [Possessive and completed states](#possessive-and-completed-states)
    * [File](#file)
    * [Watching files](#watching-files)
* [Naming conventions](#naming-conventions)
    * [Sizes](#sizes)
    * [Instance modifiers](#instance-modifiers)

##The basics

### HTML

```html
<nav class="nav nav--primary">
    <ul class="nav__items">
        <li class="nav__item is-first"><a class="nav__item__link" href="#">Home</a></li>
        <li class="nav__item"><a class="nav__item__link" href="#">Shop</a></li>
        <li class="nav__item"><a class="nav__item__link" href="#">Contact</a></li>
        <li class="nav__item"><a class="nav__item__link" href="#">About</a></li>
        <li class="nav__item is-last"><a class="nav__item__link" href="#">Help</a></li>
    </ul>
</nav>
```

### CSS

The core mishmash syntax is [BEM](http://bem.info)-based.

```css
/**
 * Default .nav class
 */
.nav{
    ...
}
    .nav__items{
        ...
    }
        .nav__item{
            ...
        }
            .nav__item__link{
                ...
            }

/**
 * Example of .nav class with modifier (--alpha)
 * Used: A short note where the class is used i.e. In top header navigation
 */
.nav--alpha{
    ...
}
    .nav--alpha .nav__items{
        ...
    }

/**
 * Example of .nav class with modifier (--beta)
 * Used: In footer navigation
 */
.nav--beta{
    ...
}
    .nav--beta .nav__item__link{
        ...
    }
```

### Signifying State

Make use of State Modifiers to signify a module's state

* `.is-active`
* `.is-selected`
* `.is-hidden`
* `.is-great`
* `.is-loading`

#### Possessive and completed states

* `.has-animated`
* `.has-loaded`
* `.has-dropdown`

### File


## Naming conventions

### Sizes

* `.btn--xxs`
* `.btn--xs`
* `.btn--s`
* `.btn--m`
* `.btn--l`
* `.btn--xl`
* `.btn--xxl`

Can include as many xxxs as you like `.btn-xxxxl`.

### Instance modifiers

Use the NATO Phonetic alphabet when specifying multiple

In this example we are setting Sass variables:

```scss
* $brand-alpha
* $brand-beta
* $brand-charlie
* $brand-delta
* $brand-echo
```

...


## Layout

For layout use the `border-box: box-sizing` property on a global reset so you don't have to worry about padding / border style declarations when using % based widths.

```scss
@mixin clearfix {
    *zoom: 1;
    &:before,
    &:after {
        content: ' ';
        display: table;
    }
    &:after {
        clear: both;
    }
}

.grid {
    &,
    .grid__row {
        @include clearfix;
    }
    .grid__row {
        @include rem("margin", 0 -10px);
    }
    .grid__column {
        float: left;
        display: block;
        @include rem("padding", 0 10px);
        // Set a variable for the amount of columns you want to use.
        // In this case we are setting 12.
        $grid-column: 12;
        $column-inc: $grid-column;
        // Loop through and create grid columns based on the value of the $grid-column var.
        @while $column-inc > 0 {
            &.grid--column-#{$column-inc}{
                width: ( 100% / $grid-column ) * $column-inc;
            }
            $grid-column: ($column-inc - 1);
        }
        // Loop through and create percentage based columns.
        // The amount is defined by how many values are set in the $grid-array var.
        $count-inc: 1;
        $grid-array: 100%, 50%, 33.333333%, 25%, 20%, 16.666666%, 14.2857142857143%, 12.5%, 11.1111111111111%, 10%;
        @while $count-inc <= length($grid-array) {
            &.grid--count-#{$count-inc}{
                width: nth($grid-array, $count-inc);
            }
            $count-inc: ($grid-inc + 1);
        }
    }
}
```

## Groups
In short, a Group is a collection of modules. Modules within a module. When building a site in a modular fashion it's very easy to build a number of disparate modules, add these to your site/app and everything works. But sometimes you'll run into the need display modules differently depending on their context. This is where Groups come in.

Groups create a context for modules to sit within, forming a relationship between modules.


**Method 1**

```html
<button class="g-btn btn btn--alpha">Save Work <i class="g-btn__icon icon"></i></button>
```

```scss
.g-btn{
    .g-btn__icon{
        float: right;
    }
}

```

**Method 2**

```html
<button class="btn btn--alpha">Save Work <i class="g-btn__icon icon"></i></button>
```

```scss
.btn--alpha{
    .btn__icon{
        float: right;
    }
}

```

Before creating a group you may find it easier to create what you want by applying a modifier class directly to a module. This has the benefits of reuse anywhere else. If this doens't work, then proceed to creating a group.

An example of a group:


## Helpers
Coming soon...

## Project structure

* default.scss
    * config
        * _variables
            * themes
    * helpers
        * _helpers
        * _mixins
        * _reset
    * groups
        * Groups are unrelated modules brought together
    * partials
        * _layout
        * _fonts
        * _grid
        * _forms
        * _boxes
        * _lists
        * _icons
        * _navigation
        * _tables
        * _buttons

## Helper classes

`.align-right`
`.align-left`
`.align-center`
`.align-right`

## Sass
Coming soon...

## JavaScript
There are many many JS style guides out there so why reinvent the wheel? If you are looking to standardise the way your team writes JS take a look at the [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript).

### JavaScript / CSS hooks
Only to be used for JavaScript and not for styling.

## NoJS

.no-js .my-module{
    ...
}

** Or with Sass **

.my-module{
    .no-js &{
        ...
    }
}


## Default Views / Modular Media Queries
[Sass Media Queries](https://github.com/ourmaninamsterdam/sass-mediaqueries)

## Code Library
All common module patterns with full examples.

**Credits**
[Matt Burrows](https://github.com/mattjburrows) and [Justin Perry](https://github.com/ourmaninamsterdam)
