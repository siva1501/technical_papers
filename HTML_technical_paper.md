# HTML Complete Course: From Zero to Advanced

> Learn one topic completely before moving to the next. No rushing.

For every topic you will find: **What it is → Why we use it → Syntax → Examples → Difference from similar tags → Common mistakes → Practice**.

---

## Course Roadmap

| Module | Topics | Lessons |
| --- | --- | --- |
| A. Basics | Introduction, Structure, Basic Tags, Formatting, Comments, Attributes | 1-6 |
| B. Links, Images, Lists | `<a>`, `<img>`, `<ol>`, `<ul>`, `<dl>` | 7-11 |
| C. Tables | `<table>` and everything inside it | 12-18 |
| D. Forms | `<form>`, inputs, buttons, select, etc. | 19-27 |
| E. Semantic Tags | `<header>`, `<nav>`, `<main>`... | 28 |
| F. Multimedia | `<audio>`, `<video>`, `<iframe>`... | 29 |
| G. Advanced HTML | Entities, meta, accessibility, SVG, Canvas, SEO... | 30 |
| H. What's Next | CSS, JavaScript | 31 |

---

# MODULE A: HTML BASICS

---

## Lesson 1: Introduction (What is HTML? How does it work?)

### What is HTML?
**HTML** stands for **HyperText Markup Language**.

- **HyperText**: text that contains links to other pages.
- **Markup Language**: a language that uses *tags* to describe the structure and meaning of content.

HTML creates the **structure** of a website. Think of a house:

| Part of the house | Technology |
| --- | --- |
| Walls, rooms, doors (structure) | **HTML** |
| Paint, furniture, decoration (style) | **CSS** |
| Electricity, lifts, switches (behaviour) | **JavaScript** |

> HTML is **not** a programming language. It has no logic, loops, or conditions. It is a **markup language**.

### Example
Imagine a website with:
- Heading: Welcome to My Website
- Paragraph: This is my first website.
- Button: Click Me

HTML code:
```html
<h1>Welcome to My Website</h1>
<p>This is my first website.</p>
<button>Click Me</button>
```

### How does HTML work?
1. You write HTML in a file ending with `.html`.
2. You open it in a browser (Chrome, Firefox, Edge, Safari).
3. The browser **reads** the code from top to bottom.
4. The browser **renders** (draws) the page on screen.

```
index.html  →  Browser reads tags  →  Webpage displayed
```

When you visit a real website, your browser asks a **server** for the HTML file, downloads it, and then displays it.

### Tags and Elements
A **tag** is a keyword inside angle brackets `< >`.

```html
<p>Hello World</p>
```

| Part | Name |
| --- | --- |
| `<p>` | Opening tag |
| `Hello World` | Content |
| `</p>` | Closing tag (has a `/`) |
| Whole line | **HTML Element** |

**Empty (void) elements** have no content and no closing tag: `<br>`, `<hr>`, `<img>`, `<input>`.

### Common Mistakes
- Forgetting the closing tag: `<p>Hello` ❌ → `<p>Hello</p>` ✅
- Saving the file as `index.html.txt` instead of `index.html`.
- Calling HTML a "programming language".

### Practice
1. What does HTML stand for?
2. What is the difference between a tag and an element?
3. Name three empty elements.

---

## Lesson 2: HTML Structure

### What is it?
Every HTML page follows a standard skeleton.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>My First Website</title>
</head>
<body>
    <h1>Welcome to HTML</h1>
    <p>This is my first webpage.</p>
</body>
</html>
```

### Line-by-line explanation

| Tag | Explanation |
| --- | --- |
| `<!DOCTYPE html>` | Tells the browser this is an **HTML5** document. Not a tag, it's a declaration. Must be the first line. |
| `<html>` | The **root element**. Everything lives inside it. |
| `<head>` | Contains **information about the page** (not shown on the page): title, meta tags, CSS links. |
| `<title>` | Text shown in the **browser tab**. |
| `<body>` | Contains everything **visible** on the page. |
| `<h1>` | Main heading. |
| `<p>` | Paragraph. |

### Understanding `<head>` vs `<body>`

| `<head>` | `<body>` |
| --- | --- |
| Invisible information | Visible content |
| Title, meta, links to CSS | Text, images, buttons, tables |
| Only one per page | Only one per page |

### The `lang` attribute
`<html lang="en">` tells browsers and search engines the page language. It helps screen readers pronounce words correctly.

### The `<meta charset>` tag
`<meta charset="UTF-8">` lets the page show all characters (English, Hindi, Marathi, emojis 😀).

### Tree structure (how the browser sees it)
```
html
├── head
│   ├── meta
│   └── title
└── body
    ├── h1
    └── p
```

### Common Mistakes
- Writing content outside `<body>`.
- Forgetting `<!DOCTYPE html>` (browser enters "quirks mode").
- Putting `<title>` inside `<body>`.
- Using two `<body>` tags.

### Practice
1. Which tag shows text in the browser tab?
2. Where does visible content go: `<head>` or `<body>`?
3. Write the HTML skeleton from memory.

---

## Lesson 3: Basic Tags

### 3.1 Headings `<h1>` to `<h6>`

**What:** Six heading levels. `<h1>` is the largest and most important; `<h6>` is the smallest.

```html
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6</h6>
```

**Why:** Headings organise content and help **SEO** and **accessibility**.

**Rules:**
- Use **one `<h1>`** per page (the main topic).
- Don't skip levels (`<h1>` then `<h4>`).
- Don't use headings just to make text big. Use CSS for that.

### 3.2 Paragraph `<p>`

```html
<p>This is the first paragraph.</p>
<p>This is the second paragraph.</p>
```

- Browsers add space before and after each paragraph.
- Extra spaces and line breaks in your code are **collapsed into one space**:

```html
<p>This    text     has
many    spaces.</p>
```
Output: `This text has many spaces.`

### 3.3 Line Break `<br>`

**What:** Moves text to the next line **without** starting a new paragraph. Empty element.

```html
<p>Roses are red,<br>
Violets are blue,<br>
HTML is fun,<br>
And so are you.</p>
```

**Mistake:** Using many `<br><br><br>` for spacing. Use CSS margin instead.

### 3.4 Horizontal Rule `<hr>`

**What:** Draws a horizontal line to separate content (a thematic break).

```html
<h2>Chapter 1</h2>
<p>Some text...</p>
<hr>
<h2>Chapter 2</h2>
<p>More text...</p>
```

### Difference: `<br>` vs `<p>`

| `<br>` | `<p>` |
| --- | --- |
| New line only | New paragraph with spacing |
| No closing tag | Has closing tag |
| For poems, addresses | For blocks of text |

### `<pre>` bonus
`<pre>` preserves spaces and line breaks exactly as typed (good for code).
```html
<pre>
Line 1
    Line 2 (indented)
