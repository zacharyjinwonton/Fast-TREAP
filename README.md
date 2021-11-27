# Fast-TREAP

This repo presents a new algorithm for insertion in persistent balanced binary search trees (BST) on non-volatile memory (PMEM).

Many conventional implementations for insertion in BSTs, including AVL trees, Red-Black trees, and TREAPs (tree-heaps), rely on tree rotations for maintaining balance to achieve better performance. Such rotations are expensive, especially when considering the PMEM environment. They require a sequence of writes which are very expensive in PMEM. Performing these writes in a manner such that no data are lost after a crash adds further complexity.

Fast-TREAP is a new algorithm for insertion in a TREAP that does not use tree rotations and there- fore does not suffer from these drawbacks. The conventional TREAP insertion algorithm first inserts the new key as a leaf in the TREAP according to the binary search tree property, and then moves it upward in the TREAP with performing rotations to restore the heap property. In contrast, Fast-TREAP inserts the new key immediately in its final location in the TREAP according to the heap property and then rearranges the sub-tree below it to restore the binary search tree property. Fast-TREAP requires fewer writes and makes it relatively easy to perform these writes such that the data structure is recoverable after a crash.

We demonstrate the superiority of Fast-TREAP on PMEM in comparison to AVL tree, Red-Black tree, and a conventional implementation of TREAP, using both random and sequential values for insertion. For instance, for inserting one million random keys in an empty BST, Fast-TREAP achieves an insertion rate of 1,023k per second, 28% better than its nearest competitor. For inserting one million sequential keys, it achieves an insertion rate of 1,644k per second, nearly double that of its closest competitor.
