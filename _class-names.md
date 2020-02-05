[⬅️ Back to main](README.md)

# 🥳 Class names
We 'cherry picked' some rules from  BEMM and OOCSS to come up with something new. Picking best practices from both conventions.

We define a parent `component` name. This should be relatively short. If the component name is made of two words, we use a single line (`-`) to connect the name, like so: `component-name`.

- [🥳 Class names](#%f0%9f%a5%b3-class-names)
  - [👯‍♂️ Modifiers](#%f0%9f%91%af%e2%80%8d%e2%99%82%ef%b8%8f-modifiers)
  - [🎉 States](#%f0%9f%8e%89-states)
    - [🎁 Examples](#%f0%9f%8e%81-examples)
    - [🎊 Usage](#%f0%9f%8e%8a-usage)
  - [💕 Helper classes](#%f0%9f%92%95-helper-classes)
    - [💞 HTML elements](#%f0%9f%92%9e-html-elements)
    - [😍 Examples](#%f0%9f%98%8d-examples)
    - [😘 Usage](#%f0%9f%98%98-usage)
    - [💗 Helper modifiers](#%f0%9f%92%97-helper-modifiers)
      - [Example](#example)

## 👯‍♂️ Modifiers
In case a component has multiple versions of itself, target them with a modifier. We define a modifier by using double lines (`--`) between the component name and modifier, like so: `component-name--modifier`.

```html
<!---- 🚫Don't ---->
<a href="#" class="button button--primary"></a>

<!---- ✅Do ---->
<a href="#" class="button--primary"></a>
```
By using `@extend` we can use the base of the button without the need of adding an extra `.button` class.
```scss
.button {
    // Base styling
    padding: $padding; // vs $spacing--button__m
    display: flex;

    // Modifier styling
    &--primary {
        @extend .button; // This way we don't need to 'button button--primary' vs 'button--primary'
        background-color: const($color, primary);
        color: const($color, white);
    }
}
```

## 🎉 States
States are added as a sepperate class next to the component class name.

### 🎁 Examples
```scss
.active { ... }
.disabled { ... }
.error { ... }
```
### 🎊 Usage
```html
<div class="component active"></div>
```
```scss
.component {
    color: const($color, primary);
    &.active {
        color: const($color, primary, active);
    }
}
```

## 💕 Helper classes
Helper classes are for elements that barely have any semantic value of themselves, or are used in different ways. To improve readability and simplify applying styles to an element.

### 💞 HTML elements
```html
<span> 
<div>
<i>
<svg>
<img>
```

### 😍 Examples
There are only rare cases where you need to apply basic styling to helper classes. In some cases, like an `.icon`, it can be quite useful because it needs the same base styling everywhere.

Most helper classes are used inside a component and don't need base styling of themselves. 

```scss
.icon {
    display: inline-flex;
    align-items: center;
    justify-content: center;
}

.block {
    display: flex;
}

.title { ... }
.content { ... }
.text { ... }
.logo { ... }
.price { ... }
```

### 😘 Usage
```html
<!---- 🚫Don't ---->
<a href="#" class="button button--primary">
    <span class="button--primary--text">Klik hier</span>
    <i class="button--primary--icon"></i>
</a>

<!---- ✅Do ---->
<a href="#" class="button--primary">
    <span class="text">Klik hier</span>
    <svg class="icon"></svg>
</a>
```

### 💗 Helper modifiers
Even helper classes sometimes need a little bit of help. You can see them as mini-components. So it's only natural that they should have the ability be modified.

#### Example
```scss
.price {
    &--month { ... }
    &--year { ... }
    &--text { ... }
}
```