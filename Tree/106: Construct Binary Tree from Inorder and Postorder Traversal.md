# Problem 106: Construct Binary Tree from Inorder and Postorder Traversal

**Difficulty:** Medium  
**Topics:** Binary Trees, Tree Traversals, Divide and Conquer  

---

## Problem Description

Given two integer arrays `inorder` and `postorder` where:

- `inorder` is the **inorder traversal** of a binary tree.
- `postorder` is the **postorder traversal** of the same binary tree.

Construct and return the binary tree.

---

## Examples

### Example 1

**Input:**  
`inorder = [9, 3, 15, 20, 7]`  
`postorder = [9, 15, 7, 20, 3]`

**Output:**  
`[3, 9, 20, null, null, 15, 7]`

## Codes
```python
class Solution(object):
    def buildTree(self, inorder, postorder):
        """
        :type inorder: List[int]
        :type postorder: List[int]
        :rtype: Optional[TreeNode]
        """
        if not postorder or not inorder:
            return None

        root_val = postorder[-1]
        root = TreeNode(root_val)
        root_index = inorder.index(root_val)

        root.left = self.buildTree(inorder[:root_index],postorder[:root_index])
        root.right = self.buildTree(inorder[root_index + 1:],postorder[root_index:-1])

        return root

