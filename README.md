# 1. Box Model
![image](https://github.com/user-attachments/assets/f3b3dd08-5e7e-4ec6-8809-4f5a92f8aaae)

## 2. Width of block elements.
let's say we have a div with :-
- **Padding: 50px**
- **Border: 50px**
- **No `width` defined** → So the browser figures it out automatically based on the content.
✅ This worked perfectly fine.

> When you don’t set width, the block element doesn’t try to force itself for any specific width, instead it be like "I’ll take up all the available space inside the parent and will also leave space for padding and border (if exist's) such that all(content + padding + border) leave happily in the given space (without causing horizontal scrollbar or overflow) and if there's come the scenario where my parents width is decreased, I’ll shrink with it — including the content — to make sure I still fit within my parent."

> Here parent can be a **div** element with it's own width or directly root element like **body** "By default, the `<body>` element ends up being as wide as the viewport."


---

### 🔹 Then I Ask:

> “What happens if we **set a width** like `width: 100%`?”

You might think:

> “100% should just take up the full width of the screen, right?”

But...

### 🚨 Problem:

I **explicitly set `width: 100%`**, and now:

> ❗The box is overflowing — going off the edge of the screen!

---

## 🤔 Why Is This Happening?

Here’s the key:

### ⚠️ 1. `width: 100%` means:

> “The **content box** should be 100% as wide as the parent.”

Let’s say the screen (viewport) is 1000px wide.  
So `width: 100%` → **content box = 1000px**

---

### ⚠️ 2. Now Add:

- `padding: 50px` on **left & right** → adds **100px total**
- `border: 50px` on **left & right** → adds **100px total**

📦 So total width becomes:

```
1000px (content) + 50px + 50px (padding) + 50px + 50px (border) = 1200px
```

That’s **200px more** than the screen → it **overflows**! and **horizontal scroll appears**

---

## 🧠 Key Takeaways (Simplified):

### ✅ Block elements by default:

- Stretch to **fill available space** (this is `width: auto`, **not** `width: 100%`)

So when **no width is set**, the content **fits naturally**, and the browser adjusts.

---

### ❗ But when you say `width: 100%`:

- You’re **forcing the content box** to be full width
- Then **padding + border are added on top**
- So total width becomes **more than 100%** → it overflows

---

## ✅ Summary:

| Situation              | What Happens                                               |
|------------------------|------------------------------------------------------------|
| `width: auto` (default) | Content + padding + border fit naturally inside the space. |
| `width: 100%`           | Content takes full width → padding & border overflow!      |
| `box-sizing: border-box`| Fixes this by including padding & border **inside** the width. |

---

If you're thinking:  
"How to prevent this overflow while still using width 100%?"  
➡️ Use this magic line in CSS:

```css
box-sizing: border-box;
```

This tells the browser:

> “When I say width is 100%, include padding and border **inside** that 100%, not outside.”