</pre>
```

### Practice
1. Create a page with all six headings.
2. Write a four-line poem using `<br>`.
3. Separate two sections with `<hr>`.

---

## Lesson 4: Text Formatting

### Overview

| Tag | Meaning | Looks like |
| --- | --- | --- |
| `<b>` | Bold (no extra importance) | **bold** |
| `<strong>` | Strong importance | **strong** |
| `<i>` | Italic (alternate voice) | *italic* |
| `<em>` | Emphasis (stress) | *emphasis* |
| `<u>` | Underline | <u>underline</u> |
| `<mark>` | Highlight | ==highlight== |
| `<small>` | Smaller text | small print |
| `<del>` | Deleted text | ~~deleted~~ |
| `<ins>` | Inserted text | underlined |
| `<sub>` | Subscript | H₂O |
| `<sup>` | Superscript | x² |

### Examples

```html
<p>This is <b>bold</b> text.</p>
<p>This is <strong>very important</strong> text.</p>
<p>This is <i>italic</i> text.</p>
<p>I <em>really</em> love HTML.</p>
<p>This is <u>underlined</u> text.</p>
<p>Remember to <mark>submit your homework</mark>.</p>
<p><small>Terms and conditions apply.</small></p>
<p>Price: <del>₹999</del> <ins>₹499</ins></p>
<p>Water is H<sub>2</sub>O.</p>
<p>Area = side<sup>2</sup>. Also 10<sup>3</sup> = 1000.</p>
```

### Difference between similar tags

| `<b>` vs `<strong>` | |
| --- | --- |
| `<b>` | Only **visual** bold |
| `<strong>` | Bold **+ meaning**: important. Screen readers stress it. ✅ Prefer this |

| `<i>` vs `<em>` | |
| --- | --- |
| `<i>` | Visual italic (foreign words, thoughts, ship names) |
| `<em>` | Stressed emphasis. Changes sentence meaning. ✅ Prefer this for emphasis |

Example of how `<em>` changes meaning:
```html
<p>I <em>never</em> said she stole it.</p>
<p>I never said <em>she</em> stole it.</p>
```

### Combining (nesting) tags
```html
<p><strong><em>Bold and italic</em></strong></p>
```
Close tags in reverse order: last opened, first closed.

### Common Mistakes
- Wrong nesting: `<b><i>text</b></i>` ❌ → `<b><i>text</i></b>` ✅
- Using `<u>` for text that is not a link (users think it's clickable).
- Using `<b>` and `<i>` when `<strong>` and `<em>` are more meaningful.

### Practice
1. Write: "Water boils at 100°C" with `°C` formatted properly, and "H₂O" using `<sub>`.
2. Show an old price crossed out and a new price inserted.
3. Highlight one word in a sentence.

---

## Lesson 5: Comments

### What is it?
A comment is a note in your code that the **browser ignores**. Visitors cannot see it on the page.

### Syntax
```html
<!-- This is a comment -->
```

### Examples
```html
<!-- Main heading of the page -->
<h1>My Website</h1>

<!-- 
   This comment
   spans multiple lines
-->
<p>Hello</p>

<!-- <p>This paragraph is hidden (commented out)</p> -->
```

### Why use comments?
1. Explain your code to yourself and teammates.
2. Temporarily **disable** code without deleting it.
3. Mark sections (e.g., `<!-- Header Start -->`, `<!-- Header End -->`).

### Common Mistakes
- Thinking comments are secret. Anyone can see them via **View Source**. Never put passwords in comments.
- Nesting comments (`<!-- <!-- --> -->`) breaks the code.
- Forgetting `-->`.

### Shortcut
In VS Code: **Ctrl + /** (Windows) or **Cmd + /** (Mac).

### Practice
1. Comment out one paragraph and check the browser.
2. Add a comment before each section of your page.

---

## Lesson 6: Attributes

### What is it?
Attributes give **extra information** to an element. They always go inside the **opening tag** as `name="value"`.

```html
<tagname attribute="value">Content</tagname>
```

### 6.1 `id`
A **unique** identifier. No two elements may share an id.
```html
<h1 id="main-title">Welcome</h1>
```
Uses: link to a section (`<a href="#main-title">`), target with CSS/JavaScript.

### 6.2 `class`
A **reusable** group name. Many elements can share a class; one element can have multiple classes.
```html
<p class="highlight">First</p>
<p class="highlight">Second</p>
<p class="highlight big">Third (two classes)</p>
```

| `id` vs `class` | `id` | `class` |
| --- | --- | --- |
| Unique? | Yes | No |
| Per element | One | Many (space separated) |
| CSS selector | `#name` | `.name` |

### 6.3 `style`
Adds **inline CSS** directly.
```html
<p style="color: red; font-size: 20px;">Red text</p>
<h1 style="background-color: yellow;">Yellow heading</h1>
```
> Fine for learning and quick tests. In real projects, use a separate CSS file.

### 6.4 `title`
Shows a **tooltip** when you hover the mouse.
```html
<p title="I am a tooltip!">Hover over me</p>
<abbr title="HyperText Markup Language">HTML</abbr>
```

### Other useful attributes (preview)

| Attribute | Used on | Purpose |
| --- | --- | --- |
| `href` | `<a>` | Link address |
| `src` | `<img>` | Image path |
| `alt` | `<img>` | Alternative text |
| `lang` | `<html>` | Language |
| `hidden` | any | Hides element |

### Rules
- Always use **quotes** around values.
- Use **lowercase** names.
- Multiple attributes are separated by spaces.

