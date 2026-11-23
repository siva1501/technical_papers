# CSS Learning Roadmap: Short Version

A condensed step by step guide to learning CSS after HTML. Every topic has a simple explanation and a clear example you can copy and try.

# Phase 1: CSS Fundamentals

## 1. What is CSS?

CSS stands for Cascading Style Sheets. HTML builds the structure of a page (headings, paragraphs, images). CSS controls the look (colors, spacing, fonts, layout).

Think of a house: HTML is the walls and rooms, CSS is the paint, furniture and decoration.

```html
<h1>Hello World</h1>
```

```css
h1 { color: blue; font-size: 40px; }
```

## 2. Types of CSS

There are three ways to add CSS to an HTML page.

### a) Inline CSS

Written inside an HTML tag using the style attribute. It affects only that one element. Quick for tests, messy for big projects.

```html
<p style="color: red; font-size: 20px;">This is red text.</p>
```

### b) Internal CSS

Written inside a style tag in the head of the HTML file. It affects only that page.

```html
<head>
  <style>
    p {
      color: green;
      font-size: 18px;
    }
  </style>
</head>
```

### c) External CSS (Best Practice)

Written in a separate .css file and linked to the HTML file. One file can style many pages. Always use this in real projects.

```html
<head>
  <link rel="stylesheet" href="style.css">
</head>
```

```css
/* style.css */
p { color: purple; font-size: 18px; }
```

Priority when they conflict: Inline wins over Internal and External. Between Internal and External, the one written later wins.

## 3. CSS Syntax

A CSS rule has a selector and a declaration block. Each declaration is a property and value pair.

```css
selector { property: value; }
h1 {
  color: red;        /* property: color, value: red */
  text-align: center;
}
```

- h1 is the selector (what to style)
- color is the property (what to change)
- red is the value (how to change it)
- Text between /* and */ is a comment

## 4. CSS Selectors

Selectors choose which HTML elements to style.

### Element selector

Selects all elements of a given tag.

```css
p { color: gray; }
```

### Class selector (.)

Selects elements with a class. Can be reused on many elements.

```html
<p class="highlight">Important</p>
```

```css
.highlight { background-color: yellow; }
```

### ID selector (#)

Selects one unique element. An id should be used only once per page.

```html
<h1 id="main-title">Welcome</h1>
```

```css
#main-title { color: darkblue; }
```

### Universal, group, descendant and child selectors

```css
* { margin: 0; padding: 0; }            /* universal: everything */
h1, h2, h3 { font-family: Arial; }      /* group: same style for several */
div p { color: blue; }                  /* descendant: every p inside a div */
ul > li { list-style: square; }         /* child: direct children only */
```

### Attribute and sibling selectors

```css
input[type="text"] { border: 2px solid green; }
h2 + p { margin-top: 0; }       /* the paragraph right after h2 */
h2 ~ p { font-size: 18px; }     /* all paragraphs after h2 */
.note.special { font-weight: bold; }   /* element with both classes */
```

## 5. Colors

CSS gives many ways to write colors.

```css
h1 { color: red; }                    /* color name */
h1 { color: #ff0000; }                /* HEX */
h1 { color: rgb(255, 0, 0); }         /* RGB */
h1 { color: rgba(255, 0, 0, 0.5); }   /* RGBA: with transparency, 0 to 1 */
h1 { color: hsl(0, 100%, 50%); }      /* HSL: hue, saturation, lightness */
```

Two main properties:

- color changes the text color
- background-color changes the background color

```css
p { color: white; background-color: #333; }
```

## 6. Backgrounds

```css
.hero {
  background-color: #f0f0f0;                 /* solid color */
  background-image: url("banner.jpg");       /* image */
  background-repeat: no-repeat;              /* repeat, repeat-x, repeat-y */
  background-size: cover;                    /* cover, contain, 100px */
  background-position: center;               /* where the image sits */
  background-attachment: fixed;              /* parallax effect */
}
```

Gradients and shorthand:

```css
.gradient { background: linear-gradient(to right, #ff7e5f, #feb47b); }
.radial { background: radial-gradient(circle, #fff, #4facfe); }
.hero { background: #222 url("banner.jpg") no-repeat center / cover; }
```

