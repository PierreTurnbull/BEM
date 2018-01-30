# Protips

_No prefix is used in the code below_

## Table of contents

* __BEM__
* __Burger menu__
* __Pseudo attributes__

### Convention BEM

* B -> Block
* E -> Element
* M -> Modifier

HTML:

```HTML
<!-- mainlist = block -->
<ul class="mainList mainList--xmas">
  <!-- __item = element -->
  <li class="mainList__item">
    <!-- __itemLink = element -->
    <a class="mainList__itemLink mainList__itemLink--isActive" href="/home">Accueil</a>
  </li>
  <li class="mainList__item">
    <!-- __itemLink = element -->
    <a class="mainList__itemLink" href="/about">About</a>
  </li>
  <li class="mainList__item">
    <!-- __itemLink = element -->
    <a class="mainList__itemLink" href="/works">Works</a>
  </li>
</ul>
```

SCSS:

```CSS
.mainList {
  display: flex;
  justify-content: space-between;
  &--xmas {
    background: green;
  }
  &__item {
    list-style: none;
  }
  &__itemLink {
    color: red;
    &--isActive {
      color: white;
    }
  }
}
```

CSS result:

```CSS
.mainList {
  display: flex;
  justify-content: space-between;
}

.mainList--xmas {
  background: green;
}

.mainList__item {
  list-style: none;
}

.mainList__itemLink {
  color: red;
}

.mainList__itemLink--isActive {
  color: white;
}
```

### Pseudo attributes

Pseudo attributes `before` and `after` enable the creation of HTML nodes in CSS.
They are mostly used to flourish and decorate the DOM _(Document Object Model)_.
It is possible to create animations and to position them compared to their parents _(relative / absolute)_.
**They have to possess the property `content: ''` in order to display.**

Example:

HTML:

```HTML
<section class="cover">
  <h1 class="cover__mainTitle">Pseudo attribute presentation</h1>
</section>
```

SCSS:

```CSS
.cover {
  background-color: #F7F7F7;
  padding: 20px;
  &__mainTitle {
    text-align: center;
    font-size: 24px;
    color: green;
    position: relative;
    &::before,
    &::after {
      position: absolute;
      content: "HEY";
      display: block;
      width: 60;
      height: 30px;
      background-color: green;
      color: black;
      top: 0;
    }
    &::before {
      left: 0;
    }
    &::after {
      right: 0;
    }
  }
}
```

### Burger menu

A small 25 SCSS lines burger menu that can be adjusted really easily thank's to SCSS's variables and animated properly thank's to it's HTML structure.

HTML:

```HTML
<div class="burgerMenu">
  <span class="burgerMenu__rod"></span>
  <span class="burgerMenu__rod"></span>
  <span class="burgerMenu__rod"></span>
</div>
```

SCSS:

```CSS
/* BURGER MENU'S WIDTH AND HEIGHT */
$burgerMenuSize: 50px;

/* BURGER MENU ROD'S SIZE COMPARED TO BURGER MENU'S SIZE */
$burgerMenuRodRatio: 5;

/* BURGER MENU COLOR */
$burgerMenuRodColor: #600;

.burgerMenu {
  position: relative;
  height: $burgerMenuSize;
  width: $burgerMenuSize;
  &__rod {
    position: absolute;
    background-color: $burgerMenuRodColor;
    display: block;
    width: $burgerMenuSize;
    height: $burgerMenuSize / $burgerMenuRodRatio;
  }
  &__rod:nth-child(1) {
    top: 0;
  }
  &__rod:nth-child(2) {
    top: $burgerMenuSize / 2 - $burgerMenuSize / $burgerMenuRodRatio / 2;
  }
  &__rod:nth-child(3) {
    bottom: 0;
  }
}
```

### REM, EM, %, VW

#### REM

* REM is based on the root's font-size, `<html>`, which by default is 16 pixels. In order to make things easier _(less calculations)_, `<html>` font size value should be set to 10%, or 62.5%.
* REM is an interesting tool to get propotional values when resizing the page.
* REM proportions are kept the same when a user zooms in the page.

```CSS
html {
  font-size: 62.5%;
}
```

#### EM

* EM is a value relative to the font-size of the direct parent.

SCSS:

```CSS
.cover {
  font-size: 20px;
  &__mainTitle {
    /* 1em = 20px / 0.8em < 20px */
    font-size: 0.8em;
  }
}
```

#### %

* Percentage is a value relative to the corresponding value of the direct parent.

SCSS:

```CSS
.cover {
  width: 500px;
  &__mainTitle {
    /* 50% of 500px is 250px */
    width: 50%;
  }
}
```

#### VW / VH

* vw and vh are screen size based values. 1vh is 1% of the screen height.
* Be careful with vh and its content. 100vh = 100% of the screen height, whatever happens _(even when flipping a phone)_.
* vw is very usefull for fluid interfaces (which is different of responsive).
