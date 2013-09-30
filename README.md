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

```css

/**
 * Default Nav class
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
 * Nav Primary
 */
.nav--alpha{
    ...
}
    .nav--alpha .nav__items{
        ...
    }

```

## Naming conventions

### Sizes

.btn--xxs

.btn--xs

.btn--s

.btn--m

.btn--l

.btn--xl

.btn--xxl

Can include as many xxxs as you like `.btn-xxxxl`.

### Instances

Useful when you have many colours. Follows the NATO Phonetic alphabet.

$brand-alpha

$brand-beta

$brand-charlie

$brand-delta

$brand-echo

...


## Layout

## Groups
Module within a module. Coming soon...

## Helpers
Coming soon...

## Project structure
Coming soon...

## Sass
Coming soon...

## JavaScript
Coming soon...

## NoJS
Coming soon...

## Default Views / Modular Media Queries
[Sass Media Queries](https://github.com/ourmaninamsterdam/sass-mediaqueries)

## Code Library
All common module patterns with full examples.

**Credits**
[Matt Burrows](https://github.com/mattjburrows) and [Justin Perry](https://github.com/ourmaninamsterdam)