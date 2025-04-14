## Week 7: Flexbox & Grid — Student Reference Notes

### SESSION 1: Introduction to Flexbox

**What is Flexbox?**
- Flexbox is a **1-dimensional layout model**. It helps align items **in a row or column**.
- Use Flexbox for smaller layout sections like navbars, toolbars, or cards in a row.

**Flex Container vs. Flex Items**
- A parent element becomes a **Flex Container** when you apply `display: flex;`.
```css
.container {
  display: flex;
}
```
- All direct children become **Flex Items**. Each item can be styled independently within the Flex context.

**Main Axis vs. Cross Axis**
- The **Main Axis** is defined by `flex-direction`:
  - `row` (default) → left to right
  - `column` → top to bottom
- The **Cross Axis** is perpendicular to the Main Axis.
- `justify-content` aligns items on the Main Axis.
- `align-items` aligns items on the Cross Axis.

**Key Flexbox Properties**
```css
.container {
  display: flex;
  flex-direction: row;         /* or column */
  justify-content: center;     /* or flex-start, flex-end, space-between, etc. */
  align-items: center;         /* or flex-start, flex-end, stretch */
  flex-wrap: wrap;             /* allow wrapping */
}
```

**Code-Along: Header & Nav Layout**
```html
<header style="display: flex; justify-content: space-between; align-items: center; padding: 1rem; background-color: #333;">
  <h1 style="color: white;">Site Title</h1>
  <nav>
    <a href="#" style="color: white; margin: 0 1rem;">Home</a>
    <a href="#" style="color: white; margin: 0 1rem;">About</a>
  </nav>
</header>
```

---

### SESSION 2: Flexbox Deep Dive

**Flex Basis, Grow, & Shrink**
- `flex-basis`: initial size of the item before space distribution.
- `flex-grow`: how much the item grows relative to siblings.
- `flex-shrink`: how much the item shrinks if needed.
```css
.item {
  flex: 1 0 200px; /* grow, shrink, basis */
}
```

**flex-wrap & flex-flow**
```css
.container {
  display: flex;
  flex-flow: row wrap; /* shorthand for flex-direction + flex-wrap */
}
```

**Use Cases:** navbars, footers, toolbars, icon bars, side-by-side sections.

**Short Project: Card Layout**
- Layout 3–6 cards with Flexbox.
- Cards should wrap when screen size is reduced.
```html
<div class="card-container">
  <div class="card">Card 1</div>
  <div class="card">Card 2</div>
</div>
```
```css
.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
.card {
  flex: 1 1 300px;
  border: 1px solid #ccc;
  padding: 1rem;
}
```

---

### SESSION 3: Intro to CSS Grid

**Flexbox vs. Grid**
- **Flexbox**: One direction (row OR column)
- **Grid**: Two directions (rows AND columns)

**Grid Terminology**
- **Tracks**: rows or columns.
- **Cells**: single box in the grid.
- **Grid Lines**: start and end lines.
- **Areas**: named sections that span multiple cells.

**Grid Container & Items**
```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-rows: 100px auto 50px;
  gap: 10px;
}
```
- All direct children of `.container` become grid items.

**Code-Along: Multi-Section Layout**
```html
<div class="container">
  <header>Header</header>
  <aside>Sidebar</aside>
  <main>Main Content</main>
  <footer>Footer</footer>
</div>
```
```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-rows: 80px 1fr 60px;
  gap: 10px;
}
header, footer {
  grid-column: 1 / -1; /* span full width */
}
```

---

### SESSION 4: Advanced CSS Grid

**minmax(), auto-fit, auto-fill**
```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 10px;
}
```
- **minmax(min, max)**: Sets a flexible column size.
- **auto-fit**: collapse empty columns.
- **auto-fill**: reserve space for empty columns.

**Named Grid Areas**
```css
.container {
  display: grid;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
  grid-template-columns: 200px 1fr;
}
header {
  grid-area: header;
}
```

**Short Project: Responsive Gallery**
```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
}
.item {
  background-color: #eee;
  height: 150px;
}
```
```html
<div class="gallery">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>
```

**Wrap-Up**
- Use Flexbox for one-dimensional layouts (e.g., navbars).
- Use Grid for two-dimensional layouts (e.g., full-page sections).
- Mix both as needed!
- Test responsiveness by resizing your screen or using DevTools.

