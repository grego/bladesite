+++
title = "Getting started"
weight = 0
+++

If you have the Rust toolchain installed, you can install Blades from its repository
``` sh
git clone https://github.com/grego/blades
cd blades
cargo install --path .
```
It is also available on [AUR](https://aur.archlinux.org/packages/blades-bin/).

Then, you can run the executable `blades` with the following subcommands:
<div id="commands">

`init` Initialise the site in the current directory, creating the basic files and folders

`build` Build the site according to config, content, templates and themes in the current directory

`colocate` Move the assets from the "assets" directory and from the theme, if one is used, into the output directory

`all` Build the site and colocate the assets

`lazy` Build the site and (colocate assets only if the theme was switched) [default]

`new` Create a new page

</div>

## Themes
When you specify a theme in the [config](config.html), templates and assets from the theme are used.
Every site that doesn't use a theme can be used as a theme for another site.
To use it, simply clone it into the themes directory.
```sh
cd themes
git clone $site_repository
```

Then, set it as a theme in `Blades.toml`:
```toml
theme = "$site_name"
```

To overwrite the theme, simply use the files in the `templates`, resp. `assets` subdirectories of the
page root directory.

## Assets
All the files from the `assets` directory (and from the theme) are moved into the directory
specified in the [config](config.html), which is emptied before. This is a subdirectory of the
output directory (defaults to `assets`).

Blades takes of the pages it rendered before and if some of them is deleted, the corresponding
files in the output directory will be deleted, too. The other files in the output directory
are left intact. This way, you can place anything in the output directory and (as long as its name
differs from all the page names and it's not in the assets subdirectory), Blades won't touch it.

## Meta
Blades renders [sitemap](https://www.sitemaps.org) (into `sitemap.xml`), [Atom](https://en.wikipedia.org/wiki/Atom_(Web_standard)) (into `atom.xml`)
and [RSS](https://en.wikipedia.org/wiki/RSS) (into `rss.xml`) feeds, unless explicitly disabled in the [config](config.html).

## Contribution
If you found a bug or would like to see some feature in Blades, you are the most welcome to submit an issue
or a pull request! Likewise if you found something in this documentation not clear or imprecise.
"""
