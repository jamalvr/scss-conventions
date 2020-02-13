[⬅️ Back to main](README.md)

# 🤯 Functions
Functions are something that are not necessarily used very often in older projects. But there some new cases where you can get more out of functions without over complicating your code.

- Extracting values from maps
- Forcing syntax check on variables (goes hand in hand with exctracting values from maps)
- Calculating stuff

## 💣 Examples
### 🧮 Calculate stuff
Calculating single values. Adds some flexibility and syntactic sugar. When named correctly it's very clear what it does and why it does what it does.
```scss
@function calculate-width ($col-span) {
    @return 100% / $col-span 
}

.span-two {
    width: calculate-width(2); // spans 2 columns, width = 50%
}
```

### 🚀 Extracting values & syntax check
This looks like a complicated function, and maybe it is, but it does something very simple. It reads a `map` and checks values. Both single or double nested maps. 

By gently 'forcing' functions, people are bound to the structure of a map. Instead of making up their own variable names. This way, code will be more consistent.
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

//// Usage
property: const($map, modifier);
// or
property: const($map, modifier, state);
```