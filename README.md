# Detect and remove invalid edges in an invalid Tree

## Question

You are given a tree of N nodes. It is mostly a valid tree, except for one
additional edge which violates the tree property. Write a function to find and
remove the edge.

# Solution
```python
edges = {
0: [1,2],
1: [1,3],
2: [3,4],
3: [2,3]
}

def identifyEdge(edges):
    # go through edges
    # nodes dict key: nodename, value: count
    nodes = {} # count nodes edges
    for edge in edges.keys(): # n1
        values = edges[edge]
        for node in values: # [1,2] # n2
            try:
                count = nodes[node]
                if count + 1 > 1:
#                     print(edge)
                    return edge
                nodes[node] = count + 1
            except:
                nodes[node] = 0
#         print(nodes)
    return -1

def removeBadEdge(edges):
    edge = identifyEdge(edges)
    if edge != -1:
        print("Edge",edge,"is invalid and is removed.")
        del edges[edge]
    return edges

def printEdges(edges):
    for edge in edges.keys(): # n1
        second_node = False
        values = edges[edge]
        print(edge, values)

printEdges(edges)
print()
edges = removeBadEdge(edges)
print()
printEdges(edges)
```

# Output

0 [1, 2]
1 [1, 3]
2 [3, 4]
3 [2, 3]

Edge 3 is invalid and is removed.

0 [1, 2]
1 [1, 3]
2 [3, 4]
