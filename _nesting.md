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
To prevent super specific CSS, we can use `inherit` to move specific CSS to the highest parent selector available. If you ever want to overwright styling (which you will), you'll be able to it fairly easy, without adding extra classes or an `!important`.

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

    ul {
        color: inherit;
        display: flex;
    }
   
    li {
        color: inherit;
        margin: 0 0 $margin 0;
    }
}
```