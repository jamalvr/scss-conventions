# 🍒 Cherry (S)CSS V2
Clean, readable and scalable CSS. By combining vanilla CSS inheritance with SCSS functionality to gently force better code.

## 🤓 Learnings from V1
The problem with [V1](#) is that we relied too much on the right interpretation of the programmer using the conventions. We are all humans and with a 'loose' language like CSS, with an almost equally loose coding style, inconsistencies will happen. No matter how good the programmer is.

## Global variables
Instead of defining global variables in a list of well... variables, we define them in a map. This map uses a global function for some **syntactic sugar**.

### Defining a map
If there are multiple values inside an object, always use a base value.

```scss
$color: (
    primary: (
        base: pink,
        active: red
    ),
)
```

### Using a map
For using the map we need the `const` function. This way we declare the variable like a javascript constant.  

<details>
<summary>The Map Function</summary>

```scss
//// Reading nested maps
@function map-get-nested($map, $arguments...) {
  @each $arg in $arguments {
    @if not map-has-key($map, $arg) {
      @error 'Unknown constant modifier or state: `#{$arg}`.';
    } @else {
      $map: map-get($map, $arg);
    }
  }

  @return $map;
}

//// Using nested maps. It takes 'base' as default state
@function var($map, $modifier, $state: base) {
  @return map-get-nested($map, $modifier, $state);
}
```

</p>
</details>

#### Syntax
```scss
//// map, modifier & state if there is one
color: var(color, primary);

&:hover {
    color: var(color, primary, active);
}
```