```html
<p id="intro" class="text" style="color: blue;" title="Introduction">Hello</p>
```

### Common Mistakes
- Duplicate `id`s on one page.
- Missing quotes: `class=big text` ❌.
- Putting the attribute in the closing tag.

### Practice
1. Create three paragraphs with the same class and one with a unique id.
2. Add a tooltip to a heading.
3. Style a paragraph with blue text and a yellow background using `style`.

---

## Mini Project 1: Personal Introduction Page

1. Open VS Code and create a folder named `HTML_Learning`.
2. Create a file named `index.html`.
3. Write the basic structure.
4. Display:
   - Your **name** as a heading
   - Your **education** as a paragraph
   - Your **hobbies** as another paragraph
   - Your **hometown** as a heading

**Sample solution:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>About Me</title>
</head>
<body>
    <!-- Name -->
    <h1 id="name">Rahul Sharma</h1>

    <!-- Education -->
    <p>I am studying <strong>B.Sc. Computer Science</strong> at Mumbai University.</p>

    <!-- Hobbies -->
    <p class="hobbies">My hobbies are <em>cricket</em>, <em>reading</em> and <mark>coding</mark>.</p>

    <hr>

    <!-- Hometown -->
    <h2 title="Where I live">Hometown: Mumbai</h2>
</body>
</html>
```
Open the file in your browser (double-click it, or right-click → Open with → Chrome).

---

# MODULE B: LINKS, IMAGES AND LISTS

---

## Lesson 7: Links `<a>`

### What is it?
The **anchor** tag creates a clickable link to another page, file, email, or a place on the same page.

### Syntax
```html
<a href="URL">Link text</a>
```

### Examples

**External link**
```html
<a href="https://www.wikipedia.org">Visit Wikipedia</a>
```

**Open in a new tab**
```html
<a href="https://www.wikipedia.org" target="_blank" rel="noopener noreferrer">Wikipedia</a>
```

**Link to another page of your site (relative path)**
```html
<a href="about.html">About Us</a>
<a href="pages/contact.html">Contact</a>
<a href="../index.html">Home</a>
```

**Link to a section on the same page**
```html
<a href="#section2">Jump to Section 2</a>
...
<h2 id="section2">Section 2</h2>
```

**Email and phone**
```html
<a href="mailto:hello@example.com">Send email</a>
<a href="tel:+911234567890">Call us</a>
```

**Download a file**
```html
<a href="notes.pdf" download>Download Notes</a>
```

**Image as a link**
```html
<a href="https://example.com"><img src="logo.png" alt="Company logo"></a>
```

### Attributes

| Attribute | Purpose |
| --- | --- |
| `href` | Destination (required) |
| `target="_blank"` | Open in new tab |
| `target="_self"` | Same tab (default) |
| `rel` | Relationship; use `noopener noreferrer` with `_blank` for security |
| `download` | Download instead of open |
| `title` | Tooltip |

### Absolute vs Relative URL

| Absolute | Relative |
| --- | --- |
| `https://site.com/about.html` | `about.html` |
| Full address, for other websites | Path from the current file, for your own files |

### Common Mistakes
- Forgetting `https://` for external sites (browser treats it as a local file).
- Vague text like "click here". Use descriptive text: "Read the HTML guide".
- Broken relative paths (wrong folder).

### Practice
1. Make a menu: Home, About, Contact.
2. Create a link that opens Google in a new tab.
3. Make an in-page "Back to top" link.

---

## Lesson 8: Images `<img>`

### What is it?
Displays an image. It is an **empty element** (no closing tag).

### Syntax
```html
<img src="image.jpg" alt="Description of the image">
```

### Examples
```html
<!-- Same folder -->
<img src="cat.jpg" alt="A grey cat sleeping on a sofa">

<!-- In an images folder -->
<img src="images/cat.jpg" alt="A grey cat">

<!-- From the internet -->
<img src="https://example.com/photo.jpg" alt="Sample photo">

<!-- With size -->
<img src="cat.jpg" alt="Cat" width="300" height="200">

<!-- Lazy loading (loads only when scrolled near) -->
<img src="big.jpg" alt="Large photo" loading="lazy">
```

### Attributes

| Attribute | Purpose |
| --- | --- |
| `src` | Image path (required) |
| `alt` | Text shown if image fails; read by screen readers (required) |
| `width`, `height` | Size in pixels |
| `title` | Tooltip |
| `loading="lazy"` | Faster page loads |

### Image formats

| Format | Best for |
| --- | --- |
| JPG/JPEG | Photos |
| PNG | Logos, transparency |
| GIF | Simple animations |
| SVG | Icons, scalable graphics |
| WebP | Modern, small file size |

### Common Mistakes
- Missing `alt`.
- Wrong path, which shows a broken-image icon.
- Setting both width and height with the wrong ratio (stretched image).
- Huge image files that slow the page.

### Practice
1. Show your photo with proper `alt` text.
2. Make an image that links to a website.
3. Deliberately break the `src` and observe the `alt` text.

---

## Lesson 9: Ordered Lists `<ol>`, `<li>`

### What is it?
A **numbered** list. `<ol>` = ordered list, `<li>` = list item.

### Syntax
```html
<ol>
    <li>Wake up</li>
    <li>Brush teeth</li>
    <li>Have breakfast</li>
</ol>
```
Output:
1. Wake up
2. Brush teeth
3. Have breakfast

### Attributes

| Attribute | Example | Result |
| --- | --- | --- |
| `type` | `<ol type="A">` | A, B, C |
| | `<ol type="a">` | a, b, c |
| | `<ol type="I">` | I, II, III |
| | `<ol type="i">` | i, ii, iii |
| `start` | `<ol start="5">` | 5, 6, 7 |
| `reversed` | `<ol reversed>` | 3, 2, 1 |

```html
<ol type="I" start="3">
    <li>Third</li>
    <li>Fourth</li>
</ol>
```

### Nested list
```html
<ol>
    <li>Fruits
        <ol type="a">
            <li>Apple</li>
            <li>Mango</li>
        </ol>
    </li>
    <li>Vegetables</li>
</ol>
```

### Use when
Order matters: steps, rankings, instructions.

### Common Mistakes
- Putting text directly inside `<ol>` without `<li>`.
- Placing a nested list *outside* the parent `<li>`.

