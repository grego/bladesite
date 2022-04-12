+++
title = "KaTeX - Rust"
weight = 0
summary = "Render math formulas using KaTeX - written in Rust"

repository = "https://github.com/grego/blades-katex-rs"
+++
Blades natively supports rendering LaTeX formulas into [MathML](https://developer.mozilla.org/docs/Web/MathML).
Sadly, Chromium-based browsers don't support it.
This plugin renders the formulas into HTML using [KaTeX](https://katex.org),
run with the QuickJS engine.
Formulas delimited by `$` are rendered in inline mode and by `$$` in display mode.

This plugin can be installed as
```bash
git clone https://github.com/grego/blades-katex-rs
cd blades-katex-rs
cargo install --path .
```

Then, it can be used in Blades as
```toml
[plugins]
transform = ["blades-katex"]
```
