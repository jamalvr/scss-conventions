[⬅️ Back to main](README.md)

# 🏡 Local Variables
There will be instances we're you want to edit or use variables locally. You don't use the global scope to define those variables. Those are defined in [🌎global maps](_global-variables.md).

  - [👨‍👩‍👧‍👦 Usage](#%f0%9f%91%a8%e2%80%8d%f0%9f%91%a9%e2%80%8d%f0%9f%91%a7%e2%80%8d%f0%9f%91%a6-usage)
    - [👷‍♂️ Usage](#%f0%9f%91%b7%e2%80%8d%e2%99%82%ef%b8%8f-usage)
    - [👶 Naming conventions](#%f0%9f%91%b6-naming-conventions)
    - [💃 Importing & Exporting](#%f0%9f%92%83-importing--exporting)
      - [🕺🏿 Exceptions](#%f0%9f%95%ba%f0%9f%8f%bf-exceptions)

## 👨‍👩‍👧‍👦 Usage
The variables are scoped inside their respective file because we use [`@use` instead of `@import`](_using-other-files.scss). This gives us the flexibility to use easy and short names that can be used in different files at the same time — wow.

For that same reason we don't place local variables inside their component class.

### 👷‍♂️ Example
Use local variables for edits that are done only inside a component. Use global maps for styling that needs to be consistent across multiple components; like the brand color palette and typography.

```scss
//////// _button.scss

// 🚫Don't
.button {
    $padding: 16px !default;

    padding: $padding; // Much local, such wow
}

// ✅Do
$padding: 16px !default;

.button {
    padding: $padding; // Much local, such wow
}
```

### 👶 Naming conventions
To avoid naming confusion, we'll use existing css property names. As stated before: because variables are scoped insided their respective file, we are able to re-use the same variables across different files.

We use `!default` to prevent unnecessary use `!important` and forced nesting when a parent wants to override certain styling.
```scss
// 🚫Don't use made up variable names
$spacing: 16px !default;

// ✅Do use existing css property names
$padding: 16px !default;
```