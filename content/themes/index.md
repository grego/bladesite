+++
title = "Themes"
template = "themes.html"
page_template = "theme.html"
sort_by_weight = true
weight = 0
+++
Any site that doesn't use a theme can be used as a theme for another site.

To use it, simply clone it into the themes directory.
```sh
cd themes
git clone $site_repository
```

Then, set it as a theme in `Blades.toml`:
```toml
theme = "$site_name"
```

To contribute your own theme, submit a PR to the [themes repository](https://github.com/grego/blades-themes).
