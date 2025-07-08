# 4. 🌱 CSS Inheritance – A Simple but Powerful Concept

## 🎯 What is Inheritance in CSS?

**Inheritance** means child elements automatically receive certain style properties from their parent elements — without needing to rewrite them.

Think of it like this:
> "If the parent has a rule, the children may follow it — unless told not to."

---

## 👀 Real-World Analogy

> "My wife has blue eyes. Our kids inherited that."

In CSS:
```css
body {
  color: blue;
}
p {
  /* color: blue is inherited here automatically */
}
```

---

## ✅ Which Properties Get Inherited by Default?

Most **typography-related** properties are inherited.

| Property          | Inherited? |
|-------------------|------------|
| `color`           | ✅ Yes     |
| `font-family`     | ✅ Yes     |
| `font-size`       | ✅ Yes     |
| `line-height`     | ✅ Yes     |
| `letter-spacing`  | ✅ Yes     |
| `text-align`      | ✅ Yes     |
| `text-transform`  | ✅ Yes     |

### 🛠 Common Practice:
```css
html {
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  line-height: 1.6;
}
```
All elements inside the `html` will inherit these values unless overridden.

---

## ❌ Which Properties Do NOT Get Inherited?

Most **layout and visual** properties do NOT inherit by default.

| Property         | Inherited? | Why Not? |
|------------------|------------|----------|
| `margin`         | ❌ No      | Layout-specific |
| `padding`        | ❌ No      | Layout-specific |
| `width` / `height` | ❌ No   | Must be set per element |
| `border`         | ❌ No      | Visual boundary |
| `position`       | ❌ No      | Layout behavior |
| `display`        | ❌ No      | Structural role |

> It would be chaos if margins or padding just flowed down — imagine every child having the same left padding!

---

## 🧪 Special Case: **Form Elements Don't Inherit Typography**

Form controls like `<input>`, `<button>`, `<select>`, `<textarea>` — **do not** inherit text styles by default.

Why?  
➡️ Browsers apply their own default styling to them (like fonts, borders, padding, etc).

### 🧯 Fixing It:
Force inheritance manually:
```css
button,
input,
select,
textarea {
  font-family: inherit;
  font-size: inherit;
  color: inherit;
  line-height: inherit;
}
```

This makes form fields **match your site’s fonts and colors**, making everything feel consistent.

---

## 🧠 Using the `inherit` Keyword

You can *force* inheritance on any property like this:
```css
h2 {
  font-weight: inherit;
}
```

This tells the `h2` to use the font weight of its parent.

✅ Useful when:
- You want consistent font weight between body text and headings.
- You’re using a design system where styles change dynamically.

---

## 📦 Another Example

```css
body {
  color: #333;
  font-family: "Roboto", sans-serif;
}

.article p {
  /* inherits both color and font-family automatically */
}
```

But:
```css
.article {
  padding: 20px;
}
.article p {
  /* does NOT inherit padding — it’s a layout property */
}
```

---

## ✅ Summary Table

| Type             | Property Examples                          | Inherited? |
|------------------|---------------------------------------------|------------|
| Typography        | `color`, `font-family`, `line-height`      | ✅ Yes     |
| Layout            | `margin`, `padding`, `width`, `display`    | ❌ No      |
| Form Elements     | `<button>`, `<input>`, etc.                | ❌ No      |
| Forced Inheritance| `inherit` keyword                          | ✅ Manual  |

---

## 🧰 Pro Tip: Use Inheritance to Keep CSS DRY

**DRY = Don’t Repeat Yourself**

Instead of this:
```css
h1, h2, h3, p {
  font-family: "Open Sans", sans-serif;
}
```

Just do:
```css
body {
  font-family: "Open Sans", sans-serif;
}
```
The rest will inherit it ✨

---