### Practice
1. List the steps to make tea.
2. Make a Top 5 movies list that starts from 1 and uses Roman numerals.

---

## Lesson 10: Unordered Lists `<ul>`, `<li>`

### What is it?
A **bulleted** list where order doesn't matter.

### Syntax
```html
<ul>
    <li>Milk</li>
    <li>Bread</li>
    <li>Eggs</li>
</ul>
```

### Bullet styles (use CSS)
```html
<ul style="list-style-type: square;">...</ul>
<ul style="list-style-type: circle;">...</ul>
<ul style="list-style-type: none;">...</ul>
```

### Nested list
```html
<ul>
    <li>Programming languages
        <ul>
            <li>Python</li>
            <li>JavaScript</li>
        </ul>
    </li>
    <li>Databases</li>
</ul>
```

### Navigation menu (very common real use)
```html
<ul>
    <li><a href="index.html">Home</a></li>
    <li><a href="about.html">About</a></li>
    <li><a href="contact.html">Contact</a></li>
</ul>
```

### `<ol>` vs `<ul>`

| `<ol>` | `<ul>` |
| --- | --- |
| Numbers/letters | Bullets |
| Order matters | Order doesn't matter |

### Practice
1. Make a shopping list.
2. Create a menu with links.
3. Make a list with a nested sub-list.

---

## Lesson 11: Description Lists `<dl>`, `<dt>`, `<dd>`

### What is it?
A list of **terms and their descriptions** (like a glossary).

| Tag | Meaning |
| --- | --- |
| `<dl>` | Description list container |
| `<dt>` | Description term |
| `<dd>` | Description details |

### Syntax
```html
<dl>
    <dt>HTML</dt>
    <dd>Language used to build the structure of web pages.</dd>

    <dt>CSS</dt>
    <dd>Language used to style web pages.</dd>

    <dt>JavaScript</dt>
    <dd>Language used to make pages interactive.</dd>
</dl>
```

One term can have multiple descriptions:
```html
<dl>
    <dt>Coffee</dt>
    <dd>Hot drink</dd>
    <dd>Contains caffeine</dd>
</dl>
```

### Use when
Glossaries, FAQs, product specs, metadata (key: value).

### Practice
Create a glossary of 4 computer terms (RAM, CPU, ROM, OS).

---

# MODULE C: TABLES

---

## Lessons 12-18: Tables (complete explanation)

### Lesson 12: Table Basics `<table>`
`<table>` is the container for tabular data (rows and columns). Use tables for **data**, never for page layout.

```html
<table border="1">
    <tr>
        <th>Name</th>
        <th>Marks</th>
    </tr>
    <tr>
        <td>Amit</td>
        <td>85</td>
    </tr>
</table>
```
> `border="1"` is only for learning. Use CSS `border` in real projects.

### Lesson 13: Table Rows `<tr>`
**Table Row.** Each `<tr>` creates one horizontal row. It contains `<th>` or `<td>` cells.

### Lesson 14: Table Headers `<th>`
**Table Header cell.** Bold and centred by default. Describes a column or row.

```html
<tr>
    <th>Name</th>
    <th>City</th>
</tr>
```
Add `scope="col"` (column header) or `scope="row"` (row header) for accessibility.

### Lesson 15: Table Data `<td>`
**Table Data cell.** Holds the actual content.

```html
<tr>
    <td>Priya</td>
    <td>Pune</td>
</tr>
```

### Lesson 16: Table Sections `<thead>`, `<tbody>`, `<tfoot>`

| Tag | Purpose |
| --- | --- |
| `<thead>` | Header rows |
| `<tbody>` | Main body rows |
| `<tfoot>` | Footer/summary rows |

```html
<table border="1">
    <thead>
        <tr><th>Item</th><th>Price</th></tr>
    </thead>
    <tbody>
        <tr><td>Pen</td><td>₹10</td></tr>
        <tr><td>Book</td><td>₹90</td></tr>
    </tbody>
    <tfoot>
        <tr><td>Total</td><td>₹100</td></tr>
    </tfoot>
</table>
```

### Lesson 17: Merging Cells `colspan`, `rowspan`

**`colspan`**: a cell spans multiple **columns**.
```html
<table border="1">
    <tr>
        <th colspan="2">Student Details</th>
    </tr>
    <tr>
        <td>Name</td>
        <td>Amit</td>
    </tr>
</table>
```

**`rowspan`**: a cell spans multiple **rows**.
```html
<table border="1">
    <tr>
        <td rowspan="2">Monday</td>
        <td>Maths</td>
    </tr>
    <tr>
        <td>Science</td>
    </tr>
</table>
```
> When a cell spans, the cells it covers must be **removed** from the code, otherwise the table shifts.

### Lesson 18: Table Caption `<caption>`
Title of the table. Must be the **first child** of `<table>`.
```html
<table border="1">
    <caption>Monthly Expenses</caption>
    <tr><th>Item</th><th>Cost</th></tr>
    <tr><td>Rent</td><td>₹8000</td></tr>
</table>
```

### Complete table example
```html
<table border="1">
    <caption>Class Result</caption>
    <thead>
        <tr>
            <th>Roll No</th>
            <th>Name</th>
            <th colspan="2">Marks</th>
        </tr>
        <tr>
            <th></th><th></th>
            <th>Maths</th><th>Science</th>
        </tr>
    </thead>
    <tbody>
        <tr><td>1</td><td>Amit</td><td>85</td><td>90</td></tr>
        <tr><td>2</td><td>Sara</td><td>92</td><td>88</td></tr>
    </tbody>
</table>
```

### Common Mistakes
- Putting `<td>` directly in `<table>` without `<tr>`.
- Rows having different numbers of cells (without colspan/rowspan).
- Using tables for page layout.
- Forgetting to remove covered cells after merging.

### Practice
1. Create a weekly timetable with `<caption>`.
2. Build a bill with `<thead>`, `<tbody>`, `<tfoot>`.
3. Make a table where "Name" spans two rows using `rowspan`.

---

# MODULE D: FORMS

---

## Lesson 19: Form `<form>`

### What is it?
A form collects information from the user (login, signup, search, feedback) and sends it to a server.

