+++
title = "KaTeX - JavaScript"
weight = 1
summary = "Render math formulas using KaTeX - written in JavaScript"

repository = "https://github.com/grego/blades-katex"
+++
Blades natively supports rendering LaTeX formulas into [MathML](https://developer.mozilla.org/docs/Web/MathML).
Sadly, Chromium-based browsers don't support it.
This plugin renders the formulas into HTML using [KaTeX](https://katex.org).
Formulas delimited by `$` are rendered in inline mode and by `$$` in display mode.

Be aware there is a [Rust version](/plugins/katex-rs.html) that does the same,
but faster.

This plugin can be installed as
```bash
yarn global add https://github.com/grego/blades-katex
```

Then, it can be used in Blades as
```toml
[plugins]
transform = "blades-katex"
```

This plugin is basically a stripped-down version of
[auto-render extension](https://katex.org/docs/autorender.html) for KaTeX.

