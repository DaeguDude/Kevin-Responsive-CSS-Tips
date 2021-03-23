# All the tips from the course

### Use percentages

Use the percentage, so you get the responsiveness back.

Child's width percentage is based on the parents element's width

### Avoid heights

Do not put height on element, because when the content is getting longer it will over flow if it has fixed height.

## Get familiar with relative units

[CSS em and rem explained by Kevin Powell](https://www.youtube.com/watch?v=_-aDOAMmDHI&ab_channel=KevinPowell)

`em`, `rem`

Using relative unit is good, because different devices use different px.

Mobile uses 70%, table uses 80%, so it is always responsive

### vh, vw, vmin, vmax

You can make layout responsive with `vh` and `vw`. `vh` and `vw` are good because it's understandable and responsive. However, normally you would use media query.

### Don't set font-sizes using `em`

[Why you shouldn't set font-sizes using `em`](https://www.youtube.com/watch?v=pautqDqa54I&ab_channel=KevinPowell)

### Adding in a max-width

Most of the time we don't want to set min-height, or width it is like going against the responsive design. However, there's no set rule for this, but generally speaking, No.

```css
.container {
  width: 80%;
  max-width: 750px;
}
```

This will make sure that `container` is always on 80% of its parent, and it can never be bigger than 750px.

**Additional tip: normally width is `%` and max-width is `px`**

```css
.container {
  width: 80%;
  max-width: 750px;
  margin: 0 auto;
}
```

You can use this `container` class to limit the width of content. And it is reusable.

### Flexbox

- Flex items will always fit as small as possible
- `width: 100%` on flex items will make each item in flex container in equal sizes
- If you want to create a gap between 2 flex items, use `justify-content: space-between` instead of margin

### Adding space in between columns

.col + .col

### Reducing the amount of HTML needed

Instead of making separate html element for styling, you can have 2 classes in one element.

```html
// Before
<div class="container">
  <div class="row">
    <div class="col"></div>
    <div class="col"></div>
    <div class="col"></div>
  </div>
</div>

// After
<div class="container row">
  <div class="col"></div>
  <div class="col"></div>
</div>
```

### Ensuring the image is responsive

Since `align-self: stretch` is the default value on flex-items, it will always stretch vertically.

To prevent that, you can change the value to `align-self: flex-start`, so it doesn't stretch all the way down and be responsive.

Otherwise, you can add additional `div` wrapper.

```html
<!-- img is a flex item -->
<img class="hero__img" src="./img/main-img" alt="laptop img" />

<!-- div is a flex item, so div stretches not img -->
<div>
  <img class="hero__img" src="./img/main-img" alt="laptop img" />
</div>
```

### Reducing CSS styling

If there are more than two sections that have a same styling applied, you can group them into one rather than having a separate styling

```css
// BEFORE
.hero__text {
  width: 62%;
}

.hero__img {
  width: 32%;
}

.main__text {
  width: 62%;
}

.main__sidebar {
  width: 32%;
}

// AFTER
.hero__text,
.main__text {
  width: 62%;
}

.hero__img,
.main__sidebar {
  width: 32%;
}
```

### HTML semantic Approach

Use meaningful HTML element

```html
<!-- Before -->
<div class="hero">
  ...
  <div>
    <!-- After -->
    <header class="hero">
      ...
      <header></header>
    </header>
  </div>
</div>
```

```html
<!-- Before -->
<main class="main">
	<div class="info__test"></div>
	<div class="sidebar"></div>
</main>
<!-- After -->
<main class="main">
	<section class="info__test"></div>
	<aside class="sidebar"></div>
</main>
```

Having class name as same to tag name is perfectly fine. Selecting element by class is generally better.

### Media query

You can use Media Query for modifying your site or app depending on various device types.

Refer to the references for the detailed explanation.

[Media Query](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)

### Breakpoint

Breakpoint: The point that you want to start apply the changes. E.g. `max-width: 600px`, You want to apply the change when it is less than 600px.

**How to decide what breakpoints to use?**

[The 100% correct way to do CSS breakpoints](https://www.freecodecamp.org/news/the-100-correct-way-to-do-css-breakpoints-88d6a5ba1862/)

However, you could take a look at your website and by adjusting the screen sizes, when thing start to break, then you can choose that point as a break point .

**Do not keep many breakpoints**

It is harder to maintain CSS if you have many media queries.

### Do not let text stretch all the way across the screen

If text stretches all the way across the screen, your eyes get tired of reading it.

Manage it with `max-width` or use media queries.

### min-height

`min-height` is useful. Giving it fixed height is bad, but giving it flexible height is okay.

### Meta viewport tag

[Meta viewport tag](https://www.w3schools.com/css/css_rwd_viewport.asp)

Viewport is user's visible area of a webpage.

### **Write mobile-first CSS**

Desktop-first approach is the culprit. Since mobile version has less things to design, you can start simply and expand on to the complicated desktop version. Even if you only have a desktop layout to base things off of, writing mobile-first CSS tends to be the easier way.

### You don't always need to styling in general tag

If things aren't being used repeatedly, it's better to keep the styling in class selector.

```css
/* what I did */
li {
  list-style-type: none;
}

a {
  text-decoration: none;
}

ul {
  padding-inline-start: 0;
  margin: 0;
  padding: 0;
}

/* what he did */
.nav__list {
  margin: 0;
  padding: 0;
  list-style: none;
}

.nav__link {
  color: #fff;
  text-transform: uppercase;
  text-decoration: none;
}
```

### Margin & Padding `top`, `bottom` does not work on inline items

```css
// Does not work!!
a {
  margin-top: 3em;
  margin-bottom: 3em;
  padding-top: 3em;
  padding-bottom: 3em;
}

// Does work!
a {
  margin-left: 3em;
  margin-right: 3em;
  padding-left: 3em;
  padding-right: 3em;
}
```

### Shared class but needs different styling

If you need specific styling on element that has shared class names, give it another class name.

```html
<ul class="nav__list nav__list--secondary">
  <li class="nav__item"><a href="#" class="nav__link">Sign In</a></li>
  <li class="nav__item">
    <a href="#" class="nav__link nav__link--button">Sign up</a>
  </li>
</ul>
```

```css
.nav__link {
  color: #fff;
  text-decoration: none;
  text-transform: uppercase;
}

.nav__link--button {
  padding: 0.5em 0.75em;
  background: #fff;
  border-radius: 100px;
  color: #136c72;
}
```

### Behavior of Position

`position: absolute` will remove things out of document flow.

## General Tips

- Websites are responsive before we write any css, it's our fault if layout is not responsive
- Learning Flexbox

  As you learn into more complex situations, you can learn more about Flexbox. No need to master it when start using it

- Don't rush things, mastering anything isn't about learning as much as you possibly can

  practice what you've learned until you feel comfortable with it. Only then can you move to learning new skills
