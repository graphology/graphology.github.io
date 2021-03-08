## Example: Subgraphs

```js
/**
 * Function taking a directed graph & returning the subgraph having the given
 * set of nodes.
 */
export function subgraph(graph, nodes) {
  const sub = graph.emptyCopy(),
        nodesSet = new Set(nodes),
        edges = [];

  // Importing the nodes:
  sub.importNodes(graph.exportNodes(nodes));

  // Keeping the relevant edges:
  nodes.forEach(node => {

    // An edge is deemed relevant if both its end are attached to
    // one of the subgraph's nodes.
    const relevantEdges = graph.outEdges(node).filter(edge => {
      const target = graph.opposite(node, edge);

      return nodeSet.has(target);
    });

    edges = edges.concat(relevantEdges);
  });

  graph.importEdges(graph.exportEdges(edges));

  return sub;
}
```
