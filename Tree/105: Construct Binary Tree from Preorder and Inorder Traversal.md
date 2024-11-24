# Problem 105: Construct Binary Tree from Preorder and Inorder Traversal

**Difficulty:** Medium  
**Topics:** Binary Trees, Tree Traversals, Divide and Conquer  

---

## Problem Description

Given two integer arrays `preorder` and `inorder` where:

- `preorder` is the **preorder traversal** of a binary tree.
- `inorder` is the **inorder traversal** of the same binary tree.

Construct and return the binary tree.

---

## Examples

### Example 1

**Input:**  
`preorder = [3, 9, 20, 15, 7]`  
`inorder = [9, 3, 15, 20, 7]`

**Output:**  
`[3, 9, 20, null, null, 15, 7]`

## Code
```python
class Solution(object):
    def buildTree(self, preorder, inorder):
        """
        :type preorder: List[int]
        :type inorder: List[int]
        :rtype: Optional[TreeNode]
        """
        if not preorder or not inorder:
            return None
        root_val = preorder[0]
        root = TreeNode(root_val)
        root_index = inorder.index(root_val)

        root.left = self.buildTree(preorder[1:1 + root_index], inorder[:root_index])
        root.right = self.buildTree(preorder[1 + root_index:], inorder[root_index + 1:])

        return root

