# 🍒 Cherry (S)CSS V2
Clean, readable and scalable CSS. By combining vanilla CSS inheritance with SCSS functionality to gently force better code. The nice bits are 'cherry picked' from different coding standards.

## 🔥 Basic SCSS rules
- [Don't nest more than two levels deep](_nesting.md). Three is still allowed, but not preferred. Four or more levels deep? Change your code.
- [Comment as much as possible](_comments.md). This helps your future self and others a lot.
- Don't use `!important`. In the very (x1000) rare case that you need it, at least comment/blame why you did it.
- `enter` everytime you target a new element. Doesn't matter if it's nested or not. This improves readability.
- **Don't style ID's** ➡️ Create a seperate class with the same name if you have to.

## 🧠 Contents
Here you'll find the most important guidelines.
1. [🌎 Global variables](_global-variables.md)
2. [🏡 Local variables](_local-variables.md)
3. [🤝 Using other files](_local-variables.md)
4. [🥳 Class names](_class-names.md)
5. [✏️ Nesting & inheritance](_nesting.md)
6. [🗣 Comments](_comments.md)

## 🤓 Learnings from V1
The problem with [V1](#) is that we relied too much on the right interpretation of the programmer using the conventions. We are all humans and with a 'loose' language like CSS, with an almost equally loose coding style, inconsistencies will happen. No matter how good the programmer is.

## 📕 Sources