## 7. Text Properties

```css
p {
  color: #333;
  text-align: center;          /* left, right, center, justify */
  text-decoration: underline;  /* none, underline, line-through */
  text-transform: uppercase;   /* lowercase, capitalize */
  letter-spacing: 2px;         /* space between letters */
  word-spacing: 5px;           /* space between words */
  line-height: 1.6;            /* space between lines */
  text-indent: 30px;           /* indent first line */
  text-shadow: 2px 2px 4px gray;
}
a { text-decoration: none; }   /* remove the underline from links */
```

## 8. Fonts

```css
body {
  font-family: "Poppins", Arial, sans-serif;  /* first choice, then fallbacks */
  font-size: 16px;
  font-weight: bold;         /* normal, bold, or 100 to 900 */
  font-style: italic;        /* normal, italic */
}
```

Using Google Fonts:

```html
<link href="https://fonts.googleapis.com/css2?family=Poppins&display=swap" rel="stylesheet">
```

```css
body { font-family: "Poppins", sans-serif; }
```

Shorthand: font: style weight size/line-height family;

```css
p { font: italic bold 16px/1.5 Arial, sans-serif; }
```

## 9. Units (px, %, em, rem, vh, vw)

| Unit | Meaning | Type |
|------|---------|------|
| px | Pixels, a fixed size | Absolute |
| % | Percentage of the parent element | Relative |
| em | Relative to the parent font size | Relative |
| rem | Relative to the root (html) font size | Relative |
| vh | 1 percent of the viewport height | Relative |
| vw | 1 percent of the viewport width | Relative |

```css
html { font-size: 16px; }
.box1 { width: 300px; }        /* always 300 pixels */
.box2 { width: 50%; }          /* half of the parent width */
.box3 { font-size: 2em; }      /* 2 x parent font size */
.box4 { font-size: 2rem; }     /* 2 x 16px = 32px */
.box5 { height: 100vh; }       /* full screen height */
.box6 { width: 100vw; }        /* full screen width */
```

Tip: Use rem for font sizes and spacing. Use %, vw and vh for flexible layouts.

# Phase 2: CSS Box Model

Every HTML element is a rectangular box. From inside to outside:

```
+------------------------------+
|            MARGIN            |
|   +----------------------+   |
|   |        BORDER        |   |
|   |   +--------------+   |   |
|   |   |   PADDING    |   |   |
|   |   |  +--------+  |   |   |
|   |   |  |CONTENT |  |   |   |
|   |   |  +--------+  |   |   |
|   |   +--------------+   |   |
|   +----------------------+   |
+------------------------------+
```

## 1. Content, Width and Height

The actual text, image or element inside the box. Its size is set with width and height.

```css
.box {
  width: 300px;
  height: 200px;
  max-width: 100%;     /* never wider than this */
  min-height: 100px;   /* never shorter than this */
}
```

## 2. Padding

Space inside the border, between the content and the border.

```css
.box {
  padding: 20px;                  /* all 4 sides */
  padding: 10px 20px;             /* top-bottom, left-right */
  padding: 10px 20px 30px 40px;   /* top, right, bottom, left (clockwise) */
  padding-left: 15px;             /* one side only */
}
```

## 3. Border

A line around the padding and content.

```css
.box {
  border: 2px solid black;        /* width style color */
  border-style: dashed;           /* solid, dashed, dotted, double */
  border-bottom: 3px solid red;   /* one side only */
}
```

## 4. Margin

Space outside the border, between this box and other boxes.

```css
.box {
  margin: 20px;
  margin: 10px 20px;
  margin-top: 30px;
  margin: 0 auto;     /* centers a block element horizontally (needs a width) */
}
```

Margin collapse: vertical margins of two blocks merge into the larger one. If one has margin-bottom 30px and the next has margin-top 20px, the gap is 30px, not 50px.

## 5. Box-sizing

By default (content-box), padding and border are added to the width, so a 300px box with 20px padding becomes 340px wide. This is confusing.

border-box includes padding and border inside the width, so the box stays 300px.

