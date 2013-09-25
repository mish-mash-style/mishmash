#mishmash

A style guide for modular CSS.

Influences: (BEM)[http://bem.info/), (SMACSS)[http://smacss.com/] and (Modular CSS)[http://www.alanayoub.com/modular-css]

##Basic

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

    /*
     * Default Nav class
     *
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

    /*
     * Nav Primary
     *
     */
    .nav--primary{
        ...
    }
        .nav--primary .nav__items{
            ...
        }

```