# Documentation

## Convention BEM

* B -> Block
* E -> Element
* M -> Modifier

_Code without prefixes_

```hmtl
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

```css
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

```css
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
**Ils doivent obligatoirement avoir un `content: ''`** afin de s'afficher.

Exemple:

```html
<section class="cover">
  <h1 class="cover__mainTitle">Présentation des pseudo-attributs</h1>
</section>
```

```css
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
