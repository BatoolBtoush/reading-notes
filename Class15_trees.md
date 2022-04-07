# **Implementation: Trees**

## **Common Terminology**

1. Node: A Tree node is a component which may contain its own values, and references to other nodes
2. Root: The root is the node at the beginning of the tree
3. K: A number that specifies the maximum number of children any node may have in a k-ary tree. In a binary tree, k = 2.
4. Left: A reference to one child node, in a binary tree
5. Right: A reference to the other child node, in a binary tree
6. Edge: The edge in a tree is the link between a parent and child node
7. Leaf: A leaf is a node that does not have any children
8. Height: The height of a tree is the number of edges from the root to the furthest leaf

<br>


## **Binary Tree**

![Binary Tree](imgs/BinaryTree.png)

<br>

## **Traversals**

The ability to traverse trees is a fundamental component of them. We may search for a node, print the contents of a tree, and much more by traversing a tree! When it comes to trees, there are two types of traversals:

- **Depth First:**

    When using depth first traversal, we emphasize traveling through the tree's depth (height) first. There are several methods for performing depth first traversal, each of which alters the order in which we search for/print the root. Here are three strategies for traversing depth first:

    Pre-order: root >> left >> right
    In-order: left >> root >> right
    Post-order: left >> right >> root

- **Breadth First:**

    The breadth first traversal iterates through the tree by node-by-node traversing each level of the tree. So, let's look at our starting tree once more:

    Our output using breadth first traversal is now:

    Output: A, B, C, D, E, F

    To explore the width/breadth of the tree, breadth first traversal traditionally employs a queue (rather than the call stack via recursion). Let's have a look at the steps.


<br>

<br>

## **Binary Tree Vs K-ary Trees**

Trees can have any number of children per node, but **Binary Trees** restrict the number of children to two (hence our left and right children).
There is no specific sorting order for a binary tree. Nodes can be added into a binary tree wherever space allows.

**K-ary Trees**:
If Nodes are able have more than 2 child nodes, we call the tree that contains them a K-ary Tree. In this type of tree we use K to refer to the maximum number of children that each Node is able to have.

<br>

## **Adding a node**

Because there are no structural rules for where nodes are “supposed to go” in a binary tree, it really doesn’t matter where a new node gets placed.

One strategy for adding a new node to a binary tree is to fill all “child” spots from the top down. To do so, we would leverage the use of breadth first traversal. During the traversal, we find the first node that does not have all its children filled, and insert the new node as a child. We fill the child slots from left to right.

In the event you would like to have a node placed in a specific location, you need to reference both the new node to create, and the parent node which the child is attached to.


<br>

<br>

## **Big O**

Inserting a new node has a Big O time complexity of O. (n). It will also be O to look for a certain node (n). Because a Binary Tree lacks organizational structure, the worst-case scenario for most operations is traversing the entire tree. If we suppose that a tree has n nodes, we will have to look at n things in the worst scenario, resulting in O(n) complexity.

The Big O space complexity for a node insertion using breadth first insertion will be O(w), where w is the largest width of the tree. For example, in the above tree, w is 4.

Every non-leaf node in a "perfect" binary tree has precisely two children. A perfect binary tree's maximum width is 2(h-1), where h is the tree's height. Log n, where n is the number of nodes, can be used to calculate height.