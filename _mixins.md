[⬅️ Back to main](README.md)

# 💩 Mixins 
Mixins are lumps of code that can use arguments like a `@function`. This way we can pass through changes without re-writing every line of code.

- Only use mixin when you pass through arguments. If you don't, it's nothing more than a [lump of re-usable code](_extend.md).

## 🚽 Example
### 🚫Don't
The problem with mixins is that it renders all lines of code that are included. It's very easy to misuse, because of it's syntactic sugar. But it's output will make your code bloated.

```scss
//// Input
@mixin button($color) {
    // Static code
    padding: const($padding, button);
    display: flex;
    align-items: center;
    justify-content: center;
    color: const($color, white);

    // Only difference
    background-color: const($colors, $color);
}

.button--primary {
    @include button(primary);
}

.button--secondary {
    @include button(secondary);
}
```
```css
/* Output */
/* a lump of code */
.button--primary {
    padding: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #ffffff;
    background-color: orange;
}

/* THE (mostly) SAME LUMP OF CODE AGAIN?  */
.button--secondary {
    padding: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #ffffff;
    background-color: pink;
}
```

### ✅Do
When using mixins to pass through specific changes, you won't repeat unnecessary code and only add the differences. Which is pretty DRY.

```scss
//// Input
// Re-usable base lump of code
%button-base {
    padding: const($padding, button);
    display: flex;
    align-items: center;
    justify-content: center;
    color: const($color, white);
}

// Use lump of code and add custom differences through an argument
@mixin button($color) {
    @extend %button-base;
    background-color: const($colors, $color);
}

.button--primary {
    @include button(primary);
}

.button--secondary {
    @include button(secondary);
}
```
```css
/* Output */
.button--primary, .button--secondary {
    padding: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #ffffff;
}

.button--primary {
    background-color: orange;
}

.button--secondary {
    background-color: pink;
}
```