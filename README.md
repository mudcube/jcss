# JCSS
#### Javascript in harmony with Stylus/SASS/SCSS/CSS

*This is currently vaporware... Feel free to pitch in thoughts :)*

* .jstyl for Javascript in Stylus
* .jsass for Javascript in SASS
* .jscss for Javascript in SCSS
* .jcss for Javascript in CSS

--------------------------------------------------

## .jstyl example #1

```js
// This is Stylus; it's the default context in a .jstyl:
background = black

// This is Javascript; dollar-bracket enters the Javascript (NodeJS) context:
${
    import 'tinycolor' // You can perform ES6 imports.
    var color1 = `${'r'}${'e'}${'d'}` // You can use template strings or any other ES6 feature.
    var color2 = 'hsla(180, 100%, 42%, 1.0)'
    var foreground = tinycolor.mostReadable(background, [ color1, color2 ]) // Stylus variables are available to Javascript.
    return `
        // You can return Stylus which is written inline.
        body
            border: 7px solid foreground
    `
}

// This is Stylus again:
body
    background: background // You can reference Stylus variables.
    color: foreground // Javascript variables can be accessed in the same way.
```

### .styl output
```js
background = black
foreground = red

body 
	border: 7px solid foreground
	background: background
	color: foreground
```

### .css output
```js
body {
	border: 7px solid red;
	background: black;
	color: red;
}
```

--------------------------------------------------

## .jstyl example #2

```js
${
	prefs = JSON.parse(require('fs').readFileSync('prefs.json', 'utf8'))
}

body
    background: prefs.background
    color: prefs.color
```
