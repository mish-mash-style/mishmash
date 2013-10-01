#mishmash

A battle-hardened style guide for modular CSS.

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

## Groups
Module within a module. Coming soon...

## Helpers
Coming soon...

## Project structure

* config
* screen.scss
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
        * 

## Sass
Coming soon...

## JavaScript
Coming soon...

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
