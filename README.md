# 🍒 Cherry (S)CSS V2
Clean, readable and scalable CSS. By combining vanilla CSS inheritance with SCSS functionality to gently force better code. The nice bits are 'cherry picked' from different coding standards.

## 🔥 Basic SCSS rules
1. [Don't nest more than two levels deep](_nesting.md). Three is still allowed, but not preferred. Four or more levels deep? Change your code.
2. [Comment as much as possible](_comments.md). This helps your future self and others a lot.
3. Don't use `!important`. In the very (x1000) rare case that you need it, at least comment/blame why you did it.
4. `enter` everytime you target a new element. Doesn't matter if it's nested or not. This improves readability.
5. Don't style ID's ➡️ Create a seperate class with the same name if you have to.
6. Only use mixins if you pass through arguments that change ALL code in the mixin.
7. `@use` files and don't `@import` files.
8. `@extend` repetitive lumps of static code. Keep it dry.

## 🧠 Contents
Here you'll find the most important guidelines.
1. [🌎 Global variables](_global-variables.md)
2. [🏡 Local variables](_local-variables.md)
3. [🤝 Using other files](_local-variables.md)
4. [🥳 Class names](_class-names.md)
5. [✏️ Nesting & inheritance](_nesting.md)
6. [🗣 Comments](_comments.md)
7. [💗 Media queries](_media-queries.md)
8. [☝️ `@extend` & `%placeholder`](_extend.md)
9. [💩 Mixins `@include`](_mixins.md)
10. [💪 Functions](_functions.md)

## 🤓 Learnings from V1
The problem with [V1](_v1.md) is that we relied too much on the right interpretation of the programmer using the conventions. We are all humans and with a 'loose' language like CSS, with an almost equally loose coding style, inconsistencies will happen. No matter how good the programmer is.

## 📕 Sources
- [SASS-lang: variables](https://sass-lang.com/documentation/variables)
- [CSS-tricks: introducing SASS modules](https://css-tricks.com/introducing-sass-modules/)
- [getbemm: introduction](http://getbem.com/introduction/)
- [Smahing Magazine: Object Oriented CSS](https://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/)
- Nope: [Smashing Magazine: Atomic Approach](https://www.smashingmagazine.com/2013/10/challenging-css-best-practices-atomic-approach/)
- [CSS-tricks: Approach to Media Queries in SASS](https://css-tricks.com/approaches-media-queries-sass/)
- Very nice: [Sitepoint: 8 tips help get best sass](https://www.sitepoint.com/8-tips-help-get-best-sass/)