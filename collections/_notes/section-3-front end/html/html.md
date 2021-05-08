---
layout: post
title: HTML
permalink: /:collection/html/
---

- [HTML Color Picker](https://www.w3schools.com/colors/colors_picker.asp){:target="_blank"}
- [CSS properties](https://www.w3schools.com/cssref/default.asp){:target="_blank"}

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- meta -->
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- link -->
    <link rel="stylesheet" href="style.css">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
    <!-- scripts -->
    <script src="script.js"></script>
</head>
<body>

</body>
</html>
```

```html
<div>
    <a href="http://google.com" target="_blank">
        <button>Google Search</button>
    </a>
</div>
```

```html
&nbsp;
<!-- non-breaking space: entity in HTML -->
```

## Form
```html
<form action="/process" method="post">
    <pre>
        username: <input type="text" name="username" id="username" placeholder="name"><br>
        password: <input type="password" name="password" id="password" required><br>
        email: <input type="email" name="email" id="email"><br>
        file: <input type="file" name="file" id="file"><br>
        telephone: <input type="tel" name="telephone" id="telephone"><br>
        <input type="submit" value="Submit">
    </pre>
</form>
```

## Table
```html
<table>
    <thead>
        <th>FName</th>
        <th>LName</th>
    </thead>
    <tbody>
        <tr>
            <td>Arpit</td>
            <td>Tripathi</td>
        </tr>
        <tr>
            <td>Second</td>
            <td>name</td>
        </tr>
    </tbody>
</table>
```