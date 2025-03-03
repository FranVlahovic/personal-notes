## Media Queries

### Media Query Syntax

```CSS
body {
    margin: 24px;
}

@media (max-width: 600px){
    body {
        margin: 8px;
    }
}
```

> On all screens below or equal to `600px` the `margin` will be `8px`, and on all screens above `600px` it will be `24px`.

#### Unlimited number of Media Queries Available

```CSS
body {
  background: purple;
}
​
@media (max-width: 900px) {
  body {
    background: green;
  }
}
​
@media (max-width: 800px) {
  body {
    background: brown;
  }
}
​
@media (max-width: 700px) {
  body {
    background: pink;
  }
}
​
@media (max-width: 600px) {
  body {
    background: blue;
  }
}
​
@media (max-width: 500px) {
  body {
    background: orange;
  }
}
```

> We can create an unlimited number of media queries in a single document.

#### Unlimited style definitions inside Media Query

```css
body {
  margin: 0;
  height: 100vh;
  display: flex;
  flex-direction: column;
}
header {
  background: dodgerblue;
  padding: 32px 64px;
  font-size: 32px;
  color: white;
}
main {
  display: flex;
  flex: 1;
}
aside {
  width: 300px;
  flex-shrink: 0;
  background: palevioletred;
  color: white;
}
li {
  font-size: 24px;
  list-style-type: none;
}

section {
  padding: 16px;
  margin: 16px;
  font-size: 24px;
  background: blanchedalmond;
}

footer {
  height: 96px;
  background: darkslateblue;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
}

@media (max-width: 800px) {
  main {
    flex-direction: column;
  }
  header {
    text-align: center;
    padding: 24px;
  }
  aside {
    width: auto;
  }
  ul {
    display: flex;
    gap: 16px;
    justify-content: center;
    padding: 0;
  }
}
```

> We can create an unlimited number of style definitions inside media query.

### Combining multiple types or features

```css
@media (min-width: 30em) and (orientation: landscape) {
  /* */
}
```

> Example combines two media features to restrict styles to `landscape` oriented devices with `width` of at least `30em`

### Tips

#### Other Queries

- A `max-width` query will apply on any screen up to the defined `max-width`

- A `min-width` will apply to any screen resolution above or equal to the given value.

- Use `min-width` first if starting _`mobile first`_.

#### Limit Media Queries

- It's best to minimize media query usage and rely more on the natural flexibility of our layouts.

- [Above example shows it the best](#unlimited-style-definitions-inside-media-query)

#### Common Breakpoints

- Takeaway is that it doesn't really matter exactly where you set your breakpoints, just do what makes sense for your project.

- When things get weird, apply a breakpoint and fix it (resize and see).

- However there are some commonly used breakpoints:
  - `320px` - `480px` > **Mobile**
  - `481px` - `768px` > **Tablets**
  - `769px` - `1024px` > **Small Screens / Laptops**
  - `1025px` - `1200px` > **Desktop**
  - +`1201px` > **Extra Large Screens / TV**

#### Print Styles

```css
@media print {
  /* print styles go here */
}
```

- We can use media print to change some colors (i.e. make things black/white), and add `display: none` to hide elements that are useless in a printed environment (buttons, nav links, etc).
