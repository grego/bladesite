+++
title = "Templates"
weight = 4
+++
Blades uses [mustache](https://mustache.github.io/mustache.5.html) templates with the 
[Ramhorns](https://github.com/maciejhirsz/ramhorns) engine. While their syntax is simple
(and can be learned in a few minutes), they are surprisingly expressive.

Templates are loaded from the `templates` subdirectory, or secondarily from the `themes/$theme/templates`
directory if a theme is specified in the [config](config.html).

Here is the list of variables available to use in templates. Apart from these,
**any** other variable of **any type** specified on the [page](/page.html)
or in the [site config](/config.html) can also be used.

These variables are common for all pages:

<code class="highlighted">

*// The data of the whole site*
**site**: [Site](#site)
*// Main page in the site*
**index**: [Page](#page)
*// A dictionary of all the taxonomies used in the site*
**classification**: Map<string, [Taxonomy](#taxonomy)>

</code>

## Page { #page }
When rendering a page, these variables are available:

<code class="highlighted">

*// Title of the page*
**title**: string
*// Date when the page was created*
**date**: Option<[DateTime](#datetime)>
*// Image representing the page*
**image**: string
*// A brief summary of the page*
**summary**: string
*// The main content of the page*
**content**: string

*// The full link of the page, with the site URL included*
**permalink**: string
*// The path of the page, beginning with `/`, without the last segment*
*// When rendered as section ({{#path}}), it acts as a list of [Ancestors](#ancestors)*
**path**: string
*// The trailing segment of this page's URL*
*// Without the .html extension*
*// For sections, it's the folder name rather than `index`*
**slug**: string
*// A list of alternative paths where this page is rendered to, if any*
**alternative_paths**: List<string>

*// A list of classifications for each of the provided taxonomies*
**taxonomies**: Map<string, List&lt;string&gt;>
*// A list of pictures provided by this page*
**pictures**: List<[Picture](#picture)>

*// Is this page a section?*
**is_section**: bool
*// Is the page hidden from the list of its parent's subpages and subsections?*
**hidden**: bool
*// A priority of this page for SEO, in the range of 0-1*
**priority**: float

*// The page one level up in the hierarchy (for the index page it's itself)*
**parent**: [Page](#page)
*// The previous page on this level, if any*
**previous**: Option<[Page](#page)>
*// The next page in this level, if any*
**next**: Option<[Page](#page)>
*// A list of all the subpages (empty if not section)*
**pages**: List<[Page](#page)>
*// A list of all the subsections (empty if not section)*
**subsections**: List<[Page](#page)>
*// Available when the subpages are paginated*
**pagination**: Option<[Pagination](#pagination)>

*// Marks whether this page is the active one*
*// Can be used to highlight the current page in a list of pages*
**active**: bool

</code>

### Pagination { #pagination }
When the pagination is available, you can use these variables in the pagination section
(`{{#pagination}} ... {{/pagination}}`):

<code class="highlighted">

*// Number of the current page in the paginated pages*
**current**: integer
*// Number of the previous page in the paginated pages*
*// This is also its slug*
**previous**: Option&lt;integer&gt;
*// Number of the next page in the paginated pages*
*// This is also its slug*
**next**: Option&lt;integer&gt;
*// Number of the paginated pages*
**length**: integer

</code>

### Ancestors { #ancestors }
When the page path is used as a section (`{{#path}} ... {{/path}}`), it is interpreted
as a list of ancestors. This makes making breadcrumbs possible.
For the path segments, the following are available:

<code class="highlighted">

*// Name of the current path segment*
**name**: string
*// The full path up to this segment*
**full**: string

</code>

### DateTime { #datetime }
When the date is available, you can use these variables in the datetime section
(`{{#date}} ... {{/date}}`), roughly corresponding to [strftime](https://strftime.org/):

<code class="highlighted">

*// Year*
**y**: integer
*// Month*
**m**: integer
*// Day, 0-padded*
**d**: integer
*// Day, space-padded*
**e**: integer
*// Hour*
**H**: integer
*// Minute*
**M**: integer
*// Second*
**S**: integer
*// First 3 letters of the English month name*
**b**: string
*// First 3 letters of the English weekday name*
**a**: string

</code>

### Picture { #picture }
When pictures are available, you can use these variables in the pictures section
(`{{#pictures}} ... {{/pictures}}` for a list of them):

<code class="highlighted">

*# Id string of the picture, used for the generated URL in the gallery page*
**pid**: string
*# An associated caption of the picture*
**caption**: string
*# An alternative text displayed when the image can't be loaded of for accessibility*
**alt**: string
*# File name of the image*
**file**: string
*# Date and time of when the image was taken*
**taken**: Option<[DateTime](#datetime)>
*// The full link of the picture, with the site URL included*
**permalink**: string

</code>

## Gallery { #gallery }
When a page contains come picture, the gallery is created. The page of each photo in the gallery
gets the following variables:

<code class="highlighted">

*// The current picture*
**current**: [Picture](#picture)
*// The previous picture in the list (the last one for the first one)*
**previous**: [Picture](#picture)
*// The next picture in the list (the first one for the last one)*
**next**: [Picture](#picture)
*// The parent page, from which this gallery is generated*
**parent**: [Page](#page)

</code>

## Taxonomy { #taxonomy }
Each taxonomy that is rendered gets the following variables:

<code class="highlighted">

*// Full name of the taxonomy*
**title**: string
*// A short name of the taxonomy, used in the URL*
**slug**: string
*// A brief description of the taxonomy*
**description**: string
*// A list of keys used in this taxonomy and their corresponding pages*
**keys**: List<[KeyPages](#keypages)>

</code>

### Key pages { #keypages }
When keys in the taxonomy are available, you can use these variables in the keys section
(`{{#keys}} ... {{/keys}}` for a list of them):

<code class="highlighted">

*// Name of this key (also used in the URL of the key page)*
**key**: str
*// All the pages with this key in this taxonomy*
**pages**: List<[Page](#page)>

</code>

## Taxonomy key { #taxonomy-key } 
When rendering a page of a single taxonomy key, these variables are available:

<code class="highlighted">

*// Name of this key (also used in the URL)*
**title**: string
*// The parent taxonomy where this key belongs to*
**taxonomy**: [Taxonomy](#taxonomy)
*// The pages using this key*
**pages**: List<[Page](#page)>
*// Optional pagination, if enabled for this taxonomy*
**pagination**: Option<[Pagination](#pagination)>

</code>

## Site { #site }
The data of the whole site, available for every page in the site section
(`{{#site}} ... {{/site}}`):

<code class="highlighted">

*// The main title of the site*
**title**: string
*// The main URL of the site*
**url**: string
**description**: string
**keywords**: string
*// A representative image of the site*
**image**: string
*// Info about the author of the site*
**author**: [Author](#author)

*// Path of the site where the assets are moved to*
**assets**: string
*// Is sitemap rendered?*
**sitemap**: bool
*// Is atom feed rendered?*
**atom**: bool
*// Is RSS feed rendered?*
**rss**: bool
*// Are taxonomies not explicitly defined in the config, but used in some page rendered?*
**implicit_taxonomies**: bool
*// Are pages without date provided assigned the date of file creation?*
**dates_of_creation**: bool

</code>

### Author { #author }
Info about the site author, available as a subsection of [site](#site)
(`{{#site}}{{#author}} ... {{/author}}{{/site}}`):

<code class="highlighted">

**name**: string
**uri**: string
**email**: string
**avatar**: string

</code>



For an actual example of templates in Blades, you can take a look at the
code of [this site](https://github.com/grego/bladesite), or of various
[themes](/themes/index.html).
