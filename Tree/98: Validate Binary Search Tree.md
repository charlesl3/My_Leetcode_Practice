# Problem 98: Validate Binary Search Tree

**Difficulty:** Medium  
**Topics:** Trees, Binary Search Tree, Depth-First Search (DFS)  

---

## Problem Description

Given the root of a binary tree, determine if it is a valid binary search tree (BST).

A valid BST is defined as follows:

- The **left subtree** of a node contains only nodes with keys **less than the node's key**.
- The **right subtree** of a node contains only nodes with keys **greater than the node's key**.
- Both the left and right subtrees must also be binary search trees.

---

## Examples

### Example 1

**Input:**  
`root = [2, 1, 3]`

**Output:**  
`true`

## Code
```python
class Solution(object):
    def isValidBST(self, root):
        """
        :type root: Optional[TreeNode]
        :rtype: bool
        """
        def validate(root,minimum,maximum):
            if not root:
                return True
            if not minimum < root.val < maximum:
                return False
            return validate(root.left, minimum, root.val) and validate(root.right, root.val, maximum)
        return validate(root, float('-inf'), float('inf'))
            
        