```css
/* Recommended: put this at the top of every project */
* { box-sizing: border-box; }
.box {
  width: 300px;
  padding: 20px;
  border: 5px solid black;
  /* total width is still 300px */
}
```

## 6. Border-radius

Rounds corners.

```css
.card   { border-radius: 10px; }        /* soft corners */
.circle { border-radius: 50%; width: 100px; height: 100px; }  /* circle */
.pill   { border-radius: 50px; }        /* pill shaped button */
.custom { border-radius: 10px 20px 30px 40px; }  /* each corner */
```

## 7. Box-shadow

Adds a shadow around a box.

Syntax: box-shadow: x-offset y-offset blur spread color;

```css
.soft   { box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2); }
.inset  { box-shadow: inset 0 0 10px gray; }
.glow   { box-shadow: 0 0 20px rgba(0,150,255,0.8); }
.hard   { box-shadow: 6px 6px 0 #000; }   /* retro style */
```

# Phase 3: CSS Layout

## 1. Display Properties

display controls how an element behaves in the page flow.

### Block

Starts on a new line and takes the full width. Width and height work. Examples: div, p, h1.

```css
span { display: block; }
```

### Inline

Stays in the same line. Width, height and top and bottom margin do not work. Examples: span, a.

```css
div { display: inline; }
```

### Inline-block

Stays in the same line but also allows width, height and margin.

```css
.box { display: inline-block; width: 100px; height: 100px; background: coral; }
```

### None

Hides the element completely (it takes no space).

```css
.hidden { display: none; }
```

Note: visibility: hidden; also hides the element but it still takes space.

## 2. Position

Controls where an element is placed. Use top, right, bottom and left to move positioned elements.

### Relative

Positioned relative to its own original place. It still keeps its original space.

```css
.box { position: relative; top: 20px; left: 30px; }
```

### Absolute

Positioned relative to the nearest positioned parent (one that is not static). It is removed from the normal flow.

```html
<div class="parent">
  <div class="child">I am inside the corner</div>
</div>
```

```css
.parent {
  position: relative;    /* the reference point */
  width: 300px;
  height: 200px;
  background: lightgray;
}
.child { position: absolute; top: 10px; right: 10px; }
```

### Fixed

Positioned relative to the browser window. It stays in place while scrolling, for example a chat button.

```css
.chat-button { position: fixed; bottom: 20px; right: 20px; }
```

### Sticky

Behaves like relative until you scroll to a point, then sticks like fixed.

```css
.navbar { position: sticky; top: 0; background: white; }
```

## 3. Overflow

Controls what happens when content is bigger than its box.

```css
.box {
  width: 200px;
  height: 100px;
  overflow: visible;   /* default: content spills outside */
  overflow: hidden;    /* extra content is cut off */
  overflow: scroll;    /* always show scrollbars */
  overflow: auto;      /* scrollbar only if needed (most useful) */
  overflow-x: auto;    /* horizontal only */
}
```

## 4. Z-index

Controls which element appears on top when elements overlap. A higher number is on top. It works only on positioned elements (not static).

```css
.box1 { position: absolute; z-index: 1; }
.box2 { position: absolute; z-index: 2; }   /* above box1 */
```

## 5. Float and Clear

float pushes an element to the left or right so text wraps around it. It was used for layouts in the past. Today Flexbox and Grid are used instead, but float is still good for wrapping text around images.

```css
.photo { float: left; margin-right: 15px; width: 150px; }
.footer { clear: both; }   /* left, right, both */
```

# Phase 4: Flexbox

## 1. What is Flexbox?

Flexbox is a one dimensional layout system (a row or a column). It makes aligning, spacing and centering items very easy.

- The parent is the flex container.
- The children are flex items.

```html
<div class="container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>
```

```css
.container {
  display: flex;      /* this turns on Flexbox */
}
.item { background: skyblue; padding: 20px; margin: 5px; }
```

Two axes:

- Main axis: the direction of the items (row by default)
- Cross axis: perpendicular to the main axis

## 2. Flex-direction

Sets the main axis direction.

```css
.container {
  display: flex;
  flex-direction: row;              /* default: left to right */
  flex-direction: row-reverse;      /* right to left */
  flex-direction: column;           /* top to bottom */
  flex-direction: column-reverse;   /* bottom to top */
}
```

