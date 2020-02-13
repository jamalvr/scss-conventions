[⬅️ Back to main](README.md)

# 🌎 Global Variables
Instead of defining global variables in a list of — well... variables. We define them in a map. This map uses a global function for some **syntactic sugar** and **rules to prevent overruling** global variables.

#### 🛩 Changing global variables
- Add custom [variables to component scope](_local-variables.md)
- Add [💪 extra values to a map](#%f0%9f%92%aa-adding-values-to-a-map) to map

## 🧠 Table of contents
  - [🤔 Defining a map for global variables](#%f0%9f%a4%94-defining-a-map-for-global-variables)
    - [💪 Adding values to a map](#%f0%9f%92%aa-adding-values-to-a-map)
      - [🤯 Exception: Using single value maps](#%f0%9f%a4%af-exception-using-single-value-maps)
  - [🗺 Using a map](#using-a-map)
    - [🧭 Syntax](#syntax)
  - [🚧 Todo's](#%f0%9f%9a%a7-todos)

## 🤔 Defining a map for global variables
If there are multiple values inside an object, always use a base value.

```scss
$color: (
    primary: (
        base: pink,
        active: red
    ),
)
```

### 💪 Adding values to a map
Make sure you always follow the structure of the map with the same modifier names. Be careful when adding new modifiers to a map object. **Is it a modifier that can be used (theoretically) by other objects?**. The example above has a `base` & `active` modifer. Keep that structure when adding new modifiers.

#### 🤯 Exception: Using single value maps
Let's pick the example above. Sometimes your map objects only have a `base` value. In that case you are allowed add the value immediately after declaring your map object.

```scss
$color: (
    primary: (
        base: pink,
        active: red
    ),
    secondary: orange,
)
```

## 🗺 Using a map
For using the map we need the `const` function. This way we declare the variable like a javascript constant.  

### 🧭 Map function
Define this function in your global functions or `@use` it in every file where you need to target maps.
```scss
// Using nested maps. It takes 'base' as default state
@function const($map, $modifier, $state: base) {
  @return map-get-nested($map, $modifier, $state);
}

// Reading both nested and single level maps
@function const($map, $modifier, $state: base) {
  // Check if the first level is a map
  @if type-of(map-get($map, $modifier)) == "map" {
    @return map-get-nested($map, $modifier, $state);
  } 
  // If not, use regular map get on first level
  @return map-get($map, $modifier);
}
```

### 🤖 Syntax
```scss
// map & modifier
color: const(color, primary);

// Add a state if there is one
&:hover {
    color: const(color, primary, active);
}
```

## 🚧 Todo's
- [ ] Map function update to support single value maps