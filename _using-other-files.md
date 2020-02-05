[⬅️ Back to main](README.md)

# 🤝 `@use` other files
We stop using the `@import` function because if loads everything globally. With `@use` you automatically scope and namespace everything you're importing. The downside is that there are files where there is a lot of `@use` imports. Flipside is that it's scoped and it's VERY clear where imports actually come from.

- [🤝 `@use` other files](#%f0%9f%a4%9d-use-other-files)
  - [🖖 Variables](#%f0%9f%96%96-variables)
    - [💅 Local](#%f0%9f%92%85-local)
    - [🤯 Global](#%f0%9f%a4%af-global)
  - [🚧 Todo's](#%f0%9f%9a%a7-todos)

## 🖖 Variables
If there is a variable you need from another file that isn't global, we import them using `@use`. This automatically gives them a namespace and local scope.

When using another file, make sure you namespace them correctly by using the corresponding file name as namespace. This way it's immediately clear where the imported variable comes from.

### 💅 Local
```scss
@use 'components/_button.scss';

$padding: button.$padding;

.component {
    padding: $padding;
}
```

### 🤯 Global
There are no actual [🌎global variables](_global-variables.md) anymore. But let's consider them 'global variables'. These already have their own syntax and should be clear where they come from already. To avoid using unnecessary extra syntax, we declare a wildcard namespace.

```scss
@use 'globals/_colors.scss' as *;

.component {
    color: const($color, primary);
}
```

## 🚧 Todo's
- [ ] Global & local mixins