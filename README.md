# sql-binary-tree
SQL solution for classifying nodes in a binary tree into Root, Inner, and Leaf

## Overview
This project solves a problem where nodes in a binary search tree (BST) need to be classified into one of three categories: `Root`, `Inner`, or `Leaf`. The problem involves using SQL queries to identify the correct classification based on the parent-child relationships of the nodes.

## Problem Statement
Given a table `BST` with columns:
- `N`: Node value
- `P`: Parent node value (NULL if the node is the root)

The objective is to classify each node as:
- `Root`: If the node has no parent.
- `Inner`: If the node is a parent (appears in the `P` column).
- `Leaf`: If the node has no children.


## SQL Solution
```sql
SELECT N,
    CASE
        WHEN P IS NULL THEN 'Root'
        WHEN N IN (SELECT P FROM BST WHERE P IS NOT NULL) THEN 'Inner'
        ELSE 'Leaf'
    END AS NodeType
FROM BST
ORDER BY N;
```

## Explanation
-The CASE statement checks the parent-child relationship of each node.

-The nodes are classified as Root, Inner, or Leaf based on their relationships.

-The query ensures that nodes are classified correctly and orders them by their value.





