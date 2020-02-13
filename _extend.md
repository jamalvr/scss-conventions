[⬅️ Back to main](README.md)

# ☝️ Extend & placeholders
Use `%placeholders` for repetitive lumps of code that don't need a class of their own.

- Use `%placeholder` and `@extend` in the same file where their called. This makes it easier to find the base code.
- Using classes as `.placeholder` also works. If you need the base styling somewhere else, this is the perfect way.

## 🖐 Example
This example is based on the one found at [Sitepoint](https://www.sitepoint.com/8-tips-help-get-best-sass/). This example creates a base placeholder. This placeholder can be re-used by a `@mixin`. In the `@mixin` we'll add the differences when called on by specific classes.

This way we are writing very dry and readable code.

```scss
// Define base styles
%button-base {
    padding: const($padding, button);
    display: flex;
    align-items: center;
    justify-content: center;
    color: const($color, white);
}

// Mixin with usage of the base styles when called
@mixin button-background($color) {
    @extend %button-base;
    background-color: const($colors, $color);
    &:hover {
        background-color: const($colors, $color, active);
    }
}

// Call mixin in specific class
.button--primary {
    @include button-background(primary);
}
```

### Exceptions
Of course there are exceptions. There will be cases where there are some global base styles that need to be extended.
```scss
%flex-center-center {
    display: flex;
    justify-content: center;
    align-items: center;
}

.component {
    @extend %flex-center-center
}
```

---

### 🚧 Todo's
- [ ] Write `%placeholder` function for syntax check & syntactic sugar. Just like global variables.