## Responsive Images

### Basics

- Don't define both `width` and `height`.
- Image will retain its aspect ratio correctly if an image is given flexible `width`, and `height` is set to `auto`.

### Background-size, background-position, object fit

#### Background Size & Position Example

- `background-position` and `background-size` are properties that work on elements with `background-image`.
- `background-position: center` makes sure the image is always centered in its container.
- `background-size: cover` will resize image so that is always completely filling its container (little cropping).

```css
body {
  height: 100vh;
  margin: 0;
  background-image: url(https://images.unsplash.com/photo-1578241561880-0a1d5db3cb8a?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2070&q=80);
  background-size: cover;
  background-position: center;
}
```

#### Object Fit Example

- `Object fit` work similar but is meant for `<img>`.
- Specify `width` and `height` for your images and then tell an image how it's supposed to fit itself to those dimensions.

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>
        img {
            height: 300px;
            width: 100%;
            object-fit: cover;
        }
    </style>

</head>

<body>
   <img src="https://images.unsplash.com/photo-1578241561880-0a1d5db3cb8a?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2070&q=80" alt="">
</body>

</html>
```

### Picture tag

#### Art Direction Switcher

```HTML
<picture>

  <source media="(max-width: 799px)" srcset="elva-480w-close-portrait.jpg">
  <source media="(min-width: 800px)" srcset="elva-800w.jpg"/>
  <img src="elva-800w.jpg" alt="Chris standing up holding his daughter Elva"/>

</picture>
```

- If viewport width is 799px wide or less the first `<source>` will be displayed.
- If viewport width is 800 or more, it will be the second one.
- An `<img>` element needs to be provided, this acts as a default case that will apply when none of the media conditions return true.

#### Resolution Switching

```HTML
<img
  srcset="elva-fairy-480w.jpg 480w, elva-fairy-800w.jpg 800w"
  sizes="(max-width: 600px) 480px,
         800px"
  src="elva-fairy-800w.jpg"
  alt="Elva dressed as a fairy" />
```

- `srcset` => attribute specifies a list of image sources and their widths.

- `sizes` => attribute defines a set of media conditions and indicates what image size to use for each condition.\
  `(max-width: 600px) 480px` => if viewport is `600px` wide or less, use `480px` image, for all other cases use `800px` image.
- `src="elva-fairy-800w.jpg"` => specifies the url of the default image to be displayed if browser doesn't support the `srcset` attribute.

#### ↩️ [Odin Project Main](/work/notes/odin_project/the-odin-project.md)
