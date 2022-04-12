+++
title = "Kroki"
weight = 2
summary = "Render code blocks using Kroki as the default service. The algorithm can be specified in the first line."

repository = "https://github.com/Heiss/blades-kroki"
+++
A transform plugin that renders code blocks using [Kroki](https://kroki.io/) as the default service.
Code blocks are delimited by `` ``` `` and the algorithm can be specified in the first line.

You can use any other code blocks as before, too. This plugin replaces only code blocks, which Kroki responses with a successful conversion of a diagram. Otherwise it will print out the code block untouched, so another plugin can handle it.

## Beware:

This implementation currently not support parallel requests to kroki server, so a heavy load of diagrams can lags performance. But we are using a cache, so all requests done only once as long as you do not change the diagramtype or diagram content.

## Tutorial

General use:

````
```[Diagramtype]
<your diagram code>
```
````

Example:
````
```Graphviz
digraph D {
  subgraph cluster_p {
    label = "Kroki";
    subgraph cluster_c1 {
      label = "Server";
      Filebeat;
      subgraph cluster_gc_1 {
        label = "Docker/Server";
        Java;
      }
      subgraph cluster_gc_2 {
        label = "Docker/Mermaid";
        "Node.js";
        "Puppeteer";
        "Chrome";
      }
    }
    subgraph cluster_c2 {
      label = "CLI";
      Golang;
    }
  }
}
```
````

This plugin can be installed as
```bash
git clone https://github.com/Heiss/blades-kroki
cd blades-kroki
cargo install --path .
```

Then, it can be used in Blades as
```toml
[plugins]
transform = ["blades-kroki"]
```
