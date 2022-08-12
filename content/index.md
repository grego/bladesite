+++
title = "Index"
sort_by_weight = true
+++
<code class="highlighted">

**bla**zing fast
 **de**ad simple
  **s**tatic site generator

</code>


Blades is made to do one job - generate HTML files from the provided
content using the provided templates.  
Thanks to [zero-copy](https://serde.rs/lifetimes.html#borrowing-data-in-a-derived-impl) deserialisation
and the [Ramhorns](https://github.com/maciejhirsz/ramhorns) templating engine,
it renders the whole site in milliseconds, possibly more than
[20 times](https://github.com/grego/ssg-bench) faster than other generators like Hugo.

It's made for easy setup and use. A static site generator should be a no brainer.
It uses [mustache](https://mustache.github.io/mustache.5.html) templates with extremely minimal
and obvious syntax (like 7 rules!), providing the necessary building blocks
to let you focus on your content.

## Features
* Powerful plugin system
* Themes
* Image gallery generation
* [CommonMark](https://commonmark.org) markdown with tables and footnotes for content
* Automatic syntax highlighting using [cmark-syntax](https://github.com/grego/cmark-syntax)
  (with a possibility of turning LaTeX formulas into [MathML](https://developer.mozilla.org/docs/Web/MathML))
* Customizable taxonomies (like categories or tags)
* Pagination
* Breadcrumbs
* Asset colocation
* Table of contents with access to all of the site data
* Automatic sitemap, Atom and RSS feed generation

## Why not _`blades`_?
Unlike other monolithic generators, Blades is modest in its scope. All it does is generating your site.
It doesn't do any fancy stuff like transpiling Haskell to minified Javascript, or ever
watching the site for changes. For that, you can use a dedicated tool like
[caretaker](https://github.com/grego/caretaker).

Nevertheless, if you have a feature request or ran into some issue using Blades, please submit an
[issue](https://github.com/grego/blades). Any contribution
is welcome! `:)`

## Why _`blades`_?
They shave the [mustache](https://mustache.github.io/mustache.5.html) off.
