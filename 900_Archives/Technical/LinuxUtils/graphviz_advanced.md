---
tags: 
  - Linux
  - Utils
  - graphviz
  - graphing
  - visualization
alias: []
created: 2025-08-01
updated:
source:
---

# `Graphviz` Advanced Usage

This note covers more advanced Graphviz features. For a basic introduction, see [[graphviz]].

## Node and Edge Attributes

You can customize the appearance of nodes and edges using attributes.

- **`label`**: Sets the display text for a node or edge.
- **`shape`**: Changes the shape of a node (e.g., `box`, `ellipse`, `circle`).
- **`color`**: Sets the color of nodes, edges, or text.
- **`style`**: Changes the style (e.g., `filled`, `dashed`, `bold`).

### Advanced Example

Create a file named `custom.dot`:
```dot
digraph custom_graph {
  // Global node and edge attributes
  node [shape=box, style=filled, color=lightblue];
  edge [color=gray, style=dashed];

  // Node definitions with custom attributes
  A [label="Start", shape=ellipse, color=lightgreen];
  B [label="Process"];
  C [label="End", shape=ellipse, color=lightcoral];

  // Edge definitions with custom labels
  A -> B [label="Step 1"];
  B -> C [label="Step 2"];
  A -> C [style=dotted, label="Optional"];
}
```

Generate the image:
```bash
dot -Tpng custom.dot -o custom.png
```

## Different Layout Engines

Graphviz includes several layout engines for different types of graphs:

- **`dot`**: The default, for hierarchical or layered drawings.
- **`neato`**: For "spring model" layouts.
- **`fdp`**: For force-directed graphs.
- **`circo`**: For circular layouts.
- **`twopi`**: For radial layouts.

To use a different engine, simply replace the `dot` command:

```bash
# Use the neato engine for a spring model layout
neato -Tpng custom.dot -o custom_neato.png

# Use the circo engine for a circular layout
circo -Tpng custom.dot -o custom_circo.png
```

## Subgraphs and Clusters

You can group nodes together using subgraphs. If the subgraph name starts with `cluster`, Graphviz will draw a box around it.

Create a file named `cluster.dot`:
```dot
digraph cluster_example {
  subgraph cluster_0 {
    label = "Group A";
    color=blue;
    node [style=filled, color=white];
    a0 -> a1 -> a2 -> a3;
  }

  subgraph cluster_1 {
    label = "Group B";
    color=red;
    node [style=filled];
    b0 -> b1 -> b2 -> b3;
  }

  start -> a0;
  start -> b0;
  a3 -> end;
  b3 -> end;
}
```

Generate the image:
```bash
dot -Tpng cluster.dot -o cluster.png
```