### Syntax
```html
<form action="/submit" method="post">
    <!-- form controls go here -->
</form>
```

### Attributes

| Attribute | Purpose |
| --- | --- |
| `action` | URL where data is sent |
| `method` | `get` or `post` |
| `target` | Where to show the response (`_blank`) |
| `autocomplete` | `on`/`off` browser suggestions |
| `novalidate` | Skip browser validation |
| `enctype` | Needed for file upload: `multipart/form-data` |

### GET vs POST

| GET | POST |
| --- | --- |
| Data visible in URL | Data hidden in request body |
| For searches, filters | For logins, signups, sensitive data |
| Can be bookmarked | Cannot |
| Limited size | Large data allowed |

---

## Lesson 20: Input `<input>`

### What is it?
The most important form element. Its behaviour depends on the `type` attribute. Empty element.

```html
<input type="text" name="username" placeholder="Enter your name">
```

### Common attributes

| Attribute | Purpose |
| --- | --- |
| `type` | Kind of input |
| `name` | Key sent to the server (**required** for data to be submitted) |
| `id` | Unique id (connects with `<label>`) |
| `value` | Default/current value |
| `placeholder` | Hint text |
| `required` | Must be filled |
| `disabled` | Cannot be used or submitted |
| `readonly` | Visible, can't be edited, still submitted |
| `maxlength`, `minlength` | Text length limits |
| `min`, `max`, `step` | Number/date/range limits |
| `pattern` | Regular-expression validation |
| `autofocus` | Focus on page load |

### All Important Input Types

**1. text**: single-line text
```html
<input type="text" name="fullname" placeholder="Full name">
```

**2. password**: hides characters
```html
<input type="password" name="pwd" minlength="8">
```

**3. email**: validates email format
```html
<input type="email" name="email" placeholder="you@example.com" required>
```

**4. number**: numeric only
```html
<input type="number" name="age" min="1" max="100" step="1">
```

**5. date**: calendar picker
```html
<input type="date" name="dob">
```

**6. time**: time picker
```html
<input type="time" name="meeting">
```

**7. radio**: choose **one** from a group (same `name`)
```html
<input type="radio" id="m" name="gender" value="male">
<label for="m">Male</label>
<input type="radio" id="f" name="gender" value="female">
<label for="f">Female</label>
```

**8. checkbox**: choose **zero or many**
```html
<input type="checkbox" id="c1" name="hobby" value="reading">
<label for="c1">Reading</label>
<input type="checkbox" id="c2" name="hobby" value="music" checked>
<label for="c2">Music</label>
```

**9. file**: upload files
```html
<input type="file" name="photo" accept="image/*">
<input type="file" name="docs" multiple>
```
(Form needs `enctype="multipart/form-data"` and `method="post"`.)

**10. submit**: sends the form
```html
<input type="submit" value="Register">
```

**11. reset**: clears the form to defaults
```html
<input type="reset" value="Clear">
```

**12. color**: colour picker
```html
<input type="color" name="fav" value="#ff0000">
```

**13. range**: slider
```html
<input type="range" name="volume" min="0" max="100" value="50">
```

**14. hidden**: invisible data sent with the form
```html
<input type="hidden" name="user_id" value="1234">
```

### Radio vs Checkbox

| Radio | Checkbox |
| --- | --- |
| One choice | Many choices |
| Same `name` groups them | Same name allowed, each is independent |
| Use: gender, payment method | Use: hobbies, terms agreement |

