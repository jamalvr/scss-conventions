[⬅️ Back to main](README.md)

# Nesting & Inheritance
Nesting & inheritance is very important. It's one of the hardest things to do properly in CSS.

## ✏️ Nesting
An element that is nested multiple levels deep in HTML doesn't need the same levels in CSS.
```html
<div class="nav-list">
    <ul>
        <li>Text</li>
    </ul>
</div>
```

### 🖖 Example
To prevent super specific CSS, we can use `inherit` to move specific CSS to the highest parent selector available. If you ever want to overwright styling (which you will), you'll be able to fairly easy, without adding extra classes or an `!important`.
```scss
// 🚫Don't
.nav-list {
    ul {
        li {
            .another-class { 
                color: const($color, primary);
             }
        }
    }
}

// ✅Do
.nav-list {
    color: const($color, primary);

    ul { ... }
    li { ... }
}
```

#### In case you're forced to 
In case someone made it very hard for you and overwrote inheritance, push the inheritance back to the highest parent possible. If everyone is coding nicely, this shouldn't occur very often. But if it does, you can "fix" it like this:
```scss
// This way we're very specific, without losing flexibility. 
// If you can define styling to the highest parent, always do.
// Inheritance = win, even if you have to force it haha.
.nav-list {
    color: const($color, primary);

    ul {
        color: inherit;
    }

    li { 
        color: inherit;
    }
}
```