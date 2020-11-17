# Same/Symmetric/Invert

#### [Same Tree](https://leetcode.com/problems/same-tree/)

```python
class Solution:
    def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
        if not p and not q:
            return True
        if p and q and p.val==q.val:
            return self.isSameTree(p.left,q.left) and self.isSameTree(p.right,q.right)
        return False
```

#### [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/description/)

```python
class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        return self.helper(root,root)
    def helper(self,p,q):
        if not q and not p:
            return True
        if p and q and p.val==q.val:
            return self.helper(p.left,q.right) and self.helper(p.right,q.left)
        return False
```

#### [Invert a Binary Tree](https://leetcode.com/problems/invert-binary-tree/description/)

```python
class Solution:
    def invertTree(self, root: TreeNode) -> TreeNode:
        if not root:
            return
        l,r = self.invertTree(root.left), self.invertTree(root.right)
        root.left,root.right = r,l
        return root
```



