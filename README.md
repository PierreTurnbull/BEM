# Documentation

## Convention BEM

* B -> Block
* E -> Element
* M -> Modifier

_Tout le code ci-présent est exempt de préfixe_

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

Exemple en CSS du rendu:

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

## Pseudo attributs

Les pseudo attributs `before` et `after` permettent de créer des noeuds HTML en CSS.
Ils sont essentiellement utilisés pour ajouter des ornements, des décorations...
On peut bien entendu faire des animations avec, les positionner par rapport à leur parent (relative / absolute).
**Ils doivent obligatoirement avoir la propriété `content: ''`** afin de s'afficher.

Exemple:

HTML:

```HTML
<section class="cover">
  <h1 class="cover__mainTitle">Présentation des pseudo-attributs</h1>
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

## Burger menu

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
$burgerMenuSize: 50px;
$burgerMenuRodRatio: 5;
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
