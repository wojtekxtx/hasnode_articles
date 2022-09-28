## SASS/LESS vs pure CSS

# Preface
After first hearing about `SASS/LESS` I thought that it may be sth of any use. I was wrong. Using both `SASS` / `LESS` you can do exactly the same things when using plain `CSS`. Yes, you read it correctly: both `SASS`/`LESS` are just **total replacement** of plain `CSS`.

You write files with extension `scss` instead of `css`, but, at compile time, you get **plain `css` file**. So, what are the reasons to use it, while you still get plain standard `CSS` as a result? To be honest, **there are none**!

# SASS
## Extension
`SASS` files are the ones with extension `.scss`.

## What are new things SASS implements?

Bear in mind that whats below is only extract from all new-old things `SASS` introduces. For full list, please visit [Sass: Sass basics](https://sass-lang.com/guide) website.
### Variables
This code:
```scss
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

get compiled to:
```css
body {
  font: 100% Helvetica, sans-serif;
  color: #333;
}
```

### Nesting
This code:
```scss
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```
becomes:
```css
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav li {
  display: inline-block;
}
nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```

### Operators
This code:
```scss
@use "sass:math";

.container {
  display: flex;
}

article[role="main"] {
  width: math.div(600px, 960px) * 100%;
}

aside[role="complementary"] {
  width: math.div(300px, 960px) * 100%;
  margin-left: auto;
}
```
becomes this:
```css
.container {
  display: flex;
}

article[role="main"] {
  width: 62.5%;
}

aside[role="complementary"] {
  width: 31.25%;
  margin-left: auto;
}
```
