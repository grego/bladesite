+++
title = "Pages"
weight = 3
+++
Blades loads all [Markdown](https://commonmark.org)
files (`.md` extension) with an optional [TOML](https://toml.io) header (delimited by `+++`) 
and all TOML files (`.toml` extension) from the directory
specified in the [config](config.html) (defaults to `content`).

In these files, the page content
and metadata are provided. They are then rendered using the provided [templates](templates.html).

When the file is called `index.md` or `index.toml`, the corresponding page is called **section**. The rendered page (`index.html`) is displayed
when the user browses to the parent URL. They can use some additional data in templates,
such as their subpages and subsections. Other files are treated as standard pages.

In pages (either in the header or in the TOML files), these variables can be specified.
All of them are optional, default values are shown. <br>
**Any** other variable of **any type** can be set there and used in the templates, too.

```toml
# Title of the page
title = ""
# Date when the page was created
date = nan
# date = 2020-09-08

# An image representing the page
image = ""
# A brief summary of the page content
summary = ""

# The main content of the page
# CommonMark markdown can be used here
# In Markdown files, it is replaced with the actual content of the file, if present.
content = """
"""

# A weight of the page, used if a collection this page is in is sorted by weight
weight = 0
# A priority of this page for SEO, in the range of 0-1
priority = 0.5
# Hide the page from the list of its parent's subpages or subsections
hidden = false
#A list of alternative paths to render this page in, relative to the output directory
alternative_paths = []

#A list of content plugins to transform the content of this page with
plugins = []

# A template to render this page with.
# If none is specified, the one specified in the parent section is used
template = ""
# A template to render the gallery pictures with
gallery_template = "gallery.html"

# A list of pictures associated with this page
# Each will be rendered into a separate gallery page
[[pictures]]
# Id string of the picture, used for the generated URL in the gallery page
# MANDATORY for every picture used!
pid = ""
# An associated caption of the picture
# [CommonMark](https://commonmark.org/) markdown can be used here
caption = ""
# An alternative text displayed when the image can't be loaded of for accessibility
alt = ""
# File name of the image
file = ""
# Date and time of when the image was taken
taken = None
# Repeat for every picture

# A map of lists to classify this page with
[taxonomies]
# For example:
# tags = ["blades", "documentation"]
```

## Sections { #sections }
For pages that are sections, you can additionally specify these variables:

```toml
# A number of pages to paginate by, if this number is exceeded
# If provided, must be a positive integer
paginate_by = inf
# A template to render every subpage with (unless it specifies another template)
page_template = "page.html"
# A template to render every subsection with (unless it specifies another template)
section_template = "section.html"
# Sort subpages and subsetions by their provided weight, low to high
# By default, they are sorted by their date, newer to older
sort_by_weight = false
```

## Not sections { #not-sections }
For pages that are not sections, you can additionally specify these variables
(defaults are suggested):

```toml
# The path in the output directory this page is rendered into*
path = "{{ parent directory of the page }}"
# The file name this page is rendered into, without the .html extension*
slug = "{{ file name without the extension }}"
```

For an actual example of pages in Blades, you can take a look at the
code of [this site](https://github.com/grego/blades).
