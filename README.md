### Slide Attributes

Attributes to the slide `<section>` elements are written in the [Front-matter](https://jekyllrb.com/docs/frontmatter/):

```markdown
---
layout: slide
title: Background Transitions
data:
  transition: linear
  background: 'red'
  background-transition: slide
---
```

### Fragments

Markdown fragments must be covered in a HTML block element using the attribute `markdown="1"`:

```html
<div markdown="1" class="fragment">
# Markdown Heading
 
Fragment 1 text
</div>
<div markdown="1" class="fragment">
Fragment 2 text
</div>
```

Fragments can be nested.

### Vertical Slides

For vertical scrolling you need to leave the `title:` blank. All content on vertical slides must be wrapped in HTML `<section>` blocks:

```html
---
layout: slide
title:
---

<section markdown="1">
# Top Slide
</section>
<section markdown="1">
# Bottom Slide
</section>
```

### Configuration

All options for the reveal.js presentation are available in the `_config.yml` as sub keys of `reveal:`.

The configuration will be built in the `<script />` block at the bottom of the `index.html` presentation file.

### Code Syntax Highlighting

To insert a highlighted code block the code can be surrounded with the [Liquid](https://shopify.github.io/liquid/) tag `highlight`:

```liquid
{% highlight coffee %}
# Objects:
math =
  root:   Math.sqrt
  square: square
  cube:   (x) -> x * square x
{% endhighlight %}
```

Insted of Rouge for highlighting the code, reveal-jekyll uses the [Reveal.js's preferred method](https://revealjs.com/code/) via [highlight.js](https://highlightjs.org/). To use all options it is possible to surround the code with HTML nodes `pre` and `code` using the class `language-*` adding optional `data` tags:

```html
<pre><code class="language-coffee" data-trim data-noescape data-line-numbers="1|3-5">
# Objects:
math =
  root:   Math.sqrt
  square: square
  cube:   (x) -> x * square x
</code></pre>
```

### Slide Numbers

You can show slide numbers by selecting a format in the `_config.yml` file:

```coffee
slideNumber:
  # Slide number formatting can be configured using these variables:
  #  "h.v":  horizontal . vertical slide number (default)
  #  "h/v":  horizontal / vertical slide number
  #    "c":  flattened slide number
  #  "c/t":  flattened slide number / total slides
  # "none":  don't show slide numbers
  format:    "c/t"
```

### Speaker Notes

reveal.js comes with a speaker notes plug-in which can be used to present per-slide notes in a separate browser window. The notes window also gives you a preview of the next upcoming slide so it may be helpful even if you haven't written any notes. Press the 's' key on your keyboard to open the notes window.

Notes are defined by appending an `<aside>` element to a slide as seen below. You can add the `markdown="1"` attribute to the aside element if you prefer writing notes using Markdown:

```html
---
layout: slide
---

Slide text...

<aside class="notes" markdown="1">
Oh hey, these are some notes. They'll be hidden in your presentation, but you can see them if you open the speaker notes window (hit 's' on your keyboard).
</aside>
```

When used locally, this feature requires that reveal.js [runs from a local web server](https://github.com/hakimel/reveal.js#full-setup).

---

## Runtime Dependencies for Development

### Running Jekyll on Your Server

- Commander: Command-line interface constructor (Ruby)
- Colorator: Colorizes command line output (Ruby)
- Classifier: Generating related posts (Ruby)
- Directory Watcher: Auto-regeneration of sites (Ruby)
- Kramdown: Default Markdown engine (Ruby)
- Liquid: Templating system (Ruby)
- Pygments.rb: Syntax highlighting (Ruby/Python)
- Safe YAML: YAML Parser built for security (Ruby)
- Sass: CSS extension language (Ruby)
- CoffeeScript: compiling to JavaScript (Ruby)

### Running reveal.js

Reveal.js doesn't _rely_ on any third party scripts to work but a few optional libraries are included by default. These libraries are loaded as dependencies in the order they appear, for example:

```javascript
Reveal.initialize({
  dependencies: [
    // Cross-browser shim that fully implements classList - //github.com/eligrey/classList.js/
    { src: 'lib/js/classList.js', condition: function() { return !document.body.classList; } },

    // Zoom in and out with Alt+click
    { src: 'plugin/zoom-js/zoom.js', async: true },

    // Speaker notes
    { src: 'plugin/notes/notes.js', async: true },

    // Remote control your reveal.js presentation using a touch device
    { src: 'plugin/remotes/remotes.js', async: true },

    // MathJax
    { src: 'plugin/math/math.js', async: true }
  ]
});
```

You can add your own extensions using the same syntax. The following properties are available for each dependency object:
- **src**: Path to the script to load
- **async**: [optional] Flags if the script should load after reveal.js has started, defaults to false
- **callback**: [optional] Function to execute when the script has loaded
- **condition**: [optional] Function which must return true for the script to be loaded

---

## Licenses

[Jekyll](https://github.com/jekyll/jekyll): [MIT licensed](https://github.com/jekyll/jekyll/blob/master/LICENSE)

[reveal.js](https://github.com/hakimel/reveal.js): [MIT licensed](https://github.com/hakimel/reveal.js/blob/master/LICENSE)  
Copyright (C) 2020 Hakim El Hattab, <https://hakim.se>

[reveal-jekyll](https://github.com/tasmo/reveal-jekyll) contains the third party fonts:

- [Open Sans](https://www.google.com/fonts/specimen/Open+Sans) ([Apache License, version 2.0](https://www.apache.org/licenses/LICENSE-2.0.html))
- [Droid Serif](https://www.google.com/fonts/specimen/Droid+Serif) ([Apache License, version 2.0](https://www.apache.org/licenses/LICENSE-2.0.html))
- [Font Awesome](https://github.com/FortAwesome/Font-Awesome) ([License: SIL OFL 1.1](https://fontawesome.io/license/))
and the color scheme [Solarized Colors](https://github.com/altercation/solarized) ([MIT License](https://github.com/altercation/solarized/blob/master/LICENSE))

[reveal-jekyll](https://gitlab.com/tasmo/reveal-jekyll/): [MIT licensed](https://gitlab.com/tasmo/reveal-jekyll/-/blob/main/LICENSE)  
