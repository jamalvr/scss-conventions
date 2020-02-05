[⬅️ Back to main](README.md)

# 🏡 Local Variables
There will be instances we're you want to edit or use variables locally. You don't use the global scope to define those variables. Those are defined in [🌎global maps](_global-variables.md).

## 👨‍👩‍👧‍👦 Usage
The variables are scoped inside their respective file because we use [`@use` instead of `@import`](_using-other-files.scss). This gives us the flexibility to use easy and short names that can be used in different files at the same time — wow.

### 👷‍♂️ Usage
Use local variables for edits that are done only inside a component. Use global maps for styling that needs to be consistent across multiple components; like the brand color palette and typography.

```scss
//////// _button.scss
$padding: 16px !default;

.button {
    padding: $padding; // Much local, such wow
    background-color: const($color, primary);
    color: const($color, white);

    &:hover {
        background-color: const($color, primary, active);
    }
}
```

### 👶 Naming conventions
To avoid naming confusion, we'll use existing css property names. As stated before: because variables are scoped insided their respective file, we are able to re-use the same variables across different files.
```scss
// 🚫Don't use made up variable names
$spacing: 16px !default;

// ✅Do use existing css property names
$padding: 16px !default;
```

### 💃 Importing & Exporting
If there is a variable you need from another file that isn't global, we import them using `@use`. This automatically gives them a namespace and local scope.

When using another file, make sure you namespace them correctly by using the corresponding file name as namespace. This way it's immediately clear where the imported variable comes from.

```scss
@use 'components/_button.scss';

$padding: button.$padding;

.component {
    padding: $padding;
}
```

#### 🕺🏿 Exceptions
There is no need to namespace global maps with variables. These already have their own syntax and should be clear where they come from already.
```scss
@use 'globals/_colors.scss' as *;

.component {
    color: const($color, primary);
}
```