## 3. Justify-content

Aligns items along the main axis.

```css
.container {
  display: flex;
  justify-content: flex-start;     /* default: at the start */
  justify-content: center;         /* in the middle */
  justify-content: flex-end;       /* at the end */
  justify-content: space-between;  /* equal space between, none at edges */
  justify-content: space-around;   /* equal space around each item */
  justify-content: space-evenly;   /* perfectly equal spaces */
}
```

## 4. Align-items

Aligns items along the cross axis.

```css
.container {
  display: flex;
  height: 300px;
  align-items: stretch;      /* default: fill the height */
  align-items: flex-start;   /* top */
  align-items: center;       /* middle */
  align-items: flex-end;     /* bottom */
  align-items: baseline;     /* align text baselines */
}
```

Perfect centering (the most famous Flexbox trick):

```css
.container { display: flex; justify-content: center; align-items: center; height: 100vh; }
```

## 5. Flex-wrap

By default, all items try to fit in one line. flex-wrap lets them move to the next line.

```css
.container {
  display: flex;
  flex-wrap: nowrap;        /* default: one line */
  flex-wrap: wrap;          /* wrap to the next line */
  flex-wrap: wrap-reverse;
}
.item { width: 200px; }
```

## 6. Gap

Adds space between flex items (no more margin hacks).

```css
.container {
  display: flex;
  gap: 20px;               /* row and column gap */
  gap: 10px 30px;          /* row-gap column-gap */
}
```

## 7. Align-content

Aligns multiple lines of items along the cross axis. It works only when flex-wrap: wrap is used and there is more than one line.

```css
.container { display: flex; flex-wrap: wrap; height: 500px; align-content: space-between; }
```

Difference: align-items aligns items inside each line. align-content aligns the lines themselves.

## 8. Flex-grow, Flex-shrink and Flex-basis

flex-grow: how much an item grows to fill extra space. Default is 0 (does not grow).

```css
.item1 { flex-grow: 1; }
.item2 { flex-grow: 2; }   /* takes twice as much extra space as item1 */
```

flex-shrink: how much an item shrinks when there is not enough space. Default is 1. Use 0 to stop shrinking.

```css
.item { flex-shrink: 0; }
```

flex-basis: the starting size of an item before growing or shrinking.

Shorthand: flex: grow shrink basis;

```css
.item {
  flex: 1;              /* equal width for all items */
  flex: 1 1 200px;      /* grow, shrink, start at 200px */
}
```

Useful layouts:

```css
.sidebar { flex: 0 0 250px; }          /* fixed sidebar */
.content { flex: 1; }                  /* fills the rest */
.navbar .login { margin-left: auto; }  /* push one item to the far side */
```

# Phase 5: CSS Grid

Flexbox is one dimensional. Grid is two dimensional (rows and columns at the same time). It is perfect for full page layouts and galleries.

## 1. Grid Container

Turn on Grid with display: grid. The parent is the grid container and the children are grid items.

```html
<div class="grid">
  <div>1</div><div>2</div><div>3</div>
  <div>4</div><div>5</div><div>6</div>
</div>
```

```css
.grid { display: grid; grid-template-columns: 1fr 1fr 1fr; }
.grid div { background: lightgreen; padding: 20px; text-align: center; }
```

## 2. Grid Columns

grid-template-columns defines the columns. fr means a fraction of the available space.

```css
.grid {
  display: grid;
  grid-template-columns: 200px 200px 200px;   /* 3 fixed columns */
  grid-template-columns: 1fr 2fr 1fr;         /* middle is twice as wide */
  grid-template-columns: repeat(3, 1fr);      /* same as 1fr 1fr 1fr */
  grid-template-columns: 250px 1fr;           /* sidebar and main content */
}
```

Auto responsive columns (no media query needed):

```css
.grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); }
```

## 3. Grid Rows

grid-template-rows defines the row heights.

```css
.grid { display: grid; grid-template-rows: 100px 200px 100px; grid-auto-rows: 150px; }
```

Spanning cells:

```css
.item1 {
  grid-column: 1 / 3;   /* from line 1 to line 3 (spans 2 columns) */
  grid-row: 1 / 3;      /* spans 2 rows */
}
.item2 { grid-column: span 2; }   /* span 2 columns */
```

## 4. Grid Gap

Space between rows and columns.

```css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;               /* both */
  row-gap: 10px;           /* rows only */
  column-gap: 30px;        /* columns only */
}
```

## 5. Grid-template-areas

Name parts of your layout and place them visually. It reads like a drawing of your page.

```html
<div class="page">
  <header>Header</header>
  <aside>Sidebar</aside>
  <main>Main</main>
  <footer>Footer</footer>
</div>
```

```css
.page {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-rows: 80px 1fr 60px;
  grid-template-areas:
    "header  header"
    "sidebar main"
    "footer  footer";
  height: 100vh;
  gap: 10px;
}
header { grid-area: header; background: #ffb3b3; }
aside  { grid-area: sidebar; background: #b3d9ff; }
main   { grid-area: main;   background: #c6f5c6; }
footer { grid-area: footer; background: #ffe6b3; }
```

## 6. Grid Alignment

```css
.grid { place-items: center; }      /* shorthand for align-items and justify-items */
.grid { justify-content: center; }  /* the whole grid inside the container */
.item { justify-self: end; align-self: center; }   /* one single item */
```

When to use which? Use Flexbox for components (navbars, buttons, cards in a row). Use Grid for page layouts and galleries. They also work great together.

# Phase 6: Responsive Web Design

Responsive design makes your website look good on all screen sizes: phone, tablet and desktop.

First, always add this in your HTML head:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

## 1. Media Queries

Apply CSS only when a condition is true (usually screen width).

```css
.container { background: lightblue; }
/* When the screen is 768px wide or smaller */
@media (max-width: 768px) {
  .container { background: lightcoral; }
}
```

## 2. Mobile-first Design

Design for small screens first, then add styles for larger screens using min-width. This is the modern best practice.

```css
/* Mobile (default): 1 column */
.cards { display: grid; grid-template-columns: 1fr; gap: 16px; }
/* Tablet: 2 columns */
@media (min-width: 768px) {
  .cards { grid-template-columns: repeat(2, 1fr); }
}
/* Desktop: 4 columns */
@media (min-width: 1024px) {
  .cards { grid-template-columns: repeat(4, 1fr); }
}
```

## 3. Responsive Units

Use flexible units instead of fixed pixels.

```css
.container {
  width: 90%;                          /* flexible width */
  max-width: 1200px;                   /* but never too wide */
  margin: 0 auto;
}
h1 {
  font-size: 5vw;                      /* scales with screen width */
  font-size: clamp(1.5rem, 4vw, 3rem); /* min, preferred, max */
}
.hero { height: 100vh; }
```

## 4. Responsive Images

Make images shrink to fit their container.

```css
img { max-width: 100%; height: auto; }
.thumb { width: 100%; height: 250px; object-fit: cover; }   /* cover, contain, fill */
```

## 5. Breakpoints

Breakpoints are the screen widths where your layout changes. Common choices:

| Device | Width |
|--------|-------|
| Mobile | up to 480px (default styles) |
| Large phone or small tablet | 600px |
| Tablet | 768px |
| Laptop | 1024px |
| Desktop | 1200px and above |

```css
/* mobile-first breakpoints */
@media (min-width: 600px)  { /* large phones */ }
@media (min-width: 768px)  { /* tablets */ }
@media (min-width: 1024px) { /* laptops */ }
@media (min-width: 1200px) { /* desktops */ }
```

Tip: Pick breakpoints where your design breaks, not just by device names.

# Phase 7: Advanced CSS

## 1. Pseudo-classes

A pseudo-class styles an element in a special state. It uses a single colon.

## 2. Pseudo-elements

A pseudo-element styles a part of an element, or adds extra content. It uses a double colon.

```css
p::first-letter {
  font-size: 2.5rem;       /* drop cap */
  color: crimson;
}
p::first-line { font-weight: bold; }
::selection { background: yellow; }   /* highlighted text color */
/* ::before and ::after add content (needs the content property) */
.required::after { content: " *"; color: red; }
```

Decorative underline:

```css
h2::after { content: ""; display: block; width: 60px; height: 4px; background: orange; margin-top: 8px; }
```

## 3. CSS Transitions

Make changes happen smoothly instead of instantly.

Syntax: transition: property duration timing-function delay;

```css
.btn { background: tomato; transition: background 0.3s ease; }
.btn:hover { background: darkred; }
```

Timing functions: ease, linear, ease-in, ease-out, ease-in-out.

## 4. CSS Transform

Move, rotate, scale or skew an element without affecting the layout.

```css
.box {
  transform: translate(50px, 20px);   /* move right 50px, down 20px */
  transform: translateX(100px);
  transform: rotate(45deg);
  transform: scale(1.5);              /* 1.5 times bigger */
  transform: skew(20deg);
  transform: rotate(10deg) scale(1.2);  /* combine them */
  transform-origin: top left;         /* the point of rotation or scaling */
}
```

## 5. CSS Animations

Animations run automatically and can have many steps, using @keyframes.

```css
/* Step 1: define the animation */
@keyframes bounce {
  0%   { transform: translateY(0); }
  50%  { transform: translateY(-30px); }
  100% { transform: translateY(0); }
}
/* Step 2: apply it */
.ball {
  width: 50px;
  height: 50px;
  background: orange;
  border-radius: 50%;
  animation: bounce 1s ease-in-out infinite;
}
```

Loading spinner:

```css
@keyframes spin { to { transform: rotate(360deg); } }
.spinner { width: 40px; height: 40px; border: 5px solid #ddd; border-top-color: royalblue; border-radius: 50%; animation: spin 1s linear infinite; }
```

## 6. CSS Variables

Also called custom properties. Store a value once and reuse it everywhere. Change it in one place and the whole site updates.

```css
:root { --primary-color: #4f46e5; --secondary-color: #f59e0b; --radius: 8px; --spacing: 16px; }
.btn { background: var(--primary-color); border-radius: var(--radius); padding: var(--spacing); }
/* fallback value if the variable is missing */
p { color: var(--text-color, black); }
```

Easy dark mode with variables:

```css
:root { --bg: white; --text: black; }
body.dark { --bg: #121212; --text: white; }
body { background: var(--bg); color: var(--text); }
```

## 7. Specificity

When two rules target the same element, specificity decides which one wins. Think of it as a score:

| Selector type | Score |
|---------------|-------|
| Inline style | 1000 |
| ID | 100 |
| Class, attribute, pseudo-class | 10 |
| Element, pseudo-element | 1 |

```html
<p id="intro" class="text">Hello</p>
```

```css
p        { color: blue; }    /* score: 1   */
.text    { color: green; }   /* score: 10  */
#intro   { color: red; }     /* score: 100, wins: the text is red */
```

Rules to remember:

- Higher specificity wins.
- If the score is equal, the later rule in the file wins.
- !important beats everything, but avoid it because it makes code hard to fix.

Best practice: use simple classes for styling, avoid IDs and !important.

## 8. Inheritance

Some CSS properties are passed down from a parent to its children automatically.

Inherited by default: color, font-family, font-size, line-height, text-align.

Not inherited: margin, padding, border, background, width.

```html
<div class="parent">
  <p>I get the parent's color and font.</p>
</div>
```

```css
.parent {
  color: darkgreen;
  font-family: Arial;
  border: 2px solid black;   /* NOT inherited by the p */
}
```

Tip: Setting font-family and color once on body styles the whole page.

# Phase 8: CSS Projects

Projects are where real learning happens. Build each one yourself, then improve it.

## Beginner

### 1. Personal Profile Card

Goal: A centered card with a photo, name, job title, short bio and a contact button.
Skills used: box model, border-radius, box-shadow, text properties, Flexbox centering.
Challenge: add a hover lift effect with transition and transform.

### 2. Simple Login Page

Goal: A centered login form with email, password and a button.
Skills used: forms, padding, focus states, Flexbox.
Challenges: style input:focus, add a "Forgot password?" link, add a gradient background.

### 3. Registration Form

Goal: A form with name, email, password, confirm password, gender (radio), country (select), terms (checkbox) and a submit button.
Skills used: form styling, Grid for two column fields, pseudo-classes.
Challenges: style :required, :valid and :invalid states; put first name and last name side by side with Grid.

## Intermediate

### 4. Responsive Navbar

Goal: A navbar with logo and links that turns into a hamburger menu on mobile.
Skills used: Flexbox, media queries, position, transitions.
Steps: build the desktop navbar with flex, hide the links on small screens with a media query, show a hamburger icon, then toggle the menu with a little JavaScript or the checkbox hack.

```css
.menu { display: flex; gap: 20px; }
.hamburger { display: none; }
@media (max-width: 768px) {
  .menu { display: none; flex-direction: column; position: absolute; top: 60px; left: 0; width: 100%; }
  .menu.open { display: flex; }
  .hamburger { display: block; }
}
```

### 5. Pricing Table

Goal: Three pricing cards (Basic, Pro, Premium) with the middle one highlighted.
Skills used: Flexbox or Grid, box-shadow, hover effects, transform: scale().
Challenges: add a "Most Popular" badge using position: absolute; stack the cards on mobile.

### 6. Product Landing Page

Goal: A full page with Hero, Features, Testimonials, Call-to-action and Footer.
Skills used: Grid, Flexbox, backgrounds, gradients, responsive design, animations.

## Advanced

### 7. Portfolio Website

Goal: A complete personal website to show to employers (Home, About, Skills, Projects, Contact).
Skills used: everything: CSS variables, Grid, Flexbox, animations, responsive design, dark mode.
Challenges: add a dark and light theme toggle, add scroll animations, make it fully responsive, deploy it free on GitHub Pages or Netlify.

### 8. Responsive Dashboard

Goal: An admin dashboard with a sidebar, top bar, stat cards, charts area and a table.
Skills used: Grid layout with grid-template-areas, Flexbox, sticky sidebar, media queries.

```css
.dashboard { display: grid; grid-template-columns: 240px 1fr;
  grid-template-areas: "sidebar header" "sidebar main"; min-height: 100vh; }
.sidebar { grid-area: sidebar; }
.header  { grid-area: header; }
.main    { grid-area: main; }
@media (max-width: 768px) {
  .dashboard { grid-template-columns: 1fr; grid-template-areas: "header" "main"; }
  .sidebar { display: none; }
}
```

# Practice Challenges (Try Without Looking)

1. Make a div 200 by 200 with a red background, rounded corners and a shadow.
2. Center a box both horizontally and vertically using Flexbox. Then do it again using Grid.
3. Build a 3 column layout that becomes 1 column on mobile.
4. Make a button that changes color and moves up slightly when hovered.
5. Create a loading spinner with @keyframes.
6. Make a card with a badge in its top right corner using position.
7. Build a theme with CSS variables, then change the primary color in one place.
8. Style a list so that odd items have a light background using :nth-child.
9. Build a page layout with grid-template-areas: header, sidebar, main, footer.
10. Write two competing rules and predict which one wins using specificity.

# Study Tips

1. Code every example yourself. Do not just read. Type it and change values to see what happens.
2. Use DevTools. Right click a page, choose Inspect, and edit CSS live in the browser.
3. Practice daily, even 30 to 60 minutes.
4. Rebuild real websites. Pick a simple page and try to copy its design.
5. Learn in order. Do not skip the Box Model; Flexbox and Grid depend on it.
6. Play games to learn layouts: Flexbox Froggy (flexboxfroggy.com) and Grid Garden (cssgridgarden.com).
7. Reference documentation: MDN Web Docs (developer.mozilla.org/en-US/docs/Web/CSS).

## What to Learn After CSS

1. JavaScript (make pages interactive)
2. Git and GitHub (save and share your code)
3. CSS frameworks (Tailwind CSS, Bootstrap)
4. Sass or SCSS (CSS with superpowers)
5. React (build modern web apps)
<<<<<<< HEAD

Happy coding. Keep practicing, and build something every week.
=======
>>>>>>> 5636433 (Added CSS_technical_paper.md)
