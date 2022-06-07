+++
title = "Making plugins"
weight = 5
+++
Blades has a versatile extension system, where a plugin can be written in any language
that can read from standard input and write to the standard output.
Each plugin is run at the appropriate stage of site rendering.

Check out the already made [plugins](/plugins/index.html).

There are 4 types of plugins that can be used with Blades.
* **input** - they put a JSON-serialised list of [pages](/pages.html) on the standard output, can be used
  to get pages from different sources
* **output** - they receive a JSON-serialised list of [pages](/pages.html) on the standard input and can be
  used to generate further page data, such as processed images
* **transform** - they receive a JSON-serialised list of [pages](/pages.html) on the standard input and output
  another such list on the standard output, can transform anything on the pages
* **content** - they receive a markdown content of one page on standard input and output markdown on the standard output; they are enabled
  on per-page basis

The plugins can be set up in the [config](/config.html).

### Serialised page data
All the data specified on every [page](/pages.html) is available in the serialised list of pages.
It contains only the fields that were explicitly set, so no field can be assumed to be
present or non-present.

For Rust, Blades also provides a
[library](https://docs.rs/blades) for automatic serialisation and deserialisation of pages.
Currently, Cargo doesn't support binary-only dependencies. As such, these dependencies are behind
the `bin` feature gate, which is enabled by default. When using Blades as a library, they are not
necessary, so it is recommended to import blades with `default_features = false`.

```toml
blades = { version = "0.3", default_features = false }
```

### Example
An example plugin can be found in the [Blades repository](https://github.com/grego/blades)
in the `examples` directory.
To try it, clone it and downolad the theme as a submodule
```bash
git clone https://github.com/grego/blades
cd blades
git submodule update --init
```
Then build the plugin:
```bash
cargo build --release transform_plugin
```
Then run Blades in the `examples` directory:
```bash
cd examples
cargo run --release
```

Or check some [real plugins](/plugins/index.html).
