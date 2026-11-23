# CSS Learning Roadmap: Beginner to Advanced

A step-by-step guide to learning CSS after HTML. Every topic has a **simple explanation** and a **clear example** you can copy and try.

##  Table of Contents

- [Phase 1: CSS Fundamentals](#phase-1-css-fundamentals)
- [Phase 2: CSS Box Model](#phase-2-css-box-model)
- [Phase 3: CSS Layout](#phase-3-css-layout)
- [Phase 4: Flexbox](#phase-4-flexbox)
- [Phase 5: CSS Grid](#phase-5-css-grid)
- [Phase 6: Responsive Web Design](#phase-6-responsive-web-design)
- [Phase 7: Advanced CSS](#phase-7-advanced-css)
- [Phase 8: CSS Projects](#phase-8-css-projects)
- [Bonus: More Examples for Every Topic](#-bonus-more-examples-for-every-topic)
- [Practice Challenges](#️-practice-challenges-try-without-looking)
- [Study Tips](#study-tips)

---

# Phase 1: CSS Fundamentals

## 1. What is CSS?

**CSS** stands for **Cascading Style Sheets**. HTML builds the *structure* of a page (headings, paragraphs, images). CSS controls the *look* (colors, spacing, fonts, layout).

Think of a house: HTML is the walls and rooms, CSS is the paint, furniture and decoration.

**Without CSS:** plain black text on a white page.
**With CSS:** colors, layouts, animations, responsive design.

<h1>Hello World</h1>



h1 {
  color: blue;
  font-size: 40px;
}



---

## 2. Types of CSS

There are three ways to add CSS to an HTML page.

### a) Inline CSS

Written directly inside an HTML tag using the 
style attribute. It affects only that one element.

<p style="color: red; font-size: 20px;">This is red text.</p>



✅ Quick for tests
❌ Hard to maintain, messy for big projects

### b) Internal CSS

Written inside a 
<style> tag in the <head> of the HTML file. It affects only that page.

<!DOCTYPE html>
<html>
<head>
  <style>
    p {
      color: green;
      font-size: 18px;
    }
  </style>
</head>
<body>
  <p>This is green text.</p>
</body>
</html>



✅ Good for single-page demos
❌ Cannot be reused on other pages

### c) External CSS (Best Practice ⭐)

Written in a separate 
.css file and linked to the HTML file. One file can style many pages.

**index.html**

<head>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <p>This is styled by an external file.</p>
</body>
</html>



**style.css**

p {
  color: purple;
  font-size: 18px;
}



✅ Clean, reusable, professional
Always use this in real projects.

---

## 3. CSS Syntax

A CSS rule has a **selector** and a **declaration block**. Each declaration is a **property: value;** pair.

selector {
  property: value;
}



Example:

h1 {
  color: red;        /* property: color, value: red */
  text-align: center;
}



- 
h1 is the **selector** (what to style)
- color is the **property** (what to change)
- red is the **value** (how to change it)
- /* ... */ is a **comment**

---

## 4. CSS Selectors

Selectors choose which HTML elements to style.

### Element selector
Selects all elements of a given tag.

p {
  color: gray;
}



### Class selector (
.)
Selects elements with a class. Can be reused on many elements.

<p class="highlight">Important</p>
<p class="highlight">Also important</p>



.highlight {
  background-color: yellow;
}



### ID selector (
#)
Selects one unique element. An id should be used only once per page.

<h1 id="main-title">Welcome</h1>



#main-title {
  color: darkblue;
}



### Universal selector (
*)
Selects everything.

* {
  margin: 0;
  padding: 0;
}



### Group selector (
,)
Applies the same style to several selectors.

h1, h2, h3 {
  font-family: Arial, sans-serif;
}



### Descendant selector (space)
Selects elements inside another element.

div p {
  color: blue;   /* every <p> inside a <div> */
}



### Child selector (
>)
Selects only direct children.

ul > li {
  list-style: square;
}



### Attribute selector
Selects by attribute.

input[type="text"] {
  border: 2px solid green;
}



---

## 5. Colors

CSS gives many ways to write colors.

/* 1. Color names */
h1 { color: red; }

/* 2. HEX codes */
h1 { color: #ff0000; }

/* 3. RGB */
h1 { color: rgb(255, 0, 0); }

/* 4. RGBA (with transparency, 0 to 1) */
h1 { color: rgba(255, 0, 0, 0.5); }

/* 5. HSL (hue, saturation, lightness) */
h1 { color: hsl(0, 100%, 50%); }



Two main properties:

- 
color changes the **text** color
- background-color changes the **background** color

p {
  color: white;
  background-color: #333;
}



---

## 6. Backgrounds

.hero {
  background-color: #f0f0f0;                 /* solid color */
  background-image: url("banner.jpg");       /* image */
  background-repeat: no-repeat;              /* repeat, repeat-x, repeat-y */
  background-size: cover;                    /* cover, contain, 100px */
  background-position: center;               /* where the image sits */
  background-attachment: fixed;              /* parallax effect */
}



**Gradient background:**

.gradient {
  background: linear-gradient(to right, #ff7e5f, #feb47b);
}



**Shorthand:**

.hero {
  background: #222 url("banner.jpg") no-repeat center / cover;
}



---

## 7. Text Properties

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



Remove the underline from links:

a {
  text-decoration: none;
}



---

## 8. Fonts

body {
  font-family: "Poppins", Arial, sans-serif;  /* first choice, then fallbacks */
  font-size: 16px;
  font-weight: bold;         /* normal, bold, or 100 to 900 */
  font-style: italic;        /* normal, italic */
}



**Using Google Fonts:**

<link href="https://fonts.googleapis.com/css2?family=Poppins&display=swap" rel="stylesheet">



body {
  font-family: "Poppins", sans-serif;
}



**Shorthand:** 
font: style weight size/line-height family;

p {
  font: italic bold 16px/1.5 Arial, sans-serif;
}



---

## 9. Units (px, %, em, rem, vh, vw)

| Unit | Meaning | Type |
|------|---------|------|
| 
px | Pixels, a fixed size | Absolute |
| % | Percentage of the parent element | Relative |
| em | Relative to the **parent's** font size | Relative |
| rem | Relative to the **root (html)** font size | Relative |
| vh | 1% of the viewport **height** | Relative |
| vw | 1% of the viewport **width** | Relative |

html { font-size: 16px; }

.box1 { width: 300px; }        /* always 300 pixels */
.box2 { width: 50%; }          /* half of the parent's width */
.box3 { font-size: 2em; }      /* 2 x parent font size */
.box4 { font-size: 2rem; }     /* 2 x 16px = 32px */
.box5 { height: 100vh; }       /* full screen height */
.box6 { width: 100vw; }        /* full screen width */



💡 **Tip:** Use 
rem for font sizes and spacing, % / vw / vh for flexible layouts.

---

# Phase 2: CSS Box Model

Every HTML element is a rectangular **box**. From inside to outside:

┌──────────────────────────────┐
│           MARGIN             │
│   ┌──────────────────────┐   │
│   │        BORDER        │   │
│   │   ┌──────────────┐   │   │
│   │   │   PADDING    │   │   │
│   │   │  ┌────────┐  │   │   │
│   │   │  │CONTENT │  │   │   │
│   │   │  └────────┘  │   │   │
│   │   └──────────────┘   │   │
│   └──────────────────────┘   │
└──────────────────────────────┘



## 1. Content

The actual text, image or element inside the box. Its size is set with 
width and height.

## 2. Padding

Space **inside** the border, between the content and the border.

.box {
  padding: 20px;                  /* all 4 sides */
  padding: 10px 20px;             /* top-bottom, left-right */
  padding: 10px 20px 30px 40px;   /* top, right, bottom, left (clockwise) */
  padding-left: 15px;             /* one side only */
}



## 3. Border

A line around the padding and content.

.box {
  border: 2px solid black;        /* width style color */
  border-style: dashed;           /* solid, dashed, dotted, double */
  border-bottom: 3px solid red;   /* one side only */
}



## 4. Margin

Space **outside** the border, between this box and other boxes.

.box {
  margin: 20px;
  margin: 10px 20px;
  margin-top: 30px;
  margin: 0 auto;     /* centers a block element horizontally (needs a width) */
}



## 5. Width and Height

.box {
  width: 300px;
  height: 200px;
  max-width: 100%;     /* never wider than this */
  min-height: 100px;   /* never shorter than this */
}



## 6. Box-sizing

By default (
content-box), padding and border are **added** to the width, so a 300px box with 20px padding becomes 340px wide. This is confusing.

border-box includes padding and border **inside** the width, so the box stays 300px.

/* Recommended: put this at the top of every project */
* {
  box-sizing: border-box;
}

.box {
  width: 300px;
  padding: 20px;
  border: 5px solid black;
  /* total width is still 300px */
}



## 7. Border-radius

Rounds corners.

.card   { border-radius: 10px; }        /* soft corners */
.circle { border-radius: 50%; width: 100px; height: 100px; }  /* circle */
.pill   { border-radius: 50px; }        /* pill-shaped button */
.custom { border-radius: 10px 20px 30px 40px; }  /* each corner */



## 8. Box-shadow

Adds a shadow around a box.

Syntax: 
box-shadow: x-offset y-offset blur spread color;

.card {
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.inner-shadow {
  box-shadow: inset 0 0 10px gray;
}



### ✅ Full Box Model Example

<div class="card">Hello Box Model</div>



* { box-sizing: border-box; }

.card {
  width: 300px;
  padding: 20px;
  border: 2px solid #333;
  margin: 30px auto;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  background-color: #fff;
}

…

Created your shortened CSS Learning Roadmap in Markdown format.
File details

    File name: css_learning_roadmap_short.md
    Line count: 1,050 lines
    Format: Markdown (.md)
    Language: Simple English
    Level: Beginner to Advanced

Included topics

    CSS Fundamentals
    CSS Box Model
    CSS Layout
    Flexbox
    CSS Grid
    Responsive Web Design
    Advanced CSS
    CSS Projects
    Practice Questions
    Revision Notes

No emojis or decorative symbols. The file uses simple headings and code examples.
Download
css_learning_roadmap_short.mdDocument

CSS Learning Notes
Beginner to Advanced
A shorter and easier version of the complete CSS roadmap

Purpose
This file explains the important CSS topics in simple English.
Read one topic at a time.
Type every example yourself.
Change the values and observe the result.
Use the practice tasks after each phase.

How to Use This Guide

    Learn the explanation before writing code.
    Create an index.html file.
    Create a style.css file.
    Connect the CSS file to the HTML file.
    Try the example in your browser.
    Change one property at a time.
    Open browser developer tools to inspect the result.
    Complete the practice tasks without copying the answer.
    Review topics that are difficult.
    Build the projects at the end of this guide.

Phase 1
CSS Fundamentals

    What Is CSS

CSS means Cascading Style Sheets.
HTML creates the structure of a web page.
CSS controls how that structure looks.
CSS can change colors, spacing, fonts and layout.
CSS can also make a page responsive.
CSS can add transitions and animations.

Example HTML
<h1>Hello World</h1> <p>Welcome to my website.</p>

Example CSS

h1 {
color: blue;
font-size: 40px;
}

p {
color: gray;
font-size: 18px;
}

The h1 selector chooses the heading.
The color property changes the text color.
The font-size property changes the text size.

    Three Ways to Add CSS

Inline CSS
Inline CSS is written inside an HTML element.
It uses the style attribute.
It is useful for a quick test.
It is difficult to maintain in a large project.
<p style="color: red;">Red paragraph</p>

Internal CSS
Internal CSS is written inside a style element.
The style element is usually placed inside the head.
It is useful for a single page example.
<style> p { color: green; } </style>

External CSS
External CSS is written in a separate CSS file.
The HTML file connects to that file using link.
This is the recommended method for most projects.

HTML
<head> <link rel="stylesheet" href="style.css"> </head>

CSS file named style.css

p {
color: purple;
}

Remember
Use external CSS when building normal projects.
Keep HTML structure and CSS styling separate.

    CSS Rule Structure

A CSS rule contains a selector and declarations.
The selector chooses the HTML element.
A declaration contains a property and a value.
A declaration ends with a semicolon.
Declarations are written inside curly braces.

Example

h2 {
color: darkblue;
text-align: center;
}

h2 is the selector.
color is a property.
darkblue is a value.
text-align is another property.
center is its value.

CSS comments explain code.
A CSS comment starts with slash and star.
A CSS comment ends with star and slash.

Example

/* This is a CSS comment */
h1 {
color: navy;
}

    Basic Selectors

Element selector
Selects every element with the given tag name.

p {
color: gray;
}

Class selector
A class can be reused on many elements.
In CSS, a class selector starts with a dot.

.notice {
background-color: yellow;
}

HTML
<p class="notice">First notice</p> <p class="notice">Second notice</p>

ID selector
An id should identify one element on a page.
In CSS, an id selector starts with a hash sign.

#main-title {
color: navy;
}

Universal selector
Selects all elements.

    {
    box-sizing: border-box;
    }

Group selector
Applies the same styles to several selectors.

h1, h2, h3 {
font-family: Arial, sans-serif;
}

Descendant selector
Selects matching elements anywhere inside another element.

.card p {
color: gray;
}

Child selector
Selects only direct children.

.menu > li {
list-style: none;
}

Attribute selector
Selects elements based on an attribute.

input[type="email"] {
border: 1px solid blue;
}

    Colors

CSS supports named colors.
CSS supports hexadecimal colors.
CSS supports RGB colors.
CSS supports RGBA colors with transparency.
CSS supports HSL colors.

Named color

h1 {
color: red;
}

Hexadecimal color

h1 {
color: #ff0000;
}

RGB color

h1 {
color: rgb(255, 0, 0);
}

RGBA color

.box {
background-color: rgba(255, 0, 0, 0.5);
}

HSL color

.box {
background-color: hsl(0, 100%, 50%);
}

The color property changes text color.
The background-color property changes the background.
Use enough contrast so text is easy to read.

    Backgrounds

background-color adds a solid background color.
background-image adds an image.
background-repeat controls image repetition.
background-size controls image size.
background-position controls image placement.
background-attachment controls how the image moves while scrolling.

Example

.hero {
background-color: lightblue;
background-image: url("banner.jpg");
background-repeat: no-repeat;
background-size: cover;
background-position: center;
}

cover fills the available area.
The image may be cropped to fill the area.
contain shows the full image inside the area.
A gradient creates a smooth color transition.

.gradient {
background: linear-gradient(to right, blue, purple);
}

Use a background image only when the image file exists.
Keep important text readable over background images.

    Text Properties

color changes text color.
text-align aligns text.
text-decoration adds or removes decoration.
text-transform changes letter case.
letter-spacing controls space between letters.
word-spacing controls space between words.
line-height controls space between lines.
text-indent adds space before the first line.
text-shadow adds a shadow behind text.

Example

.article {
color: #333333;
text-align: left;
line-height: 1.6;
letter-spacing: 0.2px;
}

.link {
text-decoration: none;
}

.heading {
text-transform: uppercase;
}

Use line-height to make paragraphs easier to read.
Avoid making long paragraphs too wide.

    Fonts

font-family chooses the font.
font-size changes the size.
font-weight changes thickness.
font-style can make text italic.
Use fallback fonts in case the first font is unavailable.

Example

body {
font-family: Arial, sans-serif;
font-size: 16px;
font-weight: normal;
}

h1 {
font-weight: bold;
}

A font stack provides fallback choices.
A generic family such as sans-serif is useful.
External font services can provide additional fonts.
Do not use too many different fonts on one page.

    CSS Units

px is a fixed CSS length unit.
% is relative to another value, often the parent size.
em is relative to the relevant font size.
rem is relative to the root element font size.
vw is one percent of the viewport width.
vh is one percent of the viewport height.

Example

html {
font-size: 16px;
}

.title {
font-size: 2rem;
}

.container {
width: 90%;
}

.hero {
min-height: 100vh;
}

Use rem for many font sizes and spacing values.
Use percentages for flexible widths.
Use viewport units when the viewport is the intended reference.
Do not use viewport width for every element.

Phase 1 Practice

    Create a heading and change its color.
    Add three paragraphs and give them one shared class.
    Give one heading a unique id.
    Use a group selector for three heading levels.
    Create a paragraph with a background color.
    Add a background image to a hero section.
    Change the font family of the whole page.
    Make a heading uppercase using CSS.
    Compare px and rem font sizes.
    Connect an external CSS file to an HTML page.

Phase 2
CSS Box Model

    Understanding the Box Model

Every HTML element is displayed as a box.
The box contains content, padding, border and margin.
Content is the text, image or child content.
Padding is the space between content and border.
Border is the line around the padding and content.
Margin is the space outside the border.

The order from inside to outside is:
Content
Padding
Border
Margin

Example

.box {
width: 200px;
padding: 20px;
border: 5px solid black;
margin: 30px;
}

    Content and Size

width controls the content width by default.
height controls the content height by default.
max-width sets an upper size limit.
min-width sets a lower size limit.
max-height sets an upper height limit.
min-height sets a lower height limit.

Example

.card {
width: 300px;
min-height: 150px;
max-width: 100%;
}

A fixed width can cause problems on a small screen.
max-width can help prevent an element becoming too wide.
Use min-height when content may need extra space.

    Padding

Padding creates space inside the border.
Padding can be set on all four sides.
Padding can also be set for individual sides.

Example

.box {
padding: 20px;
}

The same value is used on all sides.

.box {
padding: 10px 20px;
}

The first value is top and bottom.
The second value is left and right.

.box {
padding: 10px 20px 30px 40px;
}

The order is top, right, bottom and left.

Individual properties include:
padding-top
padding-right
padding-bottom
padding-left

    Border

A border appears around the padding and content.
A border has width, style and color.

Example

.box {
border: 2px solid black;
}

Common border styles:
solid
dashed
dotted
double
none

Individual border properties:
border-top
border-right
border-bottom
border-left

Example

.card {
border-bottom: 3px solid blue;
}

Use a visible border when an element needs a clear boundary.

    Margin

Margin creates space outside the border.
It separates one element from another.
Margin can be set on all sides or one side.

Example

.box {
margin: 20px;
}

Two values set vertical and horizontal margins.

.box {
margin: 10px 20px;
}

Auto horizontal margins can center a block with a set width.

.container {
width: 80%;
margin: 0 auto;
}

Margin and padding are different.
Padding is inside the border.
Margin is outside the border.

    Box Sizing

The default box-sizing value is content-box.
With content-box, padding and border add to the declared width.
This can make the final element wider than expected.

border-box includes padding and border inside the declared width.

Recommended starting rule

    {
    box-sizing: border-box;
    }

Example

.box {
width: 300px;
padding: 20px;
border: 5px solid black;
}

With border-box, the total width remains 300 pixels.
This makes layout calculations easier.

    Border Radius

border-radius rounds the corners of an element.

Example

.card {
border-radius: 12px;
}

A circle can be created from a square element.

.avatar {
width: 100px;
height: 100px;
border-radius: 50%;
}

A pill shape can use a large radius.

.button {
border-radius: 50px;
}

Different values can be used for different corners.

    Box Shadow

box-shadow adds a shadow around an element.
The common order is horizontal offset, vertical offset, blur, spread and color.

Example

.card {
box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
}

A positive horizontal offset moves the shadow right.
A positive vertical offset moves the shadow down.
Blur makes the shadow softer.
Spread changes the shadow size.
Inset creates a shadow inside the element.

Use shadows gently.
Too many strong shadows can make a page look crowded.

Phase 2 Practice

    Create a box with a width of 200 pixels.
    Add 20 pixels of padding.
    Add a 3 pixel solid border.
    Add 30 pixels of margin.
    Compare content-box and border-box.
    Create a centered card using margin auto.
    Create a circular profile image.
    Add a soft shadow to a card.
    Create a button with rounded corners.
    Build three cards with equal spacing.

Phase 3
CSS Layout Basics

    Display Property

The display property controls how an element participates in layout.
Block elements normally start on a new line.
Inline elements normally stay in the same line.
Inline-block elements can stay in a line and accept width and height.
None removes an element from layout.

Block example

.box {
display: block;
}

Inline example

.label {
display: inline;
}

Inline-block example

.item {
display: inline-block;
width: 100px;
height: 60px;
}

Hide an element

.hidden {
display: none;
}

visibility hidden hides an element but keeps its layout space.

    Position Property

static is the normal default position.
relative keeps the element in normal flow and allows visual movement.
absolute removes the element from normal flow.
fixed positions an element relative to the viewport.
sticky behaves normally until it reaches a scroll position.

Relative example

.box {
position: relative;
top: 10px;
left: 20px;
}

Absolute example

.parent {
position: relative;
}

.child {
position: absolute;
top: 0;
right: 0;
}

The nearest positioned ancestor is usually the reference for absolute positioning.

    Fixed and Sticky Position

Fixed elements stay attached to the viewport.
They can be useful for floating action buttons.
They may cover content if placed carelessly.

Example

.help-button {
position: fixed;
right: 20px;
bottom: 20px;
}

Sticky elements remain in normal flow.
They stick after reaching the given offset.
Sticky often needs a top value.

Example

.navbar {
position: sticky;
top: 0;
}

Check parent overflow settings if sticky does not work as expected.

    Overflow

Overflow controls content that does not fit inside an element.
visible allows content to extend outside.
hidden clips extra content.
scroll provides scrollbars.
auto adds scrollbars when needed.

Example

.text-box {
width: 200px;
height: 100px;
overflow: auto;
}

overflow-x controls horizontal overflow.
overflow-y controls vertical overflow.
Use overflow-x auto for wide tables on small screens.

    Z Index

z-index controls stacking order in a stacking context.
A larger z-index often appears above a smaller one.
The element usually needs to be positioned or participate in a relevant layout context.
Stacking contexts can affect which element appears on top.

Example

.first {
position: relative;
z-index: 1;
}

.second {
position: relative;
z-index: 2;
}

The second element can appear above the first when they overlap.
Do not solve every layout issue by using extremely large z-index values.

    Float and Clear

Float moves an element to the left or right.
Text can wrap around a floated image.
Float is not the recommended method for modern page layouts.
Use Flexbox or Grid for most layout work.

Example

.photo {
float: left;
margin-right: 15px;
width: 150px;
}

clear prevents an element from sitting beside floated content.

.footer {
clear: both;
}

Learn float to understand older layouts and text wrapping.

Phase 3 Practice

    Show two inline elements on one line.
    Change a span to display block.
    Create three inline-block boxes.
    Make a badge appear in the corner of a card.
    Create a fixed help button.
    Make a navigation bar sticky.
    Create a scrollable text box.
    Overlap two boxes and test z-index.
    Wrap text around an image using float.
    Compare display none and visibility hidden.

Phase 4
Flexbox

    What Is Flexbox

Flexbox is a one-dimensional layout system.
It arranges items in a row or a column.
The parent is called the flex container.
Its direct children are called flex items.
Flexbox is useful for navigation bars, card rows and alignment.

HTML
<div class="container"> <div class="item">One</div> <div class="item">Two</div> <div class="item">Three</div> </div>

CSS

.container {
display: flex;
gap: 10px;
}

.item {
padding: 20px;
background: lightblue;
}

    Main Axis and Cross Axis

The main axis follows flex-direction.
The cross axis is perpendicular to the main axis.
The default direction is row.
For row, the main axis is horizontal.
For row, the cross axis is vertical.
For column, the main axis is vertical.
For column, the cross axis is horizontal.

Remember
justify-content works along the main axis.
align-items works along the cross axis.

    Flex Direction

row places items in a row.
row-reverse places items in the opposite row direction.
column places items vertically.
column-reverse places items in the opposite column direction.

Example

.container {
display: flex;
flex-direction: column;
}

Use row for horizontal navigation.
Use column for a vertical menu.

    Justify Content

justify-content aligns items along the main axis.
flex-start places items at the start.
center places items in the middle.
flex-end places items at the end.
space-between places free space between items.
space-around gives space around items.
space-evenly distributes free space evenly.

Example

.container {
display: flex;
justify-content: space-between;
}

The visible result depends on the flex direction.

    Align Items

align-items aligns items along the cross axis.
stretch is the default in many flex situations.
flex-start places items at the cross-axis start.
center places items in the middle.
flex-end places items at the cross-axis end.
baseline aligns text baselines.

Example

.container {
display: flex;
align-items: center;
height: 200px;
}

The container needs available cross-axis space for alignment to be noticeable.

    Centering with Flexbox

Flexbox can center an item horizontally and vertically.

.container {
display: flex;
justify-content: center;
align-items: center;
min-height: 100vh;
}

justify-content centers along the main axis.
align-items centers along the cross axis.
The direction is row unless changed.

    Flex Wrap and Gap

flex-wrap controls whether items can move to another line.
nowrap keeps items on one line.
wrap allows another line.
wrap-reverse reverses the cross-axis line order.

Example

.gallery {
display: flex;
flex-wrap: wrap;
gap: 16px;
}

Gap adds space between flex items.
It avoids needing margins on every item.

    Align Content

align-content aligns multiple flex lines.
It requires wrapping and more than one line.
It is different from align-items.
align-items aligns items within a line.
align-content aligns the lines as a group.

Example

.gallery {
display: flex;
flex-wrap: wrap;
align-content: center;
min-height: 400px;
}

    Grow, Shrink and Basis

flex-grow controls how extra space is shared.
A value of zero means the item does not grow.
A larger grow value receives a larger share of extra space.

flex-shrink controls shrinking when space is limited.
A value of zero prevents the item from shrinking.

flex-basis sets the initial main size of an item.

Example

.item {
flex: 1 1 200px;
}

The shorthand order is grow, shrink and basis.

    Flexbox Navbar Example

HTML
<nav class="navbar"> <div class="logo">My Site</div> <ul class="menu"> <li>Home</li> <li>About</li> <li>Contact</li> </ul> </nav>

CSS

.navbar {
display: flex;
justify-content: space-between;
align-items: center;
padding: 16px 24px;
background: #222;
color: white;
}

.menu {
display: flex;
gap: 20px;
list-style: none;
}

The navbar uses Flexbox for the main row.
The menu uses Flexbox for its list items.

Phase 4 Practice

    Put three boxes in one row.
    Change the direction to column.
    Center the boxes on the main axis.
    Center the boxes on the cross axis.
    Create a vertical sidebar menu.
    Make a row of cards wrap on small screens.
    Add a gap between all items.
    Make one item grow more than another.
    Create a navbar with a logo and menu.
    Center a box in the full viewport.

Phase 5
CSS Grid

    What Is CSS Grid

Grid is a two-dimensional layout system.
It controls rows and columns together.
The parent is called the grid container.
Its direct children are grid items.
Grid is useful for page layouts, galleries and dashboards.

HTML
<div class="grid"> <div>One</div> <div>Two</div> <div>Three</div> <div>Four</div> </div>

CSS

.grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 12px;
}

    Grid Columns

grid-template-columns defines column sizes.
Pixels create fixed column sizes.
fr distributes available space.
repeat reduces repeated values.
minmax defines a minimum and maximum size.

Example

.grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
}

Two columns

.grid {
grid-template-columns: 200px 1fr;
}

The first column is fixed.
The second column receives the remaining available space.

    Responsive Grid Columns

auto-fit and minmax can create flexible columns.
This can reduce the need for many media queries.

Example

.cards {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
gap: 20px;
}
As this conversation gets longer, ChatGPT may lose track of details from earlier in the chat. Upgrade for more context in every conversation.


