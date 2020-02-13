[⬅️ Back to main](README.md)

# 💗 Media queries
Especially in sass, there are different ways to implement mediaqueries. We'll be using `mixins` do define our mediau queries

## 📱 Mobile first. Always.
With an increasing number of mobile users every year, mobile and tablet are more important than ever. Always start off with mobile base values.

## 😎 Use per class
To make it easier to find classes and prevent re-writing classes, we'll use mediaqueries everytime they are needed. In the end all mediaqueries will be compiled together anyway.

```scss
// 🚫Don't
.component {
    color: const($color, primary);
}

@include breakpoint-min(md) {
    .component {
        color: const($color, secondary);
    }
}

// ✅Do's
.component {
    color: const($color, primary);

    @include breakpoint-min(md) {
        color: const($color, secondary);
    }   
}
```

## 🤪 Different kinds of media queries
There are three kinds of mediaqueries. The `@include breakpoint-min(){}` mixin will be your best friend most of the times.

But there are many use cases where you're in need of the other two. Especially when designing for very specific sizes.
```scss
@include media(min, tablet) { ... } // Make this standard
@include media(minmax, tablet, desktop) { ... }
@include media(max, desktop) { ... }
```

---

### 🚧 Todo's
- [ ] Write working function for the above to work 