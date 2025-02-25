## Natural Responsiveness

### Avoid fixed width and height

- Replace `width` or `height` with `max-width` or `min-height` (`min-width` and `max-height`)

#### Static Width

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>
        .box {
            background: sandybrown;
            border: 8px solid saddlebrown;
            margin: 0 auto;
            padding: 32px;
            font-size: 32px;
            /* width: 600px; */
            max-width: 600px;
        }
    </style>

</head>

<body>
    <div class="box"> let's overflow this screen right nowwwwwwwwwwwwww</div>
</body>

</html>
```

> When a `max-width` is defined, the element will not exceed that `width` but will shrink if the screen is too small to accommodate it.

#### Static Height

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>
        .box {
            background: hotpink;
            padding: 32px;
            font-size: 32px;
            margin: 0 auto;
            max-width: 600px;
            /* height: 300px; */
            min-height: 300px;
        }
    </style>

</head>

<body>
    <div>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsam modi ratione expedita delectus dolorum iusto distinctio, adipisci dolore nulla provident eius aperiam dignissimos accusantium cum recusandae aut tempora! Reprehenderit, esse.
    </div>
</body>

</html>
```

> When a `min-height` is defined, the element will not overflow but will grow when the text gets cramped.

### Avoid Heights Altogether

- Prefer using `margin` and `padding` to increase space around your content, it will keep elements flexible no matter what the content inside does.

### Appropriate fixed widths

- Smaller the div, more acceptable to make them width fixed.

- Sidebar, Icons etc. probably wont benefit from using `max-width` since probably we don't want it to shrink.

### Use Flex & Grid

- Flexbox was created to enable the creation of flexible layouts.

- Using `flex` and `grid` doesn’t necessarily guarantee perfect responsiveness, but they are really helpful tools.

### Minmax

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>

        body {
        margin: 40px;
        }

        .wrapper {
            display: grid;
            grid-gap: 10px;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr) ) ;
            background-color: #fff;
            color: #444;
        }

        .box {
            background-color: #444;
            color: #fff;
            border-radius: 5px;
            padding: 20px;
            font-size: 150%;
        }
    </style>

</head>

<body>
    <div>
        <div class="box a">A</div>
        <div class="box b">B</div>
        <div class="box c">C</div>
        <div class="box d">D</div>
        <div class="box e">E</div>
        <div class="box f">F</div>
        <div class="box g">G</div>
        <div class="box h">H</div>
        <div class="box i">I</div>
    </div>
</body>

</html>
```
