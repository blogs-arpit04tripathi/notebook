---
layout: post
title: Bootstrap
permalink: /:collection/bootstrap/
---

- TOC
{:toc}

<hr><br>

# External Links
- [Navbar CSS Tutorial: 3 Ways to Create a Navigation Bar with Flexbox](https://www.youtube.com/watch?v=PwWHL3RyQgk){:target="_blank"}
- [Complete Portfolio Website with Bootstrap - HTML/CSS](https://www.youtube.com/watch?v=dgKSqz3it50){:target="_blank"}
- [Build A Complete HTML & CSS Website with Bootstrap 4](https://www.youtube.com/watch?v=V_lAhqLXT9A){:target="_blank"}

# Checklist Topics
Bootstrap Scaffolding
* What Is Bootstrap?
* Bootstrap File Structure
* Basic HTML Template
* Global Styles
* Default Grid System
* Fluid Grid System
* Bootstrap CSS
* Typography
* Code
* Tables
* Forms
* Buttons
* Images
* Icons

# References
- [Bootstrap Website](https://getbootstrap.com/){:target="_blank"}
- [W3Schools](https://www.w3schools.com/bootstrap4/default.asp){:target="_blank"}

# Introduction

```
CDN - content delivery network
bootstrap.js and css
jquery
popper.js
bootstrap starter template

div class="container" --> page body
div class="display-1" --> bigger than h1(Head)
p class="lead" --> Lead paragraph (bigger)
div blockquote-footer or blockquote-reverse
div bg-primary
text-primary

img-fluid --> fit to container width
rounded-0
circleimg-thumbnailfloat-rightmx-auto --> centre block
figure
figure-imgrounded-circle

Grid System
responsive 12 column (col-sm-12)
Flex based
Structure --> containers, rows and columns
.container --> 15px fix padding, 3px for container and rows
col-sm-12
offset-sm-2
pb-3 --> padding bottom
row-no-gutters --> remove spaces between col
d-felx --> vertical/horizontal align
```

* Position
	- fixed-top
	* fixed-bottom
	* sticky-top
* Display
	- d-sm-none
	- inline 
	- block
	- inline-block
	- table
	- table-row
	- table-cell
* Flex
	- inline-flex
	- flex --> default block
	- flex-sm-row-reverse
	- flex-sm-col-reverse
	- rounded circle
	- align-content-strech
* sizes
	- sm(576px)
	- md(768px)
	- lg(992px)
	- xl(1200px)
* navs, tabs, pills, navbar
* nav --> nav-item, nav-links, nav-active, nav-disabled, nav-pills, nav-tabs
* navbar-text, navbar-brand
* jumbotron, jumbotron-fluid
* table-responsive, table-sm
* card-group, card-deck, card-columns
* media, media-body
* form-group, form-row, form-group-append
* d-flex align-self-center

```html
<a href="http://www.google.com" onclick="if(!(confirm('Are you sure, you want to exit?'))) return false">Google</a>
```
<a href="http://www.google.com" onclick="if(!(confirm('Are you sure, you want to exit?'))) return false">Google</a>

# SASS (Syntactically Awesome StyleSheets)
* Sass is an extension of css and allows variables, nested rules, mixins, inline imports etc. 
* Sass includes two syntax options:
    - SCSS (Sassy CSS): .scss file.
    - Indented (simply called 'Sass'): .sass file, indentation rather than brackets;
    - Files can be converted from one syntax to the other using the sass-convert command.

```
sass-convert style.sass style.scss
sass-convert style.scss style.sass
```

```ts
// Variables
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;
body {
  font: 100% $font-stack;
  color: $primary-color;
}
```
```ts
// Nesting
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
   }
   li { display: inline-block; }
}
```
```ts
// Mixins
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}
.box { @include border-radius(10px); }
```
Operators - few built-in functions to help manipulate numbers like percentage(), floor() and round()