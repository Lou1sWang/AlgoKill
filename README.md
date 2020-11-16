---
description: Popular questions when asking about tree-based algorithms
---

# Tree

* Traversal
* Hight, Width, etc..
* \*\*\*\*

## 

### [Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/description/)

```python
# recursion
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        self.dfs(root,res)
        return res
    def dfs(self,root,res):
        if root:
            self.dfs(root.left,res)
            res.append(root.val)
            self.dfs(root.right,res)

# iteration
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        stack = []
        res = []
        node = root
        while stack or node:
            while node:
                stack.append(node)
                node = node.left
                
            node = stack.pop()
            res.append(node.val)
            node = node.right
        return res
```









### Preorder Traversal

### Postorder Traversal

### Layer Traversal

## 