### Common Mistakes
- Missing `name` (value never reaches the server).
- Different `name`s on radio buttons (they don't group).
- Relying only on HTML validation. Always validate on the server too.
- Sensitive data in a GET form.

---

## Lesson 21: Labels `<label>`

### What is it?
Text description for a form control. Clicking the label focuses/selects its input. Vital for accessibility.

### Two ways
```html
<!-- 1. Using for + id -->
<label for="email">Email:</label>
<input type="email" id="email" name="email">

<!-- 2. Wrapping -->
<label>
    Email:
    <input type="email" name="email">
</label>
```

`for` value must exactly match the input's `id`.

### Common Mistakes
- Using plain text instead of `<label>`.
- `for` and `id` not matching.

---

## Lesson 22: Buttons `<button>`

### What is it?
A clickable button. More flexible than `<input type="submit">` because it can contain HTML (icons, images).

```html
<button type="submit">Send</button>
<button type="reset">Reset</button>
<button type="button">Click Me (does nothing by default)</button>
<button type="submit"><strong>Save</strong> 💾</button>
```

| Type | Behaviour |
| --- | --- |
| `submit` | Submits the form (default inside forms!) |
| `reset` | Resets the form |
| `button` | No default action (use with JavaScript) |

### Common Mistake
A button inside a form with no `type` acts as **submit**. Always write the type.

---

## Lesson 23: Text Area `<textarea>`

### What is it?
Multi-line text input (comments, messages).

```html
<label for="msg">Message:</label><br>
<textarea id="msg" name="message" rows="5" cols="40" placeholder="Write here..."></textarea>
```

| Attribute | Purpose |
| --- | --- |
| `rows` | Visible lines |
| `cols` | Visible width in characters |
| `maxlength` | Character limit |
| `placeholder`, `required`, `readonly`, `disabled` | Same as input |

Default text goes **between the tags**, not in `value`:
```html
<textarea name="bio">Default text here</textarea>
```

### `<input type="text">` vs `<textarea>`
Input is single-line and an empty element; textarea is multi-line and has a closing tag.

---

## Lesson 24: Dropdown `<select>`, `<option>`, `<optgroup>`

```html
<label for="city">Choose a city:</label>
<select id="city" name="city">
    <option value="">-- Select --</option>
    <option value="mumbai">Mumbai</option>
    <option value="pune" selected>Pune</option>
    <option value="delhi" disabled>Delhi</option>
</select>
```

| Tag/Attribute | Purpose |
| --- | --- |
| `<select>` | Dropdown container |
| `<option>` | One choice |
| `value` | Data sent to the server |
| `selected` | Pre-selected |
| `disabled` | Not selectable |
| `multiple` | Choose several (Ctrl/Cmd + click) |
| `size` | Visible rows |

### `<optgroup>`: group options
```html
<select name="car">
    <optgroup label="Indian">
        <option value="tata">Tata</option>
        <option value="mahindra">Mahindra</option>
    </optgroup>
    <optgroup label="Japanese">
        <option value="toyota">Toyota</option>
        <option value="honda">Honda</option>
    </optgroup>
</select>
```

---

## Lesson 25: Field Group `<fieldset>`, `<legend>`

Groups related controls with a border and a title.

```html
<form>
    <fieldset>
        <legend>Personal Information</legend>
        <label for="n">Name:</label>
        <input type="text" id="n" name="name"><br><br>
        <label for="a">Age:</label>
        <input type="number" id="a" name="age">
    </fieldset>
</form>
```
`disabled` on `<fieldset>` disables everything inside it. Great for radio groups: put `<legend>` as the question.

---

## Lesson 26: Data List `<datalist>`

An input with **suggestions** while still allowing custom typing.

```html
<label for="browser">Favourite browser:</label>
<input list="browsers" id="browser" name="browser">
<datalist id="browsers">
    <option value="Chrome">
    <option value="Firefox">
    <option value="Edge">
    <option value="Safari">
</datalist>
```
The input's `list` must match the datalist's `id`.

| `<select>` | `<datalist>` |
| --- | --- |
| Must pick from list | Can pick **or type own value** |

---

## Lesson 27: Output `<output>`

Shows the **result of a calculation** (usually with JavaScript or inline `oninput`).

```html
<form oninput="result.value = parseInt(a.value) + parseInt(b.value)">
    <input type="number" id="a" value="10"> +
    <input type="number" id="b" value="20"> =
    <output name="result" for="a b">30</output>
</form>
```

---

## Complete Registration Form (everything together)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Registration Form</title>
</head>
<body>
    <h1>Student Registration</h1>
    <form action="/register" method="post" enctype="multipart/form-data">

        <fieldset>
            <legend>Personal Details</legend>

            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required><br><br>

            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required><br><br>

            <label for="pwd">Password:</label>
            <input type="password" id="pwd" name="pwd" minlength="8" required><br><br>

            <label for="dob">Date of birth:</label>
            <input type="date" id="dob" name="dob"><br><br>

            <p>Gender:</p>
            <input type="radio" id="m" name="gender" value="male"><label for="m">Male</label>
            <input type="radio" id="f" name="gender" value="female"><label for="f">Female</label>
        </fieldset>

        <fieldset>
            <legend>Other Details</legend>

            <label for="course">Course:</label>
            <select id="course" name="course">
                <option value="">-- Select --</option>
                <option value="bsc">B.Sc.</option>
                <option value="bca">BCA</option>
            </select><br><br>

            <p>Hobbies:</p>
            <input type="checkbox" id="h1" name="hobby" value="reading"><label for="h1">Reading</label>
            <input type="checkbox" id="h2" name="hobby" value="sports"><label for="h2">Sports</label><br><br>

            <label for="photo">Photo:</label>
            <input type="file" id="photo" name="photo" accept="image/*"><br><br>

            <label for="color">Favourite colour:</label>
            <input type="color" id="color" name="color"><br><br>

            <label for="level">Skill level:</label>
            <input type="range" id="level" name="level" min="1" max="10"><br><br>

            <label for="about">About you:</label><br>
            <textarea id="about" name="about" rows="4" cols="40"></textarea>
        </fieldset>

        <input type="hidden" name="source" value="website">
        <br>
        <button type="submit">Register</button>
        <button type="reset">Clear</button>
    </form>
</body>
</html>
```

### Practice
1. Build a login form (email, password, remember-me checkbox, submit).
2. Build a feedback form with rating (range), comments (textarea), and a city dropdown.
3. Create a search box with a `<datalist>` of suggestions.

---

# MODULE E: SEMANTIC HTML

---

## Lesson 28: Semantic Tags

### What is it?
Semantic tags **describe the meaning** of the content, unlike `<div>`, which says nothing. They help SEO, accessibility, and readability.

| Tag | Purpose |
| --- | --- |
| `<header>` | Top section: logo, title, intro |
| `<nav>` | Navigation links |
| `<main>` | Main unique content (only **one** per page) |
| `<section>` | Thematic group of content, usually with a heading |
| `<article>` | Independent, reusable content (blog post, news) |
| `<aside>` | Side content (sidebar, ads, related links) |
| `<footer>` | Bottom section: copyright, contacts |
| `<details>` | Expandable/collapsible information |
| `<summary>` | Visible heading for `<details>` |
| `<figure>` | Image, diagram, or code with a caption |
| `<figcaption>` | Caption for `<figure>` |

### Page layout example
```html
<body>
    <header>
        <h1>My Blog</h1>
        <nav>
            <ul>
                <li><a href="#">Home</a></li>
                <li><a href="#">Posts</a></li>
                <li><a href="#">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section>
            <h2>Latest Posts</h2>

            <article>
                <h3>Learning HTML</h3>
                <p>HTML is the foundation of the web.</p>
            </article>

            <article>
                <h3>Learning CSS</h3>
                <p>CSS makes websites beautiful.</p>
            </article>
        </section>

        <aside>
            <h2>About the Author</h2>
            <p>I love coding.</p>
        </aside>
    </main>

    <footer>
        <p>&copy; 2026 My Blog. All rights reserved.</p>
    </footer>
</body>
```

### `<details>` and `<summary>`
Works without JavaScript.
```html
<details>
    <summary>What is HTML?</summary>
    <p>HTML is a markup language used to build web pages.</p>
</details>

<details open>
    <summary>Open by default</summary>
    <p>Hidden content shown.</p>
</details>
```

### `<figure>` and `<figcaption>`
```html
<figure>
    <img src="taj.jpg" alt="Taj Mahal at sunrise" width="400">
    <figcaption>Fig 1: The Taj Mahal, Agra.</figcaption>
</figure>
```

### `<section>` vs `<article>` vs `<div>`

| Tag | Use when |
| --- | --- |
| `<article>` | Content makes sense on its own (blog post, comment) |
| `<section>` | Grouping related content under a heading |
| `<div>` | Just a generic container for styling, no meaning |

### Common Mistakes
- Using `<div>` for everything ("div soup").
- More than one `<main>`.
- Using `<section>` without a heading.
- Using `<header>` only for the top of the page (it can also be inside an `<article>`).

---

# MODULE F: MULTIMEDIA AND EMBEDDING

---

## Lesson 29: Multimedia Tags

### `<audio>`
```html
<audio controls>
    <source src="song.mp3" type="audio/mpeg">
    <source src="song.ogg" type="audio/ogg">
    Your browser does not support audio.
</audio>
```
Attributes: `controls`, `autoplay`, `loop`, `muted`, `preload`.

### `<video>`
```html
<video width="480" controls poster="thumbnail.jpg">
    <source src="movie.mp4" type="video/mp4">
    <source src="movie.webm" type="video/webm">
    <track src="subs-en.vtt" kind="subtitles" srclang="en" label="English" default>
    Your browser does not support video.
</video>
```
Attributes: `controls`, `autoplay` (needs `muted` in most browsers), `loop`, `muted`, `poster`, `width`, `height`.

### `<source>`
Gives multiple file options; the browser picks the first it supports. Used inside `<audio>`, `<video>`, `<picture>`.

### `<track>`
Adds subtitles, captions, or descriptions to video/audio using `.vtt` files.

| `kind` | Meaning |
| --- | --- |
| `subtitles` | Translation of dialogue |
| `captions` | Dialogue + sound effects |
| `descriptions` | Describes the video for blind users |

### `<iframe>`
Embeds another web page inside yours (YouTube, Google Maps).
```html
<iframe src="https://www.example.com" width="600" height="400" title="Example site"></iframe>
```
Always add a `title`. Many sites block embedding.

YouTube-style embed:
```html
<iframe width="560" height="315"
        src="https://www.youtube.com/embed/VIDEO_ID"
        title="Video player" allowfullscreen></iframe>
```

### `<embed>`
Embeds external content such as a PDF or plugin.
```html
<embed src="notes.pdf" type="application/pdf" width="600" height="500">
```

### `<object>`
Embeds external resources, with a built-in fallback.
```html
<object data="notes.pdf" type="application/pdf" width="600" height="500">
    <p>PDF can't be shown. <a href="notes.pdf">Download it</a>.</p>
</object>
```

### `<picture>`: responsive images
Show different images for different screens or formats.
```html
<picture>
    <source media="(min-width: 800px)" srcset="large.jpg">
    <source media="(min-width: 400px)" srcset="medium.jpg">
    <img src="small.jpg" alt="Mountain view">
</picture>
```
The `<img>` inside is **required** (fallback).

### `<iframe>` vs `<embed>` vs `<object>`

| Tag | Best for |
| --- | --- |
| `<iframe>` | Whole web pages, videos, maps |
| `<embed>` | Simple embedding, no fallback |
| `<object>` | Embedding with fallback content |

### Common Mistakes
- Autoplaying video with sound (browsers block it).
- Providing only one video format.
- Missing `controls`, so the user can't play it.
- Embedding untrusted sites in `<iframe>` (use `sandbox`).

---

# MODULE G: ADVANCED HTML

---

## Lesson 30: Advanced Topics

### 1. HTML Entities
Special codes for reserved characters. Format: `&name;` or `&#number;`.

| Character | Entity | Why needed |
| --- | --- | --- |
| `<` | `&lt;` | Otherwise it starts a tag |
| `>` | `&gt;` | |
| `&` | `&amp;` | Starts an entity |
| `"` | `&quot;` | Inside attributes |
| non-breaking space | `&nbsp;` | Space that doesn't collapse |

```html
<p>Use &lt;p&gt; to create a paragraph.</p>
<p>Tom &amp; Jerry</p>
<p>Hello&nbsp;&nbsp;&nbsp;World</p>
```

### 2. HTML Symbols
| Symbol | Code |
| --- | --- |
| © | `&copy;` |
| ® | `&reg;` |
| ™ | `&trade;` |
| € | `&euro;` |
| ₹ | `&#8377;` |
| ♥ | `&hearts;` |
| → | `&rarr;` |
| ° | `&deg;` |

```html
<p>&copy; 2026 Company&trade; | Price: &#8377;499 | Love &hearts;</p>
```

### 3. Character Encoding
Tells the browser how to convert bytes into characters. Always use **UTF-8**.
```html
<meta charset="UTF-8">
```
Without it, text like "नमस्ते" or "é" may appear garbled.

### 4. HTML Metadata
Data **about** the page, placed inside `<head>`.

| Tag | Purpose |
| --- | --- |
| `<title>` | Tab title and search result title |
| `<meta>` | Page information |
| `<link>` | Link to CSS, favicon |
| `<style>` | Internal CSS |
| `<script>` | JavaScript |
| `<base>` | Base URL for relative links |

### 5. Meta Tags
```html
<meta charset="UTF-8">
<meta name="description" content="Learn HTML step by step.">
<meta name="keywords" content="HTML, CSS, tutorial">
<meta name="author" content="Rahul Sharma">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta http-equiv="refresh" content="30">  <!-- reload every 30 sec -->
```
The `description` appears in Google results. The `viewport` tag is essential for mobile.

### 6. Favicon
The small icon in the browser tab.
```html
<link rel="icon" type="image/png" href="favicon.png">
```

### 7. Responsive HTML
Making pages work on phones, tablets, and desktops.
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<img src="photo.jpg" alt="Photo" style="max-width: 100%; height: auto;">
```
Also: `<picture>`, `srcset`, and (later) CSS media queries, Flexbox, Grid.

`srcset` example:
```html
<img src="small.jpg"
     srcset="small.jpg 480w, medium.jpg 800w, large.jpg 1200w"
     sizes="(max-width: 600px) 480px, 800px"
     alt="Responsive image">
```

### 8. Accessibility (a11y)
Making sites usable by everyone, including people using screen readers or keyboards.
- Use semantic tags.
- Always add `alt` to images.
- Use `<label>` for inputs.
- Keep headings in order.
- Ensure good colour contrast.
- Make everything usable by keyboard (Tab, Enter).

### 9. ARIA Attributes
Extra info for assistive technology when native HTML isn't enough.
```html
<button aria-label="Close menu">✖</button>
<div role="alert">Form submitted successfully!</div>
<nav aria-label="Main navigation">...</nav>
<button aria-expanded="false" aria-controls="menu">Menu</button>
<input type="text" aria-required="true" aria-describedby="hint">
<span id="hint">Enter your full name</span>
```
> First rule of ARIA: **don't use ARIA if a native HTML element already does the job.** `<button>` is better than `<div role="button">`.

### 10. Global Attributes
Work on **any** HTML element.

| Attribute | Purpose |
| --- | --- |
| `id`, `class`, `style`, `title` | Already learned |
| `lang` | Language of element |
| `hidden` | Hides the element |
| `tabindex` | Keyboard focus order |
| `contenteditable="true"` | Makes it editable |
| `draggable="true"` | Makes it draggable |
| `spellcheck` | Spell checking |
| `dir="rtl"` | Text direction |
| `accesskey` | Keyboard shortcut |

```html
<p contenteditable="true">Click and edit me!</p>
<p hidden>You can't see me.</p>
<p lang="fr">Bonjour le monde</p>
```

### 11. Data Attributes
Store custom data on elements. Names start with `data-`. Used by JavaScript.
```html
<button data-user-id="42" data-role="admin">Delete user</button>
```
JavaScript:
```js
const btn = document.querySelector("button");
console.log(btn.dataset.userId);  // "42"
console.log(btn.dataset.role);    // "admin"
```

### 12. SVG (Scalable Vector Graphics)
Vector images that never blur when zoomed. Written in XML inside HTML.
```html
<svg width="200" height="200" viewBox="0 0 200 200">
    <circle cx="100" cy="100" r="80" fill="orange" stroke="black" stroke-width="3" />
    <rect x="60" y="60" width="80" height="80" fill="white" />
    <text x="100" y="105" text-anchor="middle">SVG</text>
</svg>
```

### 13. Canvas
Draws pixel graphics with JavaScript (games, charts, animations).
```html
<canvas id="myCanvas" width="300" height="150" style="border:1px solid black;"></canvas>
<script>
    const canvas = document.getElementById("myCanvas");
    const ctx = canvas.getContext("2d");
    ctx.fillStyle = "tomato";
    ctx.fillRect(20, 20, 150, 80);
</script>
```

| SVG | Canvas |
| --- | --- |
| Vector, elements in the DOM | Pixels, one drawing surface |
| Sharp at any size | Can blur when scaled |
| Good for icons, logos | Good for games, heavy animation |

### 14. HTML APIs
Built-in browser features accessed through JavaScript.

| API | Purpose |
| --- | --- |
| Geolocation | User's location (with permission) |
| Web Storage | `localStorage`, `sessionStorage` |
| Drag and Drop | Drag elements |
| Fetch | Get data from servers |
| Canvas | Drawing |
| Web Workers | Background tasks |
| History | Control browser history |

```html
<button onclick="getLocation()">Where am I?</button>
<p id="out"></p>
<script>
function getLocation() {
    navigator.geolocation.getCurrentPosition(pos => {
        document.getElementById("out").textContent =
            "Lat: " + pos.coords.latitude + ", Lon: " + pos.coords.longitude;
    });
}
localStorage.setItem("theme", "dark");
console.log(localStorage.getItem("theme"));
</script>
```

### 15. SEO Basics
Helping search engines understand and rank your page.
- Unique, descriptive `<title>` (about 50-60 characters).
- A good `<meta name="description">` (about 150-160 characters).
- One `<h1>`, with logical heading order.
- Semantic tags.
- `alt` text on images.
- Descriptive link text.
- Mobile-friendly (viewport tag).
- Clean, readable URLs and fast loading.

```html
<head>
    <title>Learn HTML for Beginners | My Tutorials</title>
    <meta name="description" content="A free step-by-step HTML course with examples and practice questions.">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
```

---

# MODULE H: WHAT COMES AFTER HTML

---

## Lesson 31: Roadmap

| Step | Topic | What you will do |
| --- | --- | --- |
| 1 | **CSS Fundamentals** | Colours, fonts, spacing, backgrounds |
| 2 | **Selectors** | Target elements: `p`, `.class`, `#id`, `div > p` |
| 3 | **Box Model** | content, padding, border, margin |
| 4 | **Flexbox** | One-dimensional layouts (navbars, cards) |
| 5 | **Grid** | Two-dimensional page layouts |
| 6 | **Responsive Design** | Media queries, mobile-first |
| 7 | **JavaScript Fundamentals** | Variables, functions, loops, conditions |
| 8 | **DOM Manipulation** | Change HTML/CSS with JavaScript |
| 9 | **Events** | Respond to clicks, typing, scrolling |

A taste of what's coming:
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        .card { padding: 20px; border: 2px solid teal; border-radius: 10px; width: 250px; }
    </style>
</head>
<body>
    <div class="card">
        <h2 id="title">Hello</h2>
        <button id="btn">Click me</button>
    </div>
    <script>
        document.getElementById("btn").addEventListener("click", () => {
            document.getElementById("title").textContent = "You clicked!";
        });
    </script>
</body>
</html>
```
HTML gives the structure, CSS the style, and JavaScript the behaviour.

---

## Final Capstone Projects
1. **Personal portfolio**: semantic tags, image, links, list of skills, contact form.
2. **Resume page**: headings, table of education, lists of skills.
3. **Product page**: image, description list for specs, table for pricing, video.
4. **Blog page**: `<article>`, `<aside>`, `<figure>`, `<details>` FAQ.

---

## Quick Reference Cheat Sheet

| Need | Use |
| --- | --- |
| Heading | `<h1>`-`<h6>` |
| Paragraph / line break / divider | `<p>` / `<br>` / `<hr>` |
| Important / emphasised text | `<strong>` / `<em>` |
| Link / image | `<a href>` / `<img src alt>` |
| Numbered / bullet list | `<ol>` / `<ul>` |
| Table | `<table><tr><th><td>` |
| Form input | `<input type name>` |
| Page regions | `<header> <nav> <main> <section> <footer>` |
| Video / audio | `<video controls>` / `<audio controls>` |

**Happy coding!** 🚀
