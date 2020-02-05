[⬅️ Back to main](README.md)

# 🥳 Class names
We 'cherry picked' some rules from  BEMM and OOCSS to come up with something new. Picking best practices from both conventions.

We define a parent `component` name. This should be relatively short. If the component name is made of two words, we use a single line (`-`) to connect the name, like so: `component-name`.

## Modifiers
In case a component has multiple versions of itself, target them with a modifier. We define a modifier by using double lines (`--`) between the component name and modifier, like so: `component-name--modifier`.

```html
<!---- 🚫Don't ---->
<a href="#" class="button button--primary"></a>

<!---- ✅Do ---->
<a href="#" class="button--primary"></a>
```
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

## States
States are added as a sepperate class next to the component class name.
### Examples
```scss
.active { ... }
.disabled { ... }
.error { ... }
```
### Usage
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

## Helper classes
Helper classes are for elements that barely have any semantic value of themselves, or are used in different ways. To improve readability and simplify applying styles to an element.

Voornamelijk voor elementen die geen of weinig semantische waarde vanuit hunzelf hebben. Dit komt voornamelijk omdat ze op meerdere manieren gebruikt kunnen worden en op andere manieren stijling nodig hebben. Door de helper classes zie je altijd waarvoor het element gebruikt wordt en wat het is. Zowel in de HTML als in de CSS/SCSS.

### HTML elements
```html
<span> 
<div>
<i>
<svg>
<img>
```

### Examples
There are only rare cases where you need to apply basic styling to helper classes. In some cases, like an `.icon`, it can be quite useful because it needs the same base styling everywhere.

Most helper classes are used inside a component.

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

### Usage
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