#mishmash

A battle-hardened style guide for modular CSS.

* [HTML](#html)
* [CSS](#css)
    * [Signifying state](#signifying-state)
        * [Possessive and completed states](#possessive-and-completed-states)
* [Naming conventions](#naming-conventions)
    * [Sizes](#sizes)
    * [Instance modifiers](#instance-modifiers)
* [Layout](#layout)
* [Groups](#groups)
* [Helpers](#helpers)
* [Sass structure](#sass-structure)
* [Helper classes](#helper-classes)
* [JavaScript](#javascript)
    * [JavaScript hooks](#javascript-hooks)
    * [Feature detection](#feature-detection)
    * [NoJS](#no-js)
* [Default Views / Modular Media Queries](#default-views--modular-media-queries)
* [Code Library](#code-library)

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
    .nav--beta .nav__items{
        ...
    }
```

### Signifying State

Make use of State Indicators to signify a module's state

* `.is-active`
* `.is-selected`
* `.is-hidden`
* `.is-visible`
* `.is-valid`
* `.is-invalid`
* `.is-loading`
* `.is-scrollable`
* `.is-editable`

#### Possessive and completed states

* `.has-animated`
* `.has-loaded`
* `.has-error`
* `.has-dropdown`

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

Use the [NATO Phonetic alphabet](http://en.wikipedia.org/wiki/NATO_phonetic_alphabet) when specifying multiple variations.

In this example we are setting Sass variables:

* `$brand-alpha`
* `$brand-beta`
* `$brand-charlie`
* `$brand-delta`
* `$brand-echo`

Or for modified elements:

```html
.box{
    ...
}
.box--alpha{
    background: blue;
}
.box--beta{
    background: red;
}
```

## Layout

For layout - and if IE7 is no longer a concern - use the `border-box: box-sizing` property on a global reset so you don't have to worry about padding / border style declarations when using % based widths.

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
            &.grid__column-#{$column-inc}{
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
In short, a Group is a collection of modules. Or modules within a module. When building a site in a modular fashion, it's very easy to build a number of disparate modules, add these to your site/app and everything works. But sometimes you'll run into the need to display modules differently depending on their context. This is where Groups come in.

Groups create a context for modules to sit within, forming a relationship between them. Each sub-module is then made part of the containing module (a block in BEM) by including a class.

**Method 1**

```html
<button class="btn btn--alpha">Save Work <i class="g-btn__icon icon"></i></button>
```

```scss
.btn--alpha{
    .g-btn__icon{
        float: right;
    }
}
```

**Method 2**

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

Before creating a group you may find it easier to create what you want by applying a modifier class directly to a module. This has the benefits of reuse anywhere else. If this doesn't work, then proceed to creating a group.

## Sass structure

* default.scss
	* themes
		* _theme-alpha
    * config
        * _variables
    * helpers
        * _helpers
        * _mixins
        * _reset
    * ui
        * groups
            * A group is a collection of modules
        * _fonts
        * _layout
        * _grid
        * _forms
        * _lists
        * _navigation
        * _tables
        * _boxes
        * _buttons
        * _icons

## Helper classes

* `.align-right`
* `.align-left`
* `.align-center`
* `.align-right`

## JavaScript

There are many many JS style guides out there so why reinvent the wheel? If you are looking to standardise the way your team writes JS take a look at the [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript).

### JavaScript hooks

For using JavaScript in your code, we suggest the use of prefixed CSS class hooks `.js-`. These provide an easy method to bind JavaScript functionality without relying on IDs or non-concrete class names.

Note: These should be used purely as JS hooks and not styled in anyway, other than in a [NoJS](#example) instance.

**Example**
```html
<div class="box">
	<button class="box__action js-toggle" data-id="bacon">Toggle content</button>
	<div class="box__content" id="bacon">
    	Bacon ipsum dolor sit amet corned beef tri-tip venison sirloin chuck shank brisket meatball bresaola swine jowl doner cow. Spare ribs drumstick pork loin tenderloin.
	</div>
</div>
```

```js
$(document).on('click', '.js-toggle', function() {
    ...
});
```

### Feature detection

[Modernizr](http://modernizr.com/) is fast becoming one of the most useful tools in the modern Front-end developers arsenal. Much like the [No-JS](#nojs) detection method listed above we can easily customise builds based on the environment they are served in.

**Vanilla CSS**
```css
.no-touch .module {
    ...
}
```

**Or with Sass**
```scss
.module{
    .no-touch &{
        ...
    }
}
```

#### No JS

**Vanilla CSS**
```css
.no-js .module {
    ...
}
```

**Or with Sass**
```scss
.module {
    .no-js & {
        ...
    }
}
```

#### Old IE

**Vanilla CSS**

```css
.lt-ie8 .module {
    ...
}
```

**Or with Sass**
```scss
.module{
    .lt-ie8 &{
        ...
    }
}
```

## Default Views / Modular Media Queries
[Sass Media Queries](https://github.com/ourmaninamsterdam/sass-mediaqueries)

## Code Library
All common module patterns.

### Breadcrumb

```html
<ol class="breadcrumb">
    <li class="breadcrumb__item first"><a href="" class="breadcrumb__item__link">Item 1</a></li>
    <li class="breadcrumb__item"><a href="" class="breadcrumb__item__link">Item 2</a></li>
    <li class="breadcrumb__item"><a href="" class="breadcrumb__item__link">Item 3</a></li>
    <li class="breadcrumb__item last is-active"><a href="" class="breadcrumb__item__link">Item 4</a></li>
</ol>
```
emmet: `ol.breadcrumb>li.breadcrumb__item*4>a.breadcrumb__item__link{Item $}`

### Login screen (Group)

```html
<form class="form form-standard form--vertical" action="#">
    <fieldset class="form__section">
        <p class="form__message">
            Enter your email address below and we’ll send you a link to reset your password.
        </p>
        <ol class="form__items">
            <li class="form__item"><label>Username</label><input class="form__input" type="text">
                <div class="form__item__message">
                    <p>Please enter your username</p>
                </div>
            </li>
            <li class="form__item"><label>Password</label><input class="form__input" type="password"></li>
        </ol>
    </fieldset>
    <fieldset class="form__section form__section--actions">
        <ol class="form__items" start="3">
            <li class="form__item"><button type="submit">Sign in</button></li>
            <li class="form__item"><a href="#">Reset your password</a></li>
        </ol>
    </fieldset>
</form>
```


**Credits**
[Matt Burrows](https://github.com/mattjburrows) and [Justin Perry](https://github.com/ourmaninamsterdam